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