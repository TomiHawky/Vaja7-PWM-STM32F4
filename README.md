# Vaja7-PWM-STM32F4
 Zaženite STM32CubeIDE in ustvarite nov STM32 projekt (pod zavihkom information Center). V zavihku Board selector s pomočjo filtrov Vendor, Type in MCU/MPU Series izberite ustrezno razvojno ploščo (v našem primeru STM32F401C-Discovery), kliknite Next, projekt poimenujte vaja7_PWM in kliknite Finish (na možnosti opcije za prenastavitev periferije izberite Yes, izbrana naj bo tudi opcija perspektive za STM32CubeMX).
V levem Pinout oknu razširite nabor možnosti za Timers ter za časovnik TIM1. Clock Source nastavite kot Internal Clock. Prvi kanal aktivirajte kot PWM Generation CH1. Kateri pin ste omogočili? ___PE9___. Kaj se izpiše poleg pina? ___TIM1_CH1___.
 V Clock Configuration spremenimo takt časovnika APB1 Timer Clocks (MHz) na 16 MHz.
d) V Oknu Configuration kliknemo za TIM1 Vrednost Prescaler v zavihku Counter Settinngs določite tako, da bo časovnik delal s frekvenco 1 MHz. Koliko je vrednost Perscaler (namig; delitelj) ? ___1__.
e) Parameter Counter Period nastavimo na 100 in s tem še dodatno znižamo takt časovnika. Koliko znaša sedaj? _____10_____kHz.
f) V PWM Generation Chanel nastavite Pulse (16 bits value) na 50. Kaj pomeni ta parameter? Namig – največja vrednost je lahko 100 odstotkov (znak za odstotek v polja ne pišemo).
g) Na izbrani izhodni PWM pin priključite sondo osciloskopa (ne pozabite sondo ozemljiti na GND). Vključite osciloskop in ustrezno nastavite merilno območje za x in y os.
h) Sedaj generirajte kodo tako, da enostavno kliknete ikono Save in po potrebi še enkrat potrdimo generiranje kode.
Poiščite prenastavljeni parameter Pulse (ki je 50) v vaši kodi in prepišite ukaz, ki ga je generiral CubeMX: ________sConfigOC.Pulse = 50;_______. 
V kodi spremenite vrednost širine pulza na 25 %. Zapišite popravljeni ukaz v kodi:
__________sConfigOC.Pulse = 25;_________ .
 V User code begin 1 deklariramo spremenljivko :

uint16_t dutyCycle = 10;

V User code begin 3 prepišemo naslednje ukaze:

htim1.Instance->CCR1 = dutyCycle;

dutyCycle+=10;

if(dutyCycle>90) dutyCycle=10;

HAL_Delay(1000);

Ponovno naložite program in s telefonom posnamite signal na zaslonu osciloskopa.

Zapišite kaj počnejo ukazi v 1.,2. in 3. vrstici (v user code begin 3):

1. _________Nastavi PWM generacijo na spremenjlivko dutyCycle_______

2. ____dutyCycle se poveča za 10_______

3. ___Ko je dutyCycle večje od 90 se nastavi nazaj na 10 in se ponavlja_______
