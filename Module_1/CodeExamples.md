# CODE EXAMPLES

> **Note:** Register names are from the STM32F1 reference manual, so it's crucial to have the [STM32F103x8 Reference Manual](https://www.st.com/resource/en/reference_manual/cd00171190.pdf) open while reading.

---

## 1. Goal: Use TIM2 to generate a periodic interrupt and toggle an LED on GPIOC Pin 13

```
#include "stm32f10x.h"

void timer2_init() {  
	// Enable clock for GPIOC and TIM2  
	RCC->APB2ENR |= RCC_APB2ENR_IOPCEN;  
	RCC->APB1ENR |= RCC_APB1ENR_TIM2EN;

	// Set PC13 as output
	GPIOC->CRH &= ~(0xF << 20);
	GPIOC->CRH |= (0x1 << 20); // Output, push-pull, 10 MHz

	// Timer configuration
	TIM2->PSC = 7200 - 1;     // Prescaler
	TIM2->ARR = 10000 - 1;    // Auto-reload
	TIM2->DIER |= TIM_DIER_UIE; // Enable update interrupt
	TIM2->CR1 |= TIM_CR1_CEN;   // Enable counter

	// Enable TIM2 interrupt
	NVIC_EnableIRQ(TIM2_IRQn);

}

void TIM2_IRQHandler() {  
	if (TIM2->SR & TIM_SR_UIF) {  
		TIM2->SR &= ~TIM_SR_UIF;  
		GPIOC->ODR ^= (1 << 13); // Toggle PC13  
	}  
}

int main(void) {  
	timer2_init();  
	while (1) {  
		// Do nothing, wait for interrupt  
	}  
}
```


---

## 2. Goal: Sample analog voltage from pin PA0, send its digital value over USART1 TX (PA9). (ADC1 + USART1 + GPIO + RCC)

```
#include "stm32f10x.h"

void uart_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_IOPAEN | RCC_APB2ENR_USART1EN;

	// Configure PA9 as alternate function push-pull (TX)
	GPIOA->CRH &= ~(0xF << 4);
	GPIOA->CRH |= (0xB << 4); // AF output, 50 MHz
	
	USART1->BRR = 0x1D4C; // 72 MHz / 9600 baud
	USART1->CR1 |= USART_CR1_TE | USART_CR1_UE;

}

void adc_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_ADC1EN;  
	ADC1->SMPR2 |= (7 << ADC_SMPR2_SMP0_Pos); // Max sample time  
	ADC1->CR2 |= ADC_CR2_ADON;  
}

uint16_t read_adc() {  
	ADC1->SQR3 = 0; // Channel 0 (PA0)  
	ADC1->CR2 |= ADC_CR2_ADON;  
	while (!(ADC1->SR & ADC_SR_EOC));  
		return ADC1->DR;  
}

void uart_send_char(char c) {  
	while (!(USART1->SR & USART_SR_TXE));  
		USART1->DR = c;  
}

void uart_send_number(uint16_t num) {  
	char buffer;  
	int i = 0;  
	do {  
		buffer[i++] = '0' + (num % 10);  
		num /= 10;  
	} while (num > 0);  
	while (i--) uart_send_char(buffer[i]);  
		uart_send_char('\n');  
}

int main() {  
	uart_init();  
	adc_init();  
	while (1) {  
		uint16_t val = read_adc();  
		uart_send_number(val);  
		for (volatile int i = 0; i < 100000; ++i);  
	}  
}
```


---

## 3. SPI-Based Sensor Interface (SPI1 + GPIO + RCC) - Read dummy data from an SPI slave using SPI1

```
#include "stm32f10x.h"

void spi1_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_IOPAEN | RCC_APB2ENR_SPI1EN;

	// Configure PA5(SCK), PA7(MOSI), PA6(MISO) as AF
	GPIOA->CRL = (GPIOA->CRL & ~(0xFFF << 24)) |
             (0xB << 20) | (0xB << 28) | (0x4 << 24); // AF modes

	SPI1->CR1 = SPI_CR1_MSTR | SPI_CR1_SSM | SPI_CR1_SSI | SPI_CR1_SPE;

}

uint8_t spi1_transfer(uint8_t data) {  
	while (!(SPI1->SR & SPI_SR_TXE));  
	SPI1->DR = data;  
	while (!(SPI1->SR & SPI_SR_RXNE));  
	return SPI1->DR;  
}

int main() {  
	spi1_init();  
	while (1) {  
		uint8_t val = spi1_transfer(0xFF); // Dummy byte  
		(void)val; // Placeholder for use  
	}  
}
```


---

## 4. External Interrupt to Trigger ADC Read (NVIC + EXTI + ADC)  
When a button is pressed (on PA1), an interrupt triggers an ADC read.

```
#include "stm32f10x.h"

volatile uint16_t adc_val = 0;

void exti_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_IOPAEN | RCC_APB2ENR_AFIOEN;

	// PA1 as input
	GPIOA->CRL &= ~(0xF << 4);

	AFIO->EXTICR |= AFIO_EXTICR1_EXTI1_PA;
	EXTI->IMR |= EXTI_IMR_MR1;
	EXTI->FTSR |= EXTI_FTSR_TR1;

	NVIC_EnableIRQ(EXTI1_IRQn);

}

void adc_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_ADC1EN;  
	ADC1->CR2 |= ADC_CR2_ADON;  
}

uint16_t read_adc() {  
	ADC1->SQR3 = 0;  
	ADC1->CR2 |= ADC_CR2_ADON;  
	while (!(ADC1->SR & ADC_SR_EOC));  
	return ADC1->DR;  
}

void EXTI1_IRQHandler() {  
	if (EXTI->PR & EXTI_PR_PR1) {  
		adc_val = read_adc();  
		EXTI->PR |= EXTI_PR_PR1;  
	}  
}

int main() {  
	exti_init();  
	adc_init();  
	while (1) {  
		// Main loop can use adc_val  
	}  
}
```


---

## 5. PWM Signal to Control a Motor (TIM3 + GPIO + RCC)  
Output PWM on PB0 to control motor speed.

```
#include "stm32f10x.h"

void pwm_init() {  
	RCC->APB2ENR |= RCC_APB2ENR_IOPBEN;  
	RCC->APB1ENR |= RCC_APB1ENR_TIM3EN;

	// PB0 as AF Push-pull
	GPIOB->CRL &= ~(0xF << 0);
	GPIOB->CRL |= (0xB << 0);

	// TIM3 CH3 on PB0
	TIM3->PSC = 72 - 1;
	TIM3->ARR = 1000 - 1;
	TIM3->CCR3 = 500; // 50% duty
	TIM3->CCMR2 |= (6 << 4); // PWM mode 1
	TIM3->CCER |= TIM_CCER_CC3E;
	TIM3->CR1 |= TIM_CR1_CEN;

}

int main() {  
	pwm_init();  
	while (1) {  
		// Could dynamically adjust duty cycle here  
	}  
}
```


Back to <a href="P5_ToolchainOverview.md">Module 1 - Part 5</a>

---