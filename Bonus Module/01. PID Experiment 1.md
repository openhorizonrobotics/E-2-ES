If you've ever taken a control systems course, chances are you've spent hours solving differential equations on paper -- only to walk out of class wondering, "Cool.. but how does this actually work on a real system?"

Take it from me. When we were learning about control systems in our second year of undergrad, we were presented with a bunch of detail about system dynamics, state spaces, time and frequency domain analyses -- and whatnot.
Trouble was, we were being taught control systems during mid-2021. Where I lived, the Corona was rampaging through our community. With all the doom and gloom surrounding us, it is perhaps not surprising that the finer intricacies of PID would take a backseat in one's mind. I never got around to implementing it in my undergrad years. Later on, I learned how to build aerial vehicles e.g quad-copters. Even then, I only ever fidgeted with sliders to get the drone to respond well.    

Never say never though. I'm back in 2025, and I want to put this write-up out there as a means to both fulfil a pending wish and educate readers who may be in a similar boat. 

Here's how we'll go through this: I'll briefly cover both the math and the intuition behind PID. 

## A PID Refresher

A PID controller contains 3 elements:
- P (Proportion):  React to the present error.
- I (Integral): Accumulate past errors to eliminate steady-state offsets.
- D (Derivative): Predict future trends by reacting to the rate of change.

Mathematically:

$$ 
u(t) = K_p e(t) + K_i \int_0^t e(\tau)\, d\tau + K_d \frac{de(t)}{dt}
$$

Where $u(t)$ represents the controller output, $e(t)$ represents the error/difference between the setpoint and the present output, and $K_p,K_i,K_d$ represent proportional, integral, derivative gains respectively.

## Simulate In Python

Consider a system involving a DC motor: We want the motor to spin steadily at **200 RPM**. In reality, motors don’t just jump to the desired speed — they ramp up, overshoot, and settle depending on the control strategy. Let's simulate one in python.

I tested this sketch in Google Colab, and you can follow along using the same.

```
import matplotlib.pyplot as plt 
import numpy as np

setpoint = 200   # Desired motor speed (RPM)
Kp = 0.5         # Proportional gain
Ki = 0.002       # Integral gain
Kd = 0.01        # Derivative gain
dt = 0.1         # Simulation time step (s)
sim_time = 150   # Total simulation time (s)

integral = 0
previous_error = 0
motor_speed = 0  # Initial motor speed 

time_data = [] #Store Data For Plotting
speed_data = []

for t in np.arange(0, sim_time, dt):

	# Calculate error between setpoint and current motor speed
	error = setpoint - motor_speed
	
	# Proportional term
	P_out = Kp * error
	
	# Integral term (accumulation of past errors)
	integral += error * dt
	I_out = Ki * integral
	
	# Derivative term (rate of change of error)
	derivative = (error - previous_error) / dt
	D_out = Kd * derivative
	
	# Calculate the total control output
	control_output = P_out + I_out + D_out
	
	# Simulate the motor speed response (simplified linear response)
	motor_speed += control_output * dt
	
	# Update the previous error for the next iteration
	previous_error = error
	
	# Save data for plotting
	time_data.append(t)
	speed_data.append(motor_speed)


# Plot the motor speed over time
plt.plot(time_data, speed_data)
plt.title('DC Motor Speed with PID Control')
plt.xlabel('Time (s)')
plt.ylabel('Speed (RPM)')
plt.grid(True)
plt.show()

```

## Results 

With the following parameters:
setpoint = 200   
$K_p$ = 0.5        
$K_i$ = 0.002     
$K_d$ = 0.01       
$dt$ = 0.1        
sim_time = 150  

![Image](Assets/1.png)


With the following parameters:
setpoint = 200   
$K_p$ = 0.1        
$K_i$ = 0.002     
$K_d$ = 0.01       
$dt$ = 0.1        
sim_time = 150  

- Slower system response with decreased aggressiveness in correcting errors.

![Image](Assets/2.png)

With the following parameters:
setpoint = 200   
$K_p$ = 0.1        
$K_i$ = 0     
$K_d$ = 0.01       
$dt$ = 0.1        
sim_time = 150  

- Since this is a simple system with no external dynamics, dropping $K_i$ to 0 does not introduce a steady state error. It merely lengthens the time taken to reach steady state. 


![Image](Assets/3.png)

With the following parameters:
setpoint = 200   
$K_p$ = 0.1        
$K_i$ = 0.5     
$K_d$ = 0.01       
$dt$ = 0.1        
sim_time = 150  

- If your $K_p$ is quite low, turning up $K_i$ will induce wild oscillations like below. Turning up $K_p$ to 0.9 will alleviate the oscillations, but may overtax the physical system.   


![Image](Assets/4.png)

With $K_p$ turned up to 0.9:

![Image](Assets/5.png)

$K_d$ is useful for dampening oscillations. When you can't turn up $K_p$ because the system feels too twitchy, turn up $K_d$ instead. But don't overdo it! It will amplify high frequency noise in the error signal, causing the controller to oscillate wildly. 

With the following parameters:
setpoint = 200   
$K_p$ = 0.1        
$K_i$ = 0.5     
$K_d$ = 0.99      
$dt$ = 0.1        
sim_time = 150 

![Image](Assets/6.png)


## Takeaways

- Even this basic motor model can be extended to include inertia, friction, or saturation effects to make it more realistic.
- In the next PID experiment, we'll see how to write a PID class and implement it for temperature control when the system's own dynamics threaten to destabilise your setpoint.

---