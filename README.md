# 开发环境
## 1.硬件
* 开发板：ESP32_PICO_KIT_V4.1 (主控芯片：esp32-pico-d4)
* 屏幕：中景园1.54寸TFT屏（12pin - st7789）
* 接线：
    * 屏幕 ------ 开发板
    * GND ------ GND
    * VCC ------ VCC(3.3V)
    * SCL ------ GPIO18
    * SDA ------ GPIO23
    * RES ------ GPIO4
    * DC ------ GPIO2
    * CS ------ GND
    * BLK ------ GPIO12
## 2.软件
* ubuntu(20.04.3.LTS)
* vscode(v1.63)
* platformio(v2.4.0)
* TFT_eSPI(v2.3.84) 地址:https://github.com/Bodmer/TFT_eSPI 
# 开发过程
## 1.生成工程
> 打开ubuntu的vscode的platformio首页新建工程文件如下图
![2021-12-16 11-18-03 的屏幕截图](https://user-images.githubusercontent.com/58246560/146302483-cb7ec3f3-125e-474a-a55a-69fca686174c.png)
![2021-12-16 11-18-45 的屏幕截图](https://user-images.githubusercontent.com/58246560/146302548-ea5e2f5e-8d1e-444e-8eb1-1b9a6c038696.png)
> 添加tft_espi到工程的lib
> 修改工程程序
```cpp
#include <Arduino.h>
#include "TFT_eSPI.h"
typedef TFT_eSPI SCREEN_CLASS;
#define CONFIG_SCREEN_BLK_PIN       12
void setup() {
  pinMode(CONFIG_SCREEN_BLK_PIN, OUTPUT);
  digitalWrite(CONFIG_SCREEN_BLK_PIN, HIGH);
  static SCREEN_CLASS screen;
  /* 屏幕初始化 */
  screen.begin();
  screen.setRotation(0);   
  screen.fillScreen(TFT_WHITE);  
  screen.drawRoundRect(30, 30, 200, 200,20, TFT_RED);
}
void loop() {}
```
