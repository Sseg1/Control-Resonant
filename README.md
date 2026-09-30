# CONTROL Resonant: Arabic localization

A full Modern Standard Arabic retranslation of CONTROL Resonant, done from the game's English text. It replaces the earlier machine translation. Profanity is kept strong.

## Install

The Arabic font patch (Adobe Naskh Medium) must already be installed.

1. Copy the 4 files from `data_pack2/pc/` into `D:\games\CONTROL Resonant\data_pack2\pc\`:
   - `base-en.rmdtoc`
   - `base-en-000.rmdblob`
   - `stream0-en.rmdtoc`
   - `stream0-en-000.rmdblob`
2. Replace the existing files when Windows asks.

The files were rebuilt from the original English `base-en` and `stream0-en` packs of this game version. A game update that changes those packs means they have to be rebuilt.

## Easiest install (recommended)

`install/` has one zip per font size: `Arabic_normal.zip`, `Arabic_plus20.zip` and `Arabic_plus30.zip`. Each zip already contains the right folder layout (`data_pack2\pc\…` and `data_pack2\generic\…`), with the line-order fix and the matching font. Extract it straight into `D:\games\CONTROL Resonant\` and choose "Replace" for every file. Nothing can end up in the wrong folder.

Careful: `data_pack2\pc\` also has a large game file named `base-generic-000.rmdblob` (about 6.2 GB). The small font file with the same name belongs in `data_pack2\generic\`. If the large one is ever overwritten, the game won't start. Use "Verify integrity of game files" in Steam or Epic to repair it, then install again.

## Line-order fix and speaker names

When Arabic text wraps onto 2 or more lines, the game puts the lines in the wrong order, so you have to read from the bottom line up. `line_order_fix/data_pack2/pc/` holds the same 4 files with a fix for the screens that support text styling (warnings, descriptions, tutorials). There, every word gets its own style tag. That looks identical on screen, because all 4 installed Arabic fonts are the same. This fix is included in the `install/` zips.

Plain-text screens (subtitles, menu items) keep the text exactly as in the first build. An earlier attempt to fix them put an invisible separator between words, and it reversed the word order inside each line, so it was removed.

Speaker names: the game draws its speaker label on the left of the subtitle. These files blank that label and start every subtitle with the speaker's name instead («زوي: …»), so the name is on the right, where Arabic reading starts. The name is shown in white, because subtitles can't be coloured. It shows whatever the game's «أسماء المتحدثين في الترجمة» option is set to.

## Bigger Arabic font (optional)

The Arabic font patch comes in three sizes: `font_normal` (normal size), `font_bigger_20` (+20%) and `font_bigger_30` (+30%). `font_size_preview.png` compares them with the current size. Pick one and copy its 2 files into the game, replacing the existing ones:

- `data_pack2\pc\base-generic.rmdtoc` goes to `D:\games\CONTROL Resonant\data_pack2\pc\`
- `data_pack2\generic\base-generic-000.rmdblob` goes to `D:\games\CONTROL Resonant\data_pack2\generic\`

Always copy both files from the same folder. The two files belong together.

To go back to the previous font size, copy back the two files uploaded to the `main` branch (`base-generic.rmdtoc` goes to `pc`, `base-generic-000.rmdblob` goes to `generic`).

## Uninstall

Copy the original files back from `D:\games\CONTROL Resonant\_backup_before_arabic_patch\`.

## Sources

`Control_Arabic_Localization_final_sources.zip` holds the complete working folder:
- the translated batches in `work/loc/out/`
- the glossary and style guide
- the scripts: validator, QA, term harmonization and the build script `assemble.py`

See `work/HANDOFF.md` for the details. To rebuild after editing a translation, run:

```bash
pip install lz4 fonttools
cd work && python3 loc/assemble.py
```

The rebuilt files are written to `work/loc/build/data_pack2/pc/`.

To make the font a different size, run `python3 font_scale.py <folder with the installed base-generic files> <output folder> <factor>` from `work`. For example, a factor of `1.25` makes it 25% bigger.
