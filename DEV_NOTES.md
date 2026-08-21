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
