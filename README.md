# RAK3272 TIC (Teleinfo) LoRaWAN Shield

This shield is used to get French energy meter called Teleinfo data with WisDuo LoRaWAN RAK3272 SIP Breakout board:

<img src="https://github.com/hallard/RAK3272-TIC/raw/main/pictures/RAK3272-SIP.png" alt="Top" width="40%" height="40%">&nbsp;

# Detailed Description

**V1.0**

- On Board 3.3V regulator used when powering thru batteries (Vin > 3.6V)
- Low Power Mode option driving some GPIO to disable TIC
- Led to indicated TIC reception signal
- User Red and Green Led 
- User button (pull down)
- On board I2C Pullups (4K7)
- Footprint for Battery connector 
- QWICC / Stemma standard connector

:warning: Despite the fact that RAK3272-SIP Breakout announced as xBee format, this is far from the case because:

- xBee as 16 pins on the header this one 18 pins
- xBee pinout is totally different (power and other)
- least but not least, headers spacing of external raws of RAK3272 are different than xBee.

So in V1.0 version of my shield you will need to bend headers of RAK3272 and shield so you can plug it, that's a shame.

Anyway, if you're designing shield for RAK3272 don't take xBee spacing format for external headers, it won't fit 

# Pinout

Look at the schematics for more informations, easy to understand. Wiring on the RAK3272 Teleinfo shield is as follow:

| Pin Function | RAK3272   | STM32WL |
|  :---        |  :---:    |  :---:  | 
| TIC Rx       | UART1_RX  |   PB7   |
| TIC Enable   | SPI1_CLK  |   PA5   | 
| Led TIC      |   PA8     |   PA8   | 
| Led Red      | SPI1_MISO |   PA6   | 
| Led Green    | SPI1_MOSI |   PA7   | 
| Button       | SPI1_NSS  |   PA4   | 
| I2C SDA      | I2C2_SDA  |  PA11   |
| I2C SDL      | I2C2_SCL  |  PA12   |

:warning: Button is boot0 button, to avoid adding one more button for user, I wired Boot0 to PA4 to we can read button state, but since it's boot0 it has pulldown resistor and it is active High.

To enable reading TIC you need:

- Drive High ping PA5 (mandatory)
- Drive High ping PA8 (to eable TIC Led to blink on data reception on Serial)
- Read Teleinfo on UART1_RX (PB7)

# Schematics

<img src="https://github.com/hallard/RAK3272-TIC/raw/main/pictures/RAK3272-TIC-sch.png">

# Boards

## Assembled (V1.0)

<img src="https://github.com/hallard/RAK3272-TIC/raw/main/pictures/RAK3272-TIC-top.png" alt="Top" width="40%" height="40%">&nbsp;&nbsp;
<img src="https://github.com/hallard/RAK3272-TIC/raw/main/pictures/RAK3272-TIC-bot.png" alt="Bottom" width="40%" height="40%">

## Shield Plugged on RAK3272 SIP Breakout

<img src="https://github.com/hallard/RAK3272-TIC/raw/main/pictures/RAK3272-TIC-assembled.png" width="40%" height="40%" alt="RAK3272 Teleinfo Assembled Top">&nbsp;

# Firmware 

You can write your own and use with [LibTeleinfo](https://github.com/hallard/LibTeleinfo) library I wrote if you want to get rid of driving teleinfo stuff (chekout some [examples](ttps://github.com/hallard/LibTeleinfo/tree/master/examples)).

To Be Completed

## I2C 

You can add fancy I2C display or even I2C sensors, there is a Stemma QWIIC connector on board. Since I2C VCC is conencted to 3.3V, your I2C should works in 3.3V or 5V or 5V ones (They all have level shifter since majorty of sensors works at 3.3V)


# Support and discussion

If you have any issue or just want to discuss on this project, please use community [forum](https://community.ch2i.eu/category/19/wemos-teleinfo)

# License

<img alt="Creative Commons Attribution-NonCommercial 4.0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png">   

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/)    
If you want to do commercial stuff with this project, please contact [CH2i company](https://ch2i.eu/en#support) so we can organize an simple agreement.

# Lazy building your own? 

You can order this shield fully assembled with some extra on tindie (soon)

<a href="https://www.tindie.com/products/25467/"><img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-mediums.png" alt="I sell on Tindie" width="150" height="78"></a>

# Misc

See news and other projects on my [blog][2] 
 
[2]: https://hallard.me

[20]: https://store.rakwireless.com/products/wisduo-breakout-board-rak3272-sip
[21]: https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3272-SiP-Breakout-Board/Datasheet
[22]: https://www.smart-prototyping.com/Mini-D1-PRO-Development-Board-ESP8266-4M-16M
[23]: https://www.az-delivery.de/fr/products/esp32-d1-mini
[24]: https://www.tindie.com/products/25467/

