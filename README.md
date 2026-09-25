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
