# 开发环境
## 1.硬件
* 开发板：ESP32_PICO_KIT_V4.1 (主控芯片：esp32-pico-d4)
* 屏幕：中景园1.54寸TFT屏（12pin - st7789）
* 接线： 
| 屏幕 | 开发板 |
| :----- 	| -------:	 |
| GND | GND|
|VCC|VCC(3.3V)|
*** 屏幕 ------ 开发板
*** GND ------ GND
*** VCC ------ VCC(3.3V)
*** SCL ------ GPIO18
*** SDA ------ GPIO23
*** RES ------ GPIO4
*** DC ------ GPIO2
*** CS ------ GND
*** BLK ------ GPIO12
## 2.软件
* ubuntu(20.04.3.LTS)
* vscode(v1.63)
* platformio(v2.4.0)
* TFT_eSPI(v2.3.84) 地址:https://github.com/Bodmer/TFT_eSPI 
