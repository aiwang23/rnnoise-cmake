# rnnoise-cmake

[English](./README.md) | [中文](./README_ZH.md)

This is a CMake wrapper project for [rnnoise](https://github.com/xiph/rnnoise) that supports building on Windows (MSVC,
MinGW) and Linux without changing the original code.

> ⚠️ Please download the model file to the 'data/' folder before using it (see below).

## ✅ Project Structure

```
 .
 |-> README.md # This document
 |-> CMakeLists.txt # Root build script
 |-> msvc_include# # Compatible header files provided for MSVC
 |-> rnnoise # Original rnnoise source code
 +-> data # Hold the model data file
     |-> rnnoise_data.c
     |-> rnnoise_data.h
     |-> rnnoise_data_little.c
     +-> rnnoise_data_little.h
     
```

## ✅ Instructions for use

### 1. Clone the project

```bash
git clone --recursive https://www.github.com/aiwang23/rnnoise-cmake.git
```

### 2. Download the model

Download the model from the official
address [https://media.xiph.org/rnnoise/models] (https://media.xiph.org/rnnoise/models) and extract it to the data/
directory

It should ultimately include:

```
data
|-> rnnoise_data.c
|-> rnnoise_data.h
|-> rnnoise_data_little.c
+-> rnnoise_data_little.h
```

### 3. compile

```bash
cmake -S . -B build
cmake --build build
```

## 🔧 How to use it in your project

```cmake
add_subdirectory(rnnoise-cmake)
target_link_libraries(your_target PRIVATE rnnoise)
```

## 📥 Enter the requirements

⚠️ Before using RNNoise, make sure that the input audio matches the following formats, otherwise it may cause abnormal
noise cancellation or even crash:

- Sample rate: 48kHz (48000Hz)
- Number of Channels: Mono
- Bit depth: 16-bit integer (s16, i.e. int16_t)

If you are using other audio formats (e.g., 44.1kHz, stereo, float, etc.), use an audio processing library (e.g.,
FFmpeg, SoX, or libsamplerate) for pre-processing conversion first.

## ✨ Features

- ✅ Cross-platform build (Windows/Linux)
- ✅ CMake static library encapsulation
- ✅ Non-intrusive packaging of rnnoise original items
- ✅ Support MSVC compiler compatibility handling

## 📃 License

This project is a CMake wrapper for [rnnoise](https://github.com/xiph/rnnoise) and the original project is licensed
under the BSD 3-Clause License.
This package was created by aiwang23 in 2025 and is also released under the BSD 3-Clause License.

FOR MORE INFORMATION, PLEASE REFER TO [LICENSE](./LICENSE)
