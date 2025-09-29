# Face Recognition (Fork with Prebuilt dlib)

Have you ever faced the **classic dlib installation problem**?

On Windows (and especially Python 3.13+), installing [`face_recognition`](https://pypi.org/project/face-recognition/) from PyPI often fails because its dependency `dlib` requires **CMake + Visual Studio Build Tools** to compile from source.

Example error:

<img width="1176" height="287" alt="image" src="https://github.com/user-attachments/assets/8626ad79-d22a-43a8-837e-3ff7ebc1905f" />

To solve this, this fork provides a **precompiled/custom build of `face_recognition` bundled with a prebuilt `dlib` wheel**.

* No CMake
* No Visual Studio setup
* Works on Python 3.9 → 3.13 (Windows)

---

## Installation

Instead of installing from PyPI, install directly from this repository:

```bash
pip install "face_recognition @ git+https://github.com/lovnishverma/face_recognition.git"
```

Or add this line to your `requirements.txt`:

```text
face_recognition @ git+https://github.com/lovnishverma/face_recognition.git
```

<img width="855" height="231" alt="image" src="https://github.com/user-attachments/assets/131c550c-ef0f-473b-b938-c88ed6043275" />

---

## Why this works

* **Official package** → depends on `dlib`, which requires compiling.
* **This fork** → uses prebuilt `dlib` wheels, skipping compilation.
* **Result** → smooth installation on Windows and new Python versions.

---

## Features

* Find faces in pictures
* Find and manipulate facial features
* Recognize and compare faces
* Command-line tools: `face_recognition` and `face_detection`

[![PyPI](https://img.shields.io/pypi/v/face_recognition.svg)](https://pypi.python.org/pypi/face_recognition)
[![Build Status](https://github.com/ageitgey/face_recognition/workflows/CI/badge.svg?branch=master\&event=push)](https://github.com/ageitgey/face_recognition/actions?query=workflow%3ACI)
[![Documentation Status](https://readthedocs.org/projects/face-recognition/badge/?version=latest)](http://face-recognition.readthedocs.io/en/latest/?badge=latest)

---

## Examples

### Detect faces

```python
import face_recognition
image = face_recognition.load_image_file("your_file.jpg")
face_locations = face_recognition.face_locations(image)
```

### Detect facial features

```python
import face_recognition
image = face_recognition.load_image_file("your_file.jpg")
face_landmarks_list = face_recognition.face_landmarks(image)
```

### Compare faces

```python
import face_recognition

known_image = face_recognition.load_image_file("biden.jpg")
unknown_image = face_recognition.load_image_file("unknown.jpg")

biden_encoding = face_recognition.face_encodings(known_image)[0]
unknown_encoding = face_recognition.face_encodings(unknown_image)[0]

results = face_recognition.compare_faces([biden_encoding], unknown_encoding)
```

---

## Command-Line Usage

After installation, you also get two tools:

* `face_recognition` → recognize faces in a folder of images
* `face_detection` → find face locations in images

Example:

```bash
face_recognition ./pictures_of_people_i_know/ ./unknown_pictures/
```

---

## Requirements

* Python 3.9+ (tested up to 3.13)
* Works on Windows out of the box
* macOS/Linux users should use the [official package](https://github.com/ageitgey/face_recognition)

---

## Acknowledgements

* Original library by [@ageitgey](https://github.com/ageitgey)
* `dlib` by [@davisking](https://github.com/davisking)
* This fork just packages prebuilt binaries for easier installation on Windows

---
