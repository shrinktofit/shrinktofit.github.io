---
title: Emscripten 相关
date: 2023-12-17 16:33:09
tags:
toc: true
---

# 结合 Emscripten 和 vcpkg

关键点：

- 设置 CMake 工具链 `CMAKE_TOOL_CHAIN_FILE` 为 `$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake`。其中 `$env{VCPKG_ROOT}` 指向 [vcpkg 仓库](https://github.com/microsoft/vcpkg) 根目录。

- 设置 CMake 变量 `VCPKG_CHAINLOAD_TOOLCHAIN_FILE` 为 `$env{EMSDK}/upstream/emscripten/cmake/Modules/Platform/Emscripten.cmake`。其中 `$env{EMSDK}` 指向 [emscripten 仓库](https://github.com/emscripten-core/emscripten) 根目录。

- 设置 CMake 变量 `VCPKG_TARGET_TRIPLET` 为 `wasm32-emscripten`。

  > 可能也不需要。

# 在 Visual Studio 2022 中获得 emscripten 类型提示

关键点：

- 在 CMake 预设中，确保 *配置预设*（`configurePresets` 数组元素） 中有以下配置:

  ```json
  "vendor": {
        "microsoft.com/VisualStudioSettings/CMake/1.0": {
            "intelliSenseMode": "windows-clang-x64"
        }
  }
  ```

