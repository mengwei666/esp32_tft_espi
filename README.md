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
> 添加tft_espi到工程的lib 修改通用型头文件改为自用的驱动文件，这里我使用的是（52行的 #include <User_Setups/Setup24_ST7789.h> ）打开<User_Setups/Setup24_ST7789.h>头文件，去掉默认配置，改为esp32的配置
```cpp
// Generic ESP32 setup
#define TFT_MISO 19
#define TFT_MOSI 23
#define TFT_SCLK 18
#define TFT_CS    -1 // Not connected
#define TFT_DC    2
#define TFT_RST   4  // Connect reset to ensure display initialises

// For NodeMCU - use pin numbers in the form PIN_Dx where Dx is the NodeMCU pin designation
// #define TFT_CS   -1      // Define as not used
// #define TFT_DC   PIN_D1  // Data Command control pin
// #define TFT_RST  PIN_D4  // TFT reset pin (could connect to NodeMCU RST, see next line)
//#define TFT_RST  -1    // TFT reset pin connect to NodeMCU RST, must also then add 10K pull down to TFT SCK
```
> 修改main.cpp工程文件
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
