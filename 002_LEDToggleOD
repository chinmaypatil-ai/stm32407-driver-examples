/*
 * 002ledtoogleOD.c
 * Open drain 
 *  Created on: Sep 20, 2025
 *      Author: Chinmay
 */


#include "stm32f407xx.h"

void delay(void)
{
	for(uint32_t i = 0; i < 500000 ; i++);
}

int main(void)
{
	GPIO_Handle_t GpioLed;

	GpioLed.pGPIOx = GPIOD;
	GpioLed.GPIO_PinConfig.GPIO_PinNumber = GPIO_PIN_NO_12;
	GpioLed.GPIO_PinConfig.GPIO_PinMode = GPIO_MODE_OUT;
	GpioLed.GPIO_PinConfig.GPIO_PinSpeed = GPIO_SPEED_FAST;
	//Where we have selected open drain configuration
	GpioLed.GPIO_PinConfig.GPIO_PinOPType = GPIO_OP_TYPE_OD;
	//When we use open drain we use pull resistor so we have enable internal pullup resistor
	GpioLed.GPIO_PinConfig.GPIO_PinPuPdControl = GPIO_PIN_PU; //change this to NOPUPD when we use external pull up resistor
    //But the led is not blinking on full intensity because of high value of pull resistor 40kohm
	//So always we use external pullup resistor of value around 470ohm whenever we use open drain configuration

	GPIO_PeriClockControl(GPIOD, ENABLE);
	GPIO_Init(&GpioLed);


	while(1)
	{
		GPIO_ToggleOutputPin(GPIOD, GPIO_PIN_NO_12);
		delay();
	}
  return 0;
}
