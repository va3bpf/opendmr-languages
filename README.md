# OpenDMR 界面语言

[OpenDMR](https://github.com/va3bpf/OpenDMR)（Baofeng DM-32 / DM-32UV 的固件）的界面语言和字库文件。固件只自带英文，
其他语言都在这里，由各自的译者维护。English: [README.en.md](README.en.md)

## 使用

1. 下载本仓库（Code → Download ZIP）并解压。
2. 在 OpenDMR CPS 里连接电台，打开「界面语言」页，点「选择文件夹」，选解压出来的 `languages` 文件夹。
3. 勾选要的语言，点「写入电台」。中文连同字库约 2 分钟。
4. 在电台上「Options → Language」里选择。这一行在每种语言里都叫 Language。

即使用英文界面，也建议写入 `cjk.bin`：信道名、联系人名里的汉字要靠它显示。

## 文件

| 文件 | 内容 | 维护 |
|---|---|---|
| `languages/zh.json` | 中文 | va3bpf |
| `languages/es.json` | Español（西班牙文） | 欢迎接手 |
| `languages/tr.json` | Türkçe（土耳其文） | d0ukan |
| `languages/cjk.bin` | 中文字库（GB2312，由思源黑体 Noto Sans SC 生成，SIL OFL 1.1，见 `languages/OFL-NotoSansSC.txt`） | va3bpf |
| `docs/installation.es.md`、`docs/manual.es.md` | 西班牙文的安装指南和使用手册 | 欢迎接手 |

文档的译文可能落后于英文版，以 OpenDMR 里的英文版（[安装](https://github.com/va3bpf/OpenDMR/blob/main/docs/installation.en.md)、
[手册](https://github.com/va3bpf/OpenDMR/blob/main/docs/manual.en.md)）为准；截图在 OpenDMR 的 `docs/manual/` 里。

## 贡献一种语言

1. 从 OpenDMR 复制英文原文 [`tools/text/languages/en.json`](https://github.com/va3bpf/OpenDMR/blob/develop/tools/text/languages/en.json)，
   改 `code`、`name`、`english_name` 和各条文字。
2. 用 OpenDMR 的 `py tools/text/check_lang.py <文件>` 检查（格式、占位符、长度：一种语言最多 16 KB），改掉它报的问题。
3. 用 CPS 写进电台，每个界面都看一遍：文字有没有超出屏幕、字母显示是否正常。
4. 开 PR 到本仓库，文件放 `languages/`；PR 里写清楚在电台上看过哪些界面。你也可以留下名字，作为这种语言的维护人。

字母范围：固件自带的字体有 ASCII、Latin-1 和拉丁扩展 A（U+0100–U+017F），西欧、土耳其、波兰、捷克、罗马尼亚、匈牙利等
语言只要 `.json`，不写 `font`。其他文字（韩文、日文……）需要字库文件，用 OpenDMR 的 `tools/fonts/mkfont_pack.py` 生成，
格式见 OpenDMR 的 [docs/i18n.md](https://github.com/va3bpf/OpenDMR/blob/develop/docs/i18n.md)。

许可：译文和 OpenDMR 相同，中文字库按 SIL OFL 1.1，见 [LICENSE](LICENSE)。

OpenDMR 增加或修改界面文字时，`en.json` 会跟着变；`check_lang.py` 会列出译文里缺少的条目，欢迎补上。
