# beamerthemehaidian

A clean, dark-themed Beamer template for astrophysics and gravitational-wave (or anything you like, including Glagolitic alphabet) presentations.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Commands Reference](#commands-reference)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Author](#author)

---

## Overview

**beamerthemehaidian** is a minimalist, dark-themed Beamer developed at the Haidian district of Beijing.

It is designed with a focus on **readability in low-light environments** (e.g., auditoriums, conference halls, and online seminars).

The theme provides a consistent visual style with:
- A black background with high-contrast white text
- Dimmed red highlights for key points
- Fade-in transitions for figures (reduces eye strain from brightness jumps)
- Clean, distraction-free slides natively integrated with Beamer's list environments

---

## Features

| Feature | Description |
|---------|-------------|
| **Dark background** | Black canvas with white text for low-light environments |
| **Dimmed red highlights** | Softer red (`dimred`) for emphasis without eye strain |
| **Square bullets** | Clean, modern list markers using native Beamer templates |
| **Fade-in transitions** | 1.5-second fade for figures and movies |
| **`\idea{}` and `\point{}`** | Semantic markup for main ideas and key takeaways |
| **`\plain{}`** | Full-screen text slides (section breaks, quotes, transitions) |
| **`\plotslide{}`** | Centered, full-size plot with fade-in |
| **`\plotslidecomment{}`** | Plot at top with compact bullet comments below |
| **`\slidemovie{}`** | Embedded video with poster image and caption |
| **Custom `\maketitle`** | Clean title slide with title and author only |
| **No navigation symbols** | Distraction-free presentation |

---

## Installation

### Option 1: Place in Your Project Directory

Simply copy `beamerthemehaidian.sty` into the same folder as your `.tex` file:

```bash
cp beamerthemehaidian.sty /path/to/your/presentation/
