# Streamface 

A framework for extraction of face images from YouTube videos and livestreams.

## Installation

Clone repository and install required packages using
```
pip install -r requirements.txt
```

## Usage

### Frame Extraction

```python
from streamface import StreamCapture

capture = StreamCapture(
    name='skynews',
    url='https://www.youtube.com/watch?v=9Auq9mYxFEE',
    output_dir='./data/skynews',
    batch_size=50,
    empty_threshold=0.95,
    blur_threshold=50,
    similarity_threshold=0.9,
    reconnect_interval=500,
    log_interval=100
)

capture.call()
```

### Face Extraction

```python
from streamface import FaceExtraction

extract = FaceExtraction(
    input_dir='./data/skynews',
    output_dir='./data/skynews',
    detection='retinaface',
    batch_size=32,
    conf_threshold=0.95,
    size_threshold=0.005,
    blur_threshold=25,
    match_thresholds=(0.75, 0.75),
    face_size=(256, 256),
    aligned_size=(128, 128),
    padding=0.5,
    margin=1.0,
    resume=True,
    log_interval=100
)

extract.call()
```

### Face Analysis

```python
from streamface import FaceAnalysis

analyze = FaceAnalysis(
    input_dir='./data/skynews',
    output_dir='./data/skynews',
    representation='arcfacenet',
    demographics='fairface',
    expression='dfemotion',
    mask='chandrikanet',
    pose='whenet',
    batch_size=128,
    resume=True,
    log_interval=100
)

analyze.call()
```