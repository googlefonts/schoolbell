# Schoolbell

No source of this family was ever published: the fonts Google Fonts ships
were its only form. The sources in `sources/` were converted from those
fonts with [babelfont-rs](https://github.com/felipesanches/babelfont-rs/tree/2026-10-22), and
build with [gftools-builder](https://github.com/simoncozens/gftools-rust)
and fontc.

The fonts they were converted from remain in the git history.

How these sources were checked against the released fonts (the tools, this family's plan and the logs): https://github.com/felipesanches/gf-source-modernization.

## Earlier sources

Where this family was published before, kept on record; none of these holds a source of it:


## Known differences from the released fonts

These sources rebuild the fonts Google Fonts ships, except for the following, which were reviewed and deliberately left as they are:

- The release kerns with a legacy `kern` table (1046 pairs) and has no GPOS; these sources kern through a GPOS kern feature, which is how fontc builds kerning. HarfBuzz shapes every kerned pair alike in both (the functional gate). Decided 2026-10-01: releases with an old kern table are accepted and disclosed.
- The release has no glyph instructions: its font program defines functions that no glyph calls, and its control value program only turns on dropout control (SCANCTRL 511, SCANTYPE 4). These sources carry no TrueType instructions, and the build is hinted by ttfautohint, as for every release that has a font program: the outlines, spacing and layout are the release's, its rendering at small sizes under a TrueType interpreter is not. Hinting is not compared by the gates.
