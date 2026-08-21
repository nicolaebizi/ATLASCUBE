# AtlasCube - Development Notes

## 2026-08-19

### VU Analyzer
- Actualizat VU analyzer de la 12 la 16 bare.
- Numărul de bare se adaptează automat la lățimea widgetului.
- Adăugat afișare colorată în stil Winamp:
  - 0–60%: verde
  - 60–80%: galben
  - 80–100%: roșu
- Păstrat FFT-ul existent.
- Păstrat `VU_FFT_N = 1024`.
- Rendererul a fost păstrat optimizat pentru fluiditate.
- Upload-ul pe ESP32-S3 se face doar pentru `build/atlascube.bin` la `0x20000`, pentru a păstra configurația existentă.

### Git
- Proiectul este sincronizat cu versiunea upstream.
- Modificările locale sunt salvate în repository-ul personal.
- Repository personal: `nicolaebizi/ATLASCUBE`
### Performance — ILI9488 / VU
- ILI9488 SPI crescut la 60 MHz; 80 MHz a fost testat și nu a fost stabil.
- LVGL buffer pentru ILI9488 crescut de la 20 la 60 linii; testat și funcțional.
- `VU_TICK_MS` redus de la 50 ms la 33 ms (~30 FPS); testat și funcțional fără glitch-uri audio.
- Configurația stabilă actuală: ILI9488 60 MHz + LVGL buffer 60 linii + VU refresh 33 ms.
- Adăugat directorul `winamp/` cu materialele grafice și media folosite pentru interfața Winamp.

### Performance — ILI9488 / VU
- ILI9488 SPI crescut la 60 MHz; 80 MHz a fost testat și nu a fost stabil.
- LVGL buffer pentru ILI9488 crescut de la 20 la 60 linii; testat și funcțional.
- `VU_TICK_MS` redus de la 50 ms la 33 ms (~30 FPS); testat și funcțional fără glitch-uri audio.
- Configurația stabilă actuală: ILI9488 60 MHz + LVGL buffer 60 linii + VU refresh 33 ms.
- Adăugat directorul `winamp/` cu materialele grafice și media folosite pentru interfața Winamp.

## 2026-08-21

### Upstream update
- Actualizat proiectul local cu schimbările upstream până la v0.51.0.
- Sincronizat repository-ul personal `nicolaebizi/ATLASCUBE`.
- Păstrate modificările locale ale VU analyzer.
- Păstrat `DEV_NOTES.md`.
- Rezolvate conflictele de sincronizare fără pierderea modificărilor locale.
- Noua versiune aduce îmbunătățiri pentru OTA firmware update, automatic updates, backup/restore settings, Photo Frame, audio/podcast, Bluetooth, ESP-NOW și MQTT.

## Firmware Upload — USB / Firmware Only

Pentru update normal de firmware pe ESP32-S3, folosim doar firmware-ul aplicației:

    build/atlascube.bin

Nu încărcăm `partition-table.bin`, `ota_data_initial.bin`, `www.bin` sau `config.bin`, pentru a păstra configurația și Web UI-ul existente.

Comanda de upload:

    /Users/djnyk/.espressif/tools/python/v5.5.4/venv/bin/python /Users/djnyk/.espressif/v5.5.4/esp-idf/components/esptool_py/esptool/esptool.py -p /dev/tty.usbmodem101 -b 460800 --before default_reset --after hard_reset --chip esp32s3 write_flash 0x20000 build/atlascube.bin

Dacă portul USB se schimbă, verificăm cu:

    ls /dev/tty.usbmodem*

Important: upload-ul firmware-only la `0x20000` este metoda preferată pentru testarea modificărilor, fără a rescrie configurația.
