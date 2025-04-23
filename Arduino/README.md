# Cheap Yellow Display MP3 Player

## Requirements

- Arduino IDE: Tested with 2.3.5
- Board package: ESP32 by Espressif 2.0.17 - 3.1.3
- Board type: "ESP32 Dev Module" (2.0.17) or "ESP32-2432S028R CYD" (3.1.3)

## Installing Library

1. Fork or download the repository `ESP32_TFT_PIO` to your PC.
2. Copy `CYD_Audio` folder in `Examples/CYD28_BaseProject/lib` to your Arduino library folder (e.g. `Arduino/libraries`).
```
libraries/CYD_Audio
├── keywords.txt
├── library.json
├── library.properties
├── readme.md
└── src
    ├── CYD_Audio.cpp
    ├── CYD_Audio.h
    ├── CYD_DSP.cpp
    ├── CYD_DSP.h
    ├── CYD_audioCustom.cpp
    ├── aac_decoder/
    ├── flac_decoder/
    ├── mp3_decoder/
    ├── opus_decoder/
    └── vorbis_decoder/
```

## Sketch

1. Copy `CYD_MP3Player_Basic` to your Arduino sketch folder.  
```
Arduino/CYD_MP3Player_Basic
├── CYD_MP3Player_Basic.ino
├── CYD28_audio.cpp
└── CYD28_audio.h
```
2. Open `CYD_MP3Player_Basic.ino` and change the filename to your preferred `.mp3` file.
```cpp
  audioConnecttoSD("/test.mp3");
```
3. Save the `.mp3` file to the root of the microSD card and insert it into the slot on the CYD.
4. Select your board type and change the configuration settings from the IDE's **Tools** menu as follows:
  - Partition Scheme: "**Huge APP (3MB No OTA/1MB SPIFFS)**"
  - Upload Speed: "**460800**"
5. Compile & upload to your CYD.

## Known Issues

- The Internal DAC was deprecated in ESP32-IDF v5.0 and works with ESP32 board packages [3.1.3 (ESP-IDF v5.3)][6] and below. However, the following warning message appears when compiling:  
```
#warning "legacy adc driver is deprecated, please migrate to use esp_adc/adc_oneshot.h and esp_adc/adc_continuous.h for oneshot mode and continuous mode drivers respectively"
#warning "This set of I2S APIs has been deprecated, please include 'driver/i2s_std.h', 'driver/i2s_pdm.h' or 'driver/i2s_tdm.h' instead. if you want to keep using the old APIs and ignore this warning, you can enable 'Suppress legacy driver deprecated warning' option under 'I2S Configuration' menu in Kconfig"
```

- At runtime, the following assertion warning appears in [3.1.3 (ESP-IDF v5.3)][6].
```
i2s(legacy): i2s_calculate_adc_dac_clock(764): sample rate is too small, the mclk division exceed the maximum value 255
i2s(legacy): i2s_calculate_clock(859): ADC/DAC clock calculate failed
```

- There's a clicking sound at the beginning of playing a song in [3.1.3 (ESP-IDF v5.3)][6].

[1]: https://github.com/hexeguitar/ESP32_TFT_PIO ">hexeguitar/ESP32_TFT_PIO: Example project for the ESP32-2432S028 &quot;Cheap Yellow Display&quot; board."

[2]: https://github.com/hexeguitar/ESP32_TFT_PIO/tree/main/Examples/CYD28_BaseProject/lib "ESP32_TFT_PIO/Examples/CYD28_BaseProject/lib at main · hexeguitar/ESP32_TFT_PIO"

[3]: https://github.com/hexeguitar/ESP32_TFT_PIO/tree/main/Examples/CYD28_BaseProject/src "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src at main · hexeguitar/ESP32_TFT_PIO"

[4]: https://github.com/hexeguitar/ESP32_TFT_PIO/blob/main/Examples/CYD28_BaseProject/src/CYD28_audio.cpp "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src/CYD28_audio.cpp at main · hexeguitar/ESP32_TFT_PIO"

[5]: https://github.com/hexeguitar/ESP32_TFT_PIO/blob/main/Examples/CYD28_BaseProject/src/CYD28_audio.h "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src/CYD28_audio.h at main · hexeguitar/ESP32_TFT_PIO"

[6]: https://github.com/espressif/arduino-esp32/releases/tag/3.1.3 "Release Arduino Release v3.1.3 based on ESP-IDF v5.3 · espressif/arduino-esp32"
