# JuliaLang VSCode Multi-Threading Konfiguration


| [English](README.md) | [Español](README_es.md) | [(German) Deutsch](README_de.md) | [Français](README_fr.md) | [Italiano](README_it.md) | [Português](README_pt.md) | [(Russian) Русский](README_ru.md) | [(japanese) 日本語](README_ja.md) | [Chinese (Simplified) 简体中文](README_zh-CN.md) | [Chinese (Traditional) 繁體中文](README_zh-TW.md) | [Korean 한국어](README_ko.md) | [Polish Polski](README_pl.md) | [Turkish Türkçe](README_tr.md) | [Ukrainian Українська](README_uk.md) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

[![Julia Logo](https://raw.githubusercontent.com/JuliaLang/julia-logo-graphics/master/images/julia-language-logo-white-border.svg)](https://github.com/JuliaLang/julia-logo-graphics?tab=readme-ov-file)

Dieses Archiv stellt Anleitungen und Beispiele für die Konfiguration von Julia bereit um mehrere Threads in verschiedenen Umgebungen, einschließlich Jupyter Notebooks und Visual Studio Code, zu konfigurieren und zu nutzen.

## Video Anleitung

[![Schau das Video](https://img.youtube.com/vi/your_video_id/maxresdefault.jpg)](https://www.youtube.com/watch?v=your_video_id)
Dieses Video zeigt dir den Prozess, wie man Julia für Multithreading bereitstellt, inklusive einer Anleitung wie du deine Ummgebung einstellen musst und verifizieren kannst das alles funktioniert.



## Voraussetzungen

- Julia version 1.5 oder neuer
- Visual Studio Code mit der Julia Erweiterung

## Thread Menge einstellen

### Einstelluen der Umgebungsvariable `JULIA_NUM_THREADS`

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

### Einstellen von VS Code

Erstelle oder aktualisiere `.vscode/settings.json` in deinem Projekt (siehe die [settings.json](.vscode/settings.json) Datei in diesem Archiv):

(Bei Jupyter Notebooks (Dateien: .ipynb) nutze in VSCode diese Option)

```json
{
  "julia.NumThreads": 8,
  "settingsSync.ignoredSettings": [
    "-julia.NumThreads"
  ]
}
```

Alternativ, starte VS Code über PowerShell:

```powershell
$Env:JULIA_NUM_THREADS = "8"
code .
```

## Verifiziere Thread Verfügbarkeit

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

## Weiterlesen

- Offizielle Julia Multi-threading Dokumentation: [https://docs.julialang.org/en/v1/manual/multi-threading/](https://docs.julialang.org/en/v1/manual/multi-threading/)


## Probleme und Mitwirkungen
When du irgendwelche Probleme entdeckst oder verbesserungsvorschläge hast, öffne bitte ein "Problem" in diesem Archiv. Mitwirkungen sind willkommen!

## Mitwirkende:
Siehe eine ganze Liste der Mitwirkenden [contributors](contributors.md).

## Kontakt
Bei Fragen oder Feedback, kontaktiere den Archiv Leiter unter [@Happyuky7](https://github.com/Happyuky7/).

## Wissenswertes
Dieses Projekt wurde durch den gebrauch von effizienten Multi-Threading in Julia Applikationen inspiriert, das ziel ist es einen klaren und prägnanten Leitfaden für alle Nutzer auf jeder Stufe bereitzustellen. Zusätzlich wurde dieses Projekt fertiggestellt, da der Author es für eine Universtäts-Prüfung benötigte wo ein Blatt darüber geschrieben werden musste.

## Zusätzliche Resourcen
- [JuliaLang Offizielle Dokumentation](https://docs.julialang.org/)
- [JuliaLang Offizielle Dokumentation - Multi-threading](https://docs.julialang.org/en/v1/manual/multi-threading/)
- [Visual Studio Code Julia Extension](https://marketplace.visualstudio.com/items?itemName=julialang.language-julia)
