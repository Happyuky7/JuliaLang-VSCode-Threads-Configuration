# JuliaLang VSCode Multi-Threading Configuration


| [English](README.md) | [Español](README_es.md) | [(German) Deutsch](README_de.md) | [Français](README_fr.md) | [Italiano](README_it.md) | [Português](README_pt.md) | [(Russian) Русский](README_ru.md) | [(japanese) 日本語](README_ja.md) | [Chinese (Simplified) 简体中文](README_zh-CN.md) | [Chinese (Traditional) 繁體中文](README_zh-TW.md) | [Korean 한국어](README_ko.md) | [Polish Polski](README_pl.md) | [Turkish Türkçe](README_tr.md) | [Ukrainian Українська](README_uk.md) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

[![Julia Logo](https://raw.githubusercontent.com/JuliaLang/julia-logo-graphics/master/images/julia-language-logo-white-border.svg)](https://github.com/JuliaLang/julia-logo-graphics?tab=readme-ov-file)

This repository provides instructions and examples for configuring Julia to use multiple threads in various environments, including Jupyter notebooks and Visual Studio Code.

## Video Tutorial

[![Watch the video](https://img.youtube.com/vi/your_video_id/maxresdefault.jpg)](https://www.youtube.com/watch?v=your_video_id)
This video will guide you through the process of setting up Julia for multi-threading, including how to configure your environment and verify that it is working correctly.



## Prerequisites

- Julia version 1.5 or later
- Visual Studio Code with the Julia extension

## Configuring Thread Count

### Setting `JULIA_NUM_THREADS` Environment Variable

**Linux/macOS** (bash/zsh)

```bash
export JULIA_NUM_THREADS=8
julia
```

**Windows PowerShell**

```powershell
$Env:JULIA_NUM_THREADS = "8"
julia
```

### Configuring VS Code

Create or update `.vscode/settings.json` in your project (view the [settings.json](.vscode/settings.json) file in this repository):

(If using Jupyter Notebooks (Files: .ipynb) in VSCode using this option)

```json
{
  "julia.NumThreads": 8,
  "settingsSync.ignoredSettings": [
    "-julia.NumThreads"
  ]
}
```

Alternatively, launch VS Code from PowerShell:

```powershell
$Env:JULIA_NUM_THREADS = "8"
code .
```

## Verifying Thread Availability

```julia
using Base.Threads
println("Available threads: ", nthreads())

if nthreads() < 2
    error("At least 2 threads are required for this solution.")
end
```

## Multithreading Test

```julia
Threads.@threads for i in 1:16
    println("Thread ", threadid(), " processing i = ", i)
end
```

## Further Reading

- Official Julia Multi-threading Documentation: [https://docs.julialang.org/en/v1/manual/multi-threading/](https://docs.julialang.org/en/v1/manual/multi-threading/)


## Issues and Contributions
If you encounter any issues or have suggestions for improvements, please open an issue on this repository. Contributions are welcome!

## Contributions:
View full list of [contributors](contributors.md).

## Contact
For any questions or feedback, please contact the repository maintainer at [@Happyuky7](https://github.com/Happyuky7/).

## Acknowledgments
This project was inspired by the need for efficient multi-threading in Julia applications and aims to provide a clear and concise guide for users at all levels. Additionally, it was completed because the author needed it for a university exam where a paper had to be written.

## Additional Resources
- [JuliaLang Official Documentation](https://docs.julialang.org/)
- [JuliaLang Official Documentation - Multi-threading](https://docs.julialang.org/en/v1/manual/multi-threading/)
- [Visual Studio Code Julia Extension](https://marketplace.visualstudio.com/items?itemName=julialang.language-julia)


