# Water Data to Music

This project explores how hydrological measurement data (water level time series) can be transformed into a musical composition using Python.

Scientific time series from multiple measurement stations are mapped to musical pitches within defined instrumental ranges and musical scales (default: D Dorian).  
From this mapping, a multi-track MIDI composition is generated and visualized as a score-like image.

The goal is to combine:

- scientific data  
- algorithmic composition  
- visualization  

into one reproducible workflow.

---

## Features

- Load and preprocess hydrological time series (CSV)
- Assign measurement stations to instruments (Violin, Clarinet, Cello, etc.)
- Map data values to musical scales within realistic instrument ranges
- Generate a multi-track MIDI score (e.g. 64 bars in 4/4)
- Export a visual “partiture” (one row per instrument, all bars in one line)

Designed to be usable both for:

- musical composition  
- scientific/artistic visualization  

---

## Requirements

Python 3.9+

Main dependencies:

- numpy  
- pandas  
- matplotlib  
- mido  

Install with:

pip install numpy pandas matplotlib mido

(For Google Colab: !pip -q install mido)

---

## Data Format

The input CSV is expected to contain:

- a time column (date)
- one column per measurement station, e.g.:

date, P343, P33, P501, P37, ...

Each station corresponds to one instrument voice.

---

## Workflow

1. Map data to MIDI pitches

mapped = map_data_to_midi(df)

Creates a dataframe with:

- time  
- station  
- instrument name  
- MIDI program number  
- mapped MIDI pitch  

2. Generate rhythmic MIDI composition

midi_path = render_rhythmic_midi(mapped, bars=64, tempo_bpm=80)

Produces a multi-track MIDI file with:

- one track per instrument  
- 64 bars in 4/4  
- note values: eighth, quarter, half, whole (quarter notes preferred)  

3. Create visual partiture

fig, ax = midi_to_partiture_image(midi_path, bars=64)

Creates an image where:

- each instrument = one horizontal row  
- all bars are shown in one line  
- notes are drawn as time-aligned bars  

---

## Artistic Concept

- Minimum data value → lowest playable scale tone of the instrument  
- Maximum data value → highest playable scale tone of the instrument  
- Intermediate values are linearly mapped and quantized to scale steps  
- Rhythm is generated probabilistically but aligned across all voices  

This ensures that:

- the data defines the melodic contour  
- the composition rules define musical coherence  

---

## Output

- .mid file (importable into notation software or DAWs)  
- .png visualization of the score  
- reproducible pipeline from data to music  

---

## How to cite

If you use this code or methodology in academic work, please cite it as:

Reinhardt, E. F., & Basilio Hazas, M.. (2026). Water Data to Music: Sonification of hydrological time series using Python. GitHub repository. https://github.com/USERNAME/REPOSITORY

BibTeX:

@software{waterdatatomusic2026,
  author       = {Reinhardt, Esther Fee and Basilio Hazas, Mónica},
  title        = {Water Data to Music: Sonification of hydrological time series using Python},
  year         = {2026},
  publisher    = {GitHub},
  url          = {https://github.com/Eratofee/WaterMusicGeneration},
  note         = {Version 1.0}
}

---

## License

MIT

---

## Authors

Scientific data & concept:  
Mónica Basilio Hazas, Esther Fee Reinhardt

Composition & code:  
Esther Fee Reinhardt
