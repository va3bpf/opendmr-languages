# OpenDMR interface languages

The interface languages and font files of [OpenDMR](https://github.com/va3bpf/OpenDMR) (firmware for the Baofeng
DM-32 / DM-32UV). The firmware has English only; the other languages are here, kept by their translators.
中文：[README.md](README.md)

## Using them

1. Download this repository (Code → Download ZIP) and unzip it.
2. In the OpenDMR CPS, connect the radio, open the Languages page, Choose folder: the unzipped `languages` folder.
3. Tick the languages wanted and Write to the radio (Chinese with its font about 2 minutes).
4. Choose one on the radio in Options → Language (the row is called Language in every language).

Write `cjk.bin` even for an English interface: Han characters in channel and contact names need it.

## Files

| File | What | Kept by |
|---|---|---|
| `languages/zh.json` | 中文 (Chinese) | va3bpf |
| `languages/es.json` | Español (Spanish) | looking for a maintainer |
| `languages/tr.json` | Türkçe (Turkish) | d0ukan |
| `languages/cjk.bin` | The Chinese font (GB2312, made from Noto Sans SC, SIL OFL 1.1, see `languages/OFL-NotoSansSC.txt`) | va3bpf |
| `docs/installation.es.md`, `docs/manual.es.md` | The installation guide and user manual in Spanish | looking for a maintainer |

Translated documents may lag behind; the English ones in OpenDMR ([installation](https://github.com/va3bpf/OpenDMR/blob/main/docs/installation.en.md),
[manual](https://github.com/va3bpf/OpenDMR/blob/main/docs/manual.en.md)) are the reference. The screenshots are in OpenDMR's `docs/manual/`.

## Adding a language

1. Copy OpenDMR's English text, [`tools/text/languages/en.json`](https://github.com/va3bpf/OpenDMR/blob/develop/tools/text/languages/en.json),
   and change `code`, `name`, `english_name` and the strings.
2. Check it with OpenDMR's `py tools/text/check_lang.py <file>` (format, placeholders, size: 16 KB a language) and
   fix what it lists.
3. Write it to the radio with the CPS and look at every screen: text that doesn't fit, letters drawn wrong.
4. Open a pull request here with the file in `languages/`, saying which screens you checked on the radio. Add your
   name as the language's maintainer if you like.

Letters: the firmware's own fonts have ASCII, Latin-1 and Latin Extended-A (U+0100–U+017F), so Western European,
Turkish, Polish, Czech, Romanian, Hungarian ... need only the `.json`, without `font`. Other scripts (Korean,
Japanese ...) need a font file, made with OpenDMR's `tools/fonts/mkfont_pack.py`; the format is in OpenDMR's
[docs/i18n.en.md](https://github.com/va3bpf/OpenDMR/blob/develop/docs/i18n.en.md).

Licence: the translations as OpenDMR's, the Chinese font under the SIL OFL 1.1; see [LICENSE](LICENSE).

When OpenDMR adds or changes interface text, `en.json` changes with it; `check_lang.py` lists what a translation is
missing.
