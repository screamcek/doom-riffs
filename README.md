# doom-riffs
Guitar riffs &amp; tabs in Drop D
D2 – A2 – D3 – G3 – B3 – E4
# drop_d_tuner.py
# Jednoduchý generátor referenčných tónov pre Drop D ladenie 🎸
# Vyžaduje: pip install sounddevice numpy

import numpy as np
import sounddevice as sd

# frekvencie pre Drop D (Hz)
notes = {
    "D2": 73.42,
    "A2": 110.00,
    "D3": 146.83,
    "G3": 196.00,
    "B3": 246.94,
    "E4": 329.63
}

duration = 2.5  # sekundy pre každý tón
samplerate = 44100

for name, freq in notes.items():
    print(f"Hrá sa {name} ({freq:.2f} Hz)")
    t = np.linspace(0, duration, int(samplerate * duration), endpoint=False)
    wave = 0.5 * np.sin(2 * np.pi * freq * t)
    sd.play(wave, samplerate)
    sd.wait()

print("🎸 Hotovo! Gitara by mala znieť ako búrka nad Mordorom.")

