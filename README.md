# beamerthemehaidian

A clean, dark-themed Beamer template for astrophysics and gravitational-wave (or anything you like, including Glagolitic alphabet) presentations.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Commands Reference](#commands-reference)
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
- Clean, distraction-free slides

---

## Features

| Feature | Description |
|---------|-------------|
| **Dark background** | Black canvas with white text for low-light environments |
| **Dimmed red highlights** | Softer red (`dimred`) for emphasis without eye strain |
| **Square bullets** | Clean, modern list markers |
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
```

### Option 2: Install System-Wide (TeX Live)

```bash
# Create the directory if it doesn't exist
mkdir -p ~/texmf/tex/latex/beamerthemehaidian/

# Copy the style file
cp beamerthemehaidian.sty ~/texmf/tex/latex/beamerthemehaidian/

# Update the TeX database
texhash ~/texmf
```

### Option 3: Install Globally (Requires Root)

```bash
sudo mkdir -p /usr/local/share/texmf/tex/latex/beamerthemehaidian/
sudo cp beamerthemehaidian.sty /usr/local/share/texmf/tex/latex/beamerthemehaidian/
sudo texhash
```

---

## Quick Start

### Minimum Working Example

Create a file called `presentation.tex`:

```latex
\documentclass{beamer}
\usepackage{beamerthemehaidian}

\title{The Moon as a Spherical Lens for Gravitational Waves}
\author{Pau Amaro Seoane}
\date{}

\begin{document}

% Title slide
\maketitle

% Regular slide
\begin{frame}{Planar Dimensional Reduction}
  \begin{itemize}
    \item \idea{Planar detectors project 3D waves into a scalar.}
          \point{This creates an inescapable degeneracy.}
  \end{itemize}
\end{frame}

% Plot only
\plotslide{figures/violin_plots.pdf}

% Plot with comments
\plotslidecomment{figures/envelope.pdf}
  {The median shift grows linearly with $v_{\rm rot}$.}
  {The envelope saturates for $q = 0.30$.}

% Plain text slide
\plain{A Single Sphere Changes Everything}

% Movie slide
\slidemovie{animation.mp4}{poster.png}{Precession of the rotation axis.}

\end{document}
```

### Compilation

```bash
pdflatex presentation.tex
pdflatex presentation.tex  # Run twice for cross-references
```

### Viewing

- **Okular** (Linux): `okular presentation.pdf`
- **Adobe Acrobat** (any platform): Best support for embedded videos
- **Evince** (GNOME): Limited movie support

---

## Commands Reference

### `\idea{text}`

Wraps regular content without formatting. Used with `\point{}` to separate the main idea from the key takeaway.

```latex
\idea{This is the main idea.} \point{This is the punchline.}
```

### `\point{text}`

Highlights the key insight in **dimred italic**. Use for the single most important takeaway from each slide.

```latex
\point{The degeneracy is broken instantly.}
```

### `\plain{text}`

Creates a minimalist slide with centered text (no headers, no navigation).

```latex
\plain{Let's now consider the implications.}
```

### `\plotslide[options]{filename}`

Displays a plot centered with a 1.5-second fade-in.

```latex
\plotslide{figures/violin_plots.pdf}
\plotslide[<+->]{figures/animation.pdf}  % With overlay
```

### `\plotslidecomment[options]{filename}{comment1}{comment2}{comment3}{comment4}`

Displays a plot at the top with compact bullet comments below. Empty arguments are ignored automatically.

```latex
\plotslidecomment{figures/plot.pdf}{First comment}
\plotslidecomment{figures/plot.pdf}{First}{Second}
\plotslidecomment{figures/plot.pdf}{First}{Second}{Third}
\plotslidecomment{figures/plot.pdf}{First}{Second}{Third}{Fourth}
```

### `\slidemovie[options]{filename}{poster}{caption}`

Embeds a video with a preview image (poster) and a caption below. Click the poster to play.

```bash
# Extract a poster frame from your video:
ffmpeg -i animation.mp4 -vframes 1 poster.png
```

```latex
\slidemovie{animation.mp4}{poster.png}{Precession of the rotation axis.}
\slidemovie[width=0.95\textwidth,height=0.8\textheight]{movie.mp4}{poster.png}{Caption}
```

### `\maketitle`

Creates a clean title slide with the title and author only (no date, no navigation).

```latex
\title{My Presentation}
\author{Your Name}
\maketitle
```

---

## Troubleshooting

### Movie doesn't play

1. **Use Okular** (Linux) or **Adobe Acrobat** (any platform)
2. **Convert video to MP4** with H.264 codec:
   ```bash
   ffmpeg -i input.mov -c:v libx264 -pix_fmt yuv420p output.mp4
   ```
3. **Extract a poster frame**:
   ```bash
   ffmpeg -i animation.mp4 -vframes 1 poster.png
   ```

### "Unknown graphics extension: .mp4"

This occurs if you pass the video file directly to `\includegraphics`. Use the `\slidemovie` command which handles this correctly.

### "Command \figcommentlist already defined"

The style file includes a guard (`\ifdefined\figcommentlist\else...\fi`) to prevent this error.

---

## License

```
Copyright (c) 2026 Pau Amaro Seoane

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

---

## Author

**Pau Amaro Seoane**

- Universitat Politècnica de València, Spain
- Max Planck Institute for Extraterrestrial Physics, Garching, Germany
- Kavli Institute for Astronomy and Astrophysics at Peking University, Beijing, China

---

## Contributing

Contributions are welcome. Please submit issues and pull requests on GitHub.

---

## Acknowledgements

This template was developed in the Haidian district in Beijing and finished in Dunhuang, summer of 2026.

---

## Changelog

### 2026-01-01
- Initial release
- Core features: dark theme, `\idea{}`/`\point{}`, `\plotslide{}`, `\plain{}`
- Added `\plotslidecomment{}` with compact comment list
- Added `\slidemovie{}` with poster and caption
- Custom `\maketitle` with centered layout
