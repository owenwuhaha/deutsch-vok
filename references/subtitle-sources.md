# 德语字幕来源备选

按剧种/来源选路线，不必逐站走完。站点覆盖和版权政策会变化，每次都要核对剧名、年份、季数、集数和**德语原文字幕**内容；只保存精选例句用于个人学习。本技能只提取德语词条，绝不用翻译字幕反推德语词汇。

## 德语剧集 / 电影（德语原声 + 德语字幕）

1. **ARD Mediathek**：<https://www.ardmediathek.de/>。德国公共电视台点播库，含大量德剧、电影和纪录片；很多提供德语 Untertitel。优先用德文片名搜索目标剧集与集数。
2. **ZDF / ZDFmediathek**：<https://www.zdf.de/>。含德剧、电影、杂志类节目；部分带德语字幕或可开启 Untertitel。
3. **Netflix 德语剧**：如 *Dark*、*Babylon Berlin*、*How to Sell Drugs Online (Fast)*、*Dogs of Berlin*、*Biohackers* 等。若用户提供 Netflix 页面或本地德语字幕文件，优先使用用户可访问的德语原字幕；登录、地区限制或 DRM 导致无法读取时，不能假装已拿到台词，请用户贴字幕文本或上传 `.srt/.vtt/.ass/.smi`。
4. **德语电影 / 频道**：如 *Das Boot*、*Generation War*、*Tatort*（长青刑侦剧，单集独立）等。用德文片名 + `SRT` / `Untertitel` 搜索。

## 德语播客 / 新闻 / 教学（适合日常与考试词汇）

1. **Deutsche Welle（DW）**：<https://www.dw.com/de/deutsch-lernen/>。提供分级德语学习材料与转录文本，适合 A1–B1 词汇。
2. **Tagesschau / Tagesthemen**：<https://www.tagesschau.de/>。新闻文稿为规范书面/口语德语，适合 B1–C1 与 TestDaF/DSH 听力词汇。
3. **Slow German**：<https://slowgerman.com/>。慢速德语播客，附文稿，适合 A2–B1。
4. **Logo / Funk**：青少年向德语内容，口语化强，适合 A2–B1 日常表达。

## 字幕数据库（兜底）

1. **OpenSubtitles**：<https://www.opensubtitles.org/>。把字幕语言设为 German/Deutsch，再按德文剧名、年份、season/episode 过滤；多版本时以集数、分辨率/发行组和字幕行数判断是否对应目标视频。
2. **Untertitel.net / Untertitel.de**：德语字幕社区，可用德文片名搜索电影/剧集德语 SRT。
3. **Subscene / YIFYsubs**：搜索时务必选择 **German** 语言标签，不要选 “German (English)” 之类的翻译字幕。

## 通用处理

- 已知站点的单集正文可以通过 `https://r.jina.ai/` 预处理，但先确认原页面真的含连续德语对白；代理返回导航页、验证页或错误页时立即放弃该候选。
- 用户提供字幕文件时直接解析，不再联网。支持 `.srt`、`.vtt`、`.ass`、`.ssa`、`.smi` 和纯文本台词；先去时间码、标签和重复行，再保留德语对白。
- 德语特殊字符（ä ö ü ß）必须保持原样，不做 ASCII 化；可分动词在原句中往往拆开，提取时按原句实际词形填 `targets`（如 `aufgeben` → `["Gib","auf"]`）。

## 成功判断与止损

成功必须同时满足：

1. 页面或文件身份匹配剧名、年份、季数和集数；
2. 内容是德语连续对白，或字幕文件包含时间码和德语对白行；
3. 能从中抽出多条不重复的完整德语原句。

HTTP 200、页面字数多、搜索摘要或剧情简介都不算成功。请求使用 `--connect-timeout 8 --max-time 20 -fL`；每个站点最多换一次搜索词，最多尝试三类来源。所有下载和引用都遵守站点条款与版权边界，不下载整集视频，不绕过登录、付费或地区访问控制。
