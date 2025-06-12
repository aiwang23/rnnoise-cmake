# rnnoise-cmake

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

## ✨ 特性

- ✅ 跨平台构建（Windows / Linux）
- ✅ CMake 静态库封装
- ✅ 非侵入式包装 rnnoise 原始项目
- ✅ 支持 MSVC 编译器的兼容性处理
- ✅ 模型 .model 文件转 .c/.h 文件嵌入

## 📃 License

本项目基于原始 rnnoise 项目，并遵循其 BSD-style License

