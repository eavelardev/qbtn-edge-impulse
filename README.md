# qbtn-edge-impulse
Firmware for qBTN board for IMU data acquisition using Edge Impulse.

## Introduction

Firmware for qBTN board from `iot-bots`
* Site: https://www.iot-bots.com/products/qbutton-wifi-and-bluetooth-esp32-iot-board
* Repo: https://github.com/iotbotscom/qButton_HW
* Base code: commit [bd01e9b](https://github.com/edgeimpulse/firmware-espressif-esp32/compare/bd01e9b..main)

Changes from the original firmware:
* `edge-impulse\ingestion-sdk-platform\espressif_esp32\ei_device_espressif_esp32.cpp`: Remove code for leds state.
```c++
void EiDeviceESP32::set_state(EiState state)
{

}
```

* `edge-impulse\ingestion-sdk-platform\sensors\ei_inertial_sensor.cpp`: change sensor address.
```c++
lis.begin(LIS3DHTR_ADDRESS_UPDATED);
```

* `main\main.cpp`: change leds behavior
```
gpio_pad_select_gpio(GPIO_NUM_4);
gpio_reset_pin(GPIO_NUM_4);
gpio_set_direction(GPIO_NUM_4, GPIO_MODE_OUTPUT);
gpio_set_level(GPIO_NUM_4, 1);   
```
## Build

```
idf.py build
```

For more info about the project, here the original repo [firmware-espressif-esp32](https://github.com/edgeimpulse/firmware-espressif-esp32).
