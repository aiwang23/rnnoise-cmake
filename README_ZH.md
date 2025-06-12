# rnnoise-cmake

[English](./README.md) | [中文](./README_ZH.md)

这是 [rnnoise](https://github.com/xiph/rnnoise) 的 CMake 包装项目，支持在 Windows（MSVC、MinGW）和 Linux 上构建，无需更改原始代码。

> ⚠️ 使用前请先下载模型文件到 `data/` 文件夹中（见下文）。

## ✅ 项目结构

 ```
 .
 |-> README.md              # 本文档
 |-> CMakeLists.txt         # 根目录构建脚本
 |-> msvc_include#          # 为 MSVC 提供的兼容头文件
 |-> rnnoise                # 原始 rnnoise 源码
 +-> data                   # 存放模型数据文件
     |-> rnnoise_data.c
     |-> rnnoise_data.h
     |-> rnnoise_data_little.c
     +-> rnnoise_data_little.h
     
 ```

## ✅ 使用说明

### 1. 克隆项目

```bash
git clone --recursive https://www.github.com/aiwang23/rnnoise-cmake.git
```

### 2. 下载模型

从官方地址[https://media.xiph.org/rnnoise/models](https://media.xiph.org/rnnoise/models)下载模型,并解压到data/ 目录

最终应包含:

```
data
|-> rnnoise_data.c
|-> rnnoise_data.h
|-> rnnoise_data_little.c
+-> rnnoise_data_little.h
```

### 3. 编译

```bash
cmake -S . -B build
cmake --build build
```

## 🔧 如何在你的项目中使用

```cmake
add_subdirectory(rnnoise-cmake)
target_link_libraries(your_target PRIVATE rnnoise)
```

## 📥 输入要求

⚠️ 使用 RNNoise 前，请确保输入音频符合以下格式，否则可能导致噪声消除效果异常甚至崩溃：

- 采样率：48kHz（48000Hz）
- 通道数：单声道（Mono）
- 采样位深：16-bit 整数（s16，即 int16_t）

若使用其他格式音频（如44.1kHz、立体声、float等），请先使用音频处理库（如 FFmpeg、SoX 或 libsamplerate）进行预处理转换。

## ✨ 特性

- ✅ 跨平台构建（Windows / Linux）
- ✅ CMake 静态库封装
- ✅ 非侵入式包装 rnnoise 原始项目
- ✅ 支持 MSVC 编译器的兼容性处理

## 📃 License

本项目是对  [rnnoise](https://github.com/xiph/rnnoise) 的 CMake 封装，原始项目遵循 BSD 3-Clause License 协议。
本封装由 aiwang23（爱喝水的小汪）于 2025 年创建，并同样遵循 BSD 3-Clause License 协议发布。

详细条款请参见 [LICENSE](./LICENSE)
