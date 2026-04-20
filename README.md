# WalaBeat — Air Drums with Walabot

Wave your hands in front of the Walabot sensor to play drums — no contact required.

---

## Scripts

### `WalaBeat/walabeat2_gui.py` — 8-pad drum machine *(new)*

A top-down radar fan view with 8 independent pads arranged in a 4 azimuth × 2 depth grid:

```
         LEFT  ←————————————————→  RIGHT
FAR    [Crash] [  Tom ] [ Ride ] [Open HH]
NEAR   [Hi-Hat] [ Kick ] [Snare] [  Clap ]
              ↑ sensor faces you ↑
```

Dead zones between adjacent pads reduce cross-talk. Each pad glows proportionally to signal energy and flashes bright on a hit. A sustained fast wave in the near outer-right zone triggers a **snare roll**.

**Run:**
```bash
cd WalaBeat
python3 generate_sounds.py   # generate WAV files once (standard library only)
python3 walabeat2_gui.py
```

### `WalaBeat/walabeat_gui.py` — 2-pad drum machine *(original)*

The classic WalaBeat: left half → hi-hat, right half → snare. Place the sensor flat on a table facing up.

```bash
python3 walabeat_gui.py
```

---

## Requirements

- **Hardware**: Walabot Makers Series USB sensor
- **OS**: Linux x86_64 (Ubuntu / Debian recommended)
- **Python**: 3.8+
- **Walabot SDK**: install the `.deb` from [walabot.com](https://walabot.com)
- **Python package**: `pip install WalabotAPI`
- **tkinter**: `sudo apt-get install python3-tk`

---

## Walabot API used

Both scripts use `GetRawImageSlice()` with `PROF_SENSOR` + `FILTER_TYPE_MTI`.  
`walabeat2_gui.py` divides the 2D slice into a 4×2 zone grid;  
`walabeat_gui.py` uses a simple left/right split.
