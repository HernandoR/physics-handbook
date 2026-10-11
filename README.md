# A Modern Handbook of Physics: English / Simplified Chinese Bilingual Edition

**《现代物理学手册》英汉双语版**

A bilingual edition of B. M. Yavorsky and A. A. Detlaf's *A Modern Handbook of Physics* (Mir Publishers, Moscow, 1982). Each English paragraph is followed by its Simplified Chinese translation in a lighter tone. Chapter and section headings and figure captions are bilingual too.

本书为 B. M. 亚沃尔斯基与 A. A. 杰特拉夫所著《现代物理学手册》（米尔出版社，莫斯科，1982）的英汉双语版。每段英文原文下方紧接其简体中文译文，以稍浅的颜色排印。章节标题与图注均为双语。

## Credits

This edition stands entirely on the work of others:

- **The authors: B. M. Yavorsky and A. A. Detlaf.** They wrote the handbook. Parts One, Four and Five and the appendices are by Prof. A. A. Detlaf. Parts Two, Three, Six, Seven and Eight are by Prof. B. M. Yavorsky.
- **The English edition** was published by Mir Publishers, Moscow, in 1982. It was translated from the Russian by N. Weinstein, with T. Baranovskaya as science editor.
- **The Mir Titles project and Damitr Mazanav**, who typeset the book in LaTeX and released the sources under CC BY-NC 4.0:
  - Original repository: <https://gitlab.com/mirtitles/physics-handbook>
  - Project website: <https://mirtitles.org>

  Their careful LaTeX transcription of the book is what made this bilingual edition possible. The English text here is theirs, unchanged apart from a few typo fixes.

The Chinese translation and the bilingual layout were added in this repository. The translation was produced by AI (Claude) using a shared physics glossary and has not yet been fully reviewed by a human. Corrections are very welcome.

## Building

The book needs **LuaLaTeX** and a TeX Live installation with Chinese support: `ctex`/`luatexja` and the Fandol fonts, all included in `texlive-full`.

```sh
latexmk -lualatex handbook-physics.tex
# or: lualatex handbook-physics.tex  (run twice for cross-references)
```

The result is `handbook-physics.pdf`, about 1,400 pages.

### How the bilingual text is written

Translations sit directly below their English source, using three macros defined in `handbook-physics.tex`:

| Macro | Use |
|---|---|
| `\zhpar{…}` | Translation of the preceding English paragraph |
| `\zhtitle{…}` | Translation placed under a `\chapter` / `\section` heading |
| `\zhcap{…}` | Translation inside a `\caption` / `\sidecaption`, on a new line |

The English source lines are never modified by the translation. Removing every `\zhpar` / `\zhtitle` line and `\zhcap{…}` call gives back the original text.

## Releases

Pushing a tag that matches `release-v*` (for example `release-v1.0`) runs `.github/workflows/release.yml`. That workflow compiles the book with LuaLaTeX and publishes the PDF as a GitHub Release.

```sh
git tag release-v1.0 && git push origin release-v1.0
```

## Contributing

- **Translation fixes:** edit the `\zhpar{…}`, `\zhtitle{…}` or `\zhcap{…}` lines in the chapter files `NN-*.tex`.
- **Source errors:** the English text still contains OCR artefacts and typos, such as "held" for "field" and "arc" for "are". Where a formula symbol is wrong in the English, the Chinese usually repeats it, so fix both together.

## License

This work, like the Mir Titles edition it is based on, is released under the [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/) (CC BY-NC 4.0). You may share and adapt it for non-commercial purposes, with attribution to the authors, the Mir Titles project and this repository.
