# Cheap Yellow Display MP3 Player

## Requirements

- Arduino IDE: Tested with 2.3.5
- Board package: ESP32 by Espressif 2.0.17 - 3.1.3
- Board type: "ESP32 Dev Module" or "ESP32-2432S028R CYD"

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

[1]: https://github.com/hexeguitar/ESP32_TFT_PIO ">hexeguitar/ESP32_TFT_PIO: Example project for the ESP32-2432S028 &quot;Cheap Yellow Display&quot; board."

[2]: https://github.com/hexeguitar/ESP32_TFT_PIO/tree/main/Examples/CYD28_BaseProject/lib "ESP32_TFT_PIO/Examples/CYD28_BaseProject/lib at main · hexeguitar/ESP32_TFT_PIO"

[3]: https://github.com/hexeguitar/ESP32_TFT_PIO/tree/main/Examples/CYD28_BaseProject/src "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src at main · hexeguitar/ESP32_TFT_PIO"

[4]: https://github.com/hexeguitar/ESP32_TFT_PIO/blob/main/Examples/CYD28_BaseProject/src/CYD28_audio.cpp "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src/CYD28_audio.cpp at main · hexeguitar/ESP32_TFT_PIO"

[5]: https://github.com/hexeguitar/ESP32_TFT_PIO/blob/main/Examples/CYD28_BaseProject/src/CYD28_audio.h "ESP32_TFT_PIO/Examples/CYD28_BaseProject/src/CYD28_audio.h at main · hexeguitar/ESP32_TFT_PIO"
