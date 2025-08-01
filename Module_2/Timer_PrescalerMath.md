#### Timer Frequency and Period Formula

The timer event frequency is given by:

`Timer_Event_Frequency = TIM_CLK / ((PSC + 1) * (ARR + 1))`

Where:
- **TIM_CLK** = Timer clock frequency (Hz)
- **PSC** = Prescaler value
- **ARR** = Auto-reload register (counter period) value

To achieve a desired timer period \(T\) (in seconds):

`T = ((PSC + 1) × (ARR + 1)) / TIM_CLK`

Rearranged for calculation:

In the example I've written, I've chosen PSC -> 7199 & ARR -> 999
TIM_CLK is 72MHz (from BluePill's clock configuration)
Plugging these numbers into the expression, you'll get a timer event frequency of 10 Hz.

<a href="P5_Embedded%20Engineering%20In%20Practice.md">Back to P5</a>

---
