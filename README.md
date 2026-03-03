<p align="center">
  <img src="https://avatars.githubusercontent.com/u/209633456?v=4" width="160" alt="RedTail Indicators Logo"/>
</p>

<h1 align="center">RedTail FRVP</h1>

<p align="center">
  <b>A structure-triggered Fixed Range Volume Profile indicator for NinjaTrader 8.</b><br>
  Automatically builds volume profiles with Fibonacci levels, Anchored VWAP, and K-Means cluster detection — all anchored to market structure events.
</p>

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-FFDD00?style=flat-square&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>

---

## Overview

RedTail FRVP is a standalone extraction of the FRVP engine from the full [RedTail Market Structure](https://github.com/3astbeast/RedTail-Market-Structure) indicator. It includes its own internal market structure detection (BOS/CHoCH) that serves as the trigger for automatically generating Fixed Range Volume Profiles. When a structural event fires, the indicator builds a volume profile across the swing range and overlays Fibonacci retracements, an Anchored VWAP, and K-Means cluster levels — all without any manual drawing required.

If you want the full market structure suite (order blocks, strong/weak levels, displacement candles, equal highs/lows, liquidity sweeps), use the Market Structure indicator instead. If you only need the auto-triggered FRVP with its analysis layers, this is the lightweight alternative.

---

## Market Structure Engine

The internal structure engine identifies swing highs and lows to detect BOS and CHoCH events that trigger the FRVP.

- **Swing Length** — Configurable lookback for swing detection
- **BOS Confirmation** — Configurable confirmation logic for Break of Structure validation

The structure engine runs internally and is not drawn on the chart — it exists solely to determine when and where to anchor the FRVP.

---

## FRVP Trigger

- **CHoCH** — Draws the FRVP immediately when a Change of Character occurs
- **BOS** — Waits for a confirming Break of Structure after the CHoCH before drawing
- **Keep Previous FRVP** — Optionally retain the prior FRVP on the chart when a new structure event fires. When disabled, only the most recent FRVP is shown.

---

## Volume Profile

The core volume profile histogram built across the swing range defined by the structure event.

- Configurable **number of rows** for profile resolution
- **Profile Width %** — Width of the histogram as a percentage of the swing range width
- **Alignment** — Left or Right docking
- **Volume Types:** Standard, Bullish, Bearish, or Both (polarity coloring with independent bullish/bearish bar colors)
- Configurable bar thickness and opacity
- **Boundary outline** with independent color, opacity, and width
- **Labels** for POC and Value Area with optional price display and configurable font size

**Gradient Fill** — Optional gradient effect on volume bars that fades from transparent to solid, with configurable intensity (0–100).

**Adaptive Rendering** — Auto-sizes bars to fill available pixel space and smooths the profile shape with Gaussian smoothing passes (0 = raw data, 2–3 recommended, up to 5 for very smooth). Configurable min/max bar pixel height. Alternative to Manual mode which uses a fixed bar thickness.

---

## POC & Value Area

- **Point of Control (POC)** — The highest-volume price level within the FRVP range. Configurable color, width, style, and opacity.
- **Value Area** — Configurable percentage (50–95%, default 70%). VA bars render in a distinct color. Optional VAH/VAL boundary lines with independent color, width, style, and opacity.
- **Extend POC/VA Right** — Extend POC and VA lines beyond the FRVP zone to the chart edge for ongoing reference.

---

## Fibonacci Retracements

Up to 10 customizable Fibonacci levels overlaid on the FRVP swing range.

- Each level has an independent percentage value and color (set to -1 to disable any level)
- Default levels: 0, 23.6%, 38.2%, 50%, 61.8%, 78.6%, 100% with 3 extension slots
- Configurable line width, style, and opacity
- Optional right extension beyond the FRVP zone
- Optional price display on Fib labels with configurable font size

---

## Anchored VWAP

An Anchored VWAP computed from the swing origin of the FRVP zone, providing a volume-weighted average price reference from the point where the structural event began.

- Configurable color, width, style, and opacity
- Optional right extension beyond the FRVP zone
- Optional label display

---

## K-Means Cluster Levels

Segments the FRVP volume distribution into clusters using the K-Means algorithm, then detects the POC within each cluster to identify high-volume nodes at different price regions within the swing range.

- **Number of Clusters** — 2 to 10 clusters
- **K-Means Iterations** — 5 to 50 iterations for convergence
- **Rows per Cluster** — Volume profile resolution within each cluster for POC detection (5–100)
- Configurable line width, style, and opacity
- Optional right extension and labels
- Up to 5 independently colored cluster levels

---

## Alerts

- **Alert on BOS** — Sound alert when a Break of Structure is detected
- **Alert on CHoCH** — Sound alert when a Change of Character is detected
- Independent .wav sound file configuration for each alert type

---

## Installation

1. Download the `.cs` file from this repository
2. Open NinjaTrader 8
3. Go to **Tools → Import → NinjaScript Add-On**
4. Select the downloaded file and click **OK**
5. The indicator will appear in your **Indicators** list — add it to any chart

---

## Part of the RedTail Indicators Suite

This indicator is part of the [RedTail Indicators](https://github.com/3astbeast/RedTailIndicators) collection — free NinjaTrader 8 tools built for futures traders who demand precision.

---

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-Support_My_Work-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>
