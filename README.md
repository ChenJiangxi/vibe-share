<div align="center">

# vibe-share

### 把你刚做完的项目，自动写成小红书 / B 站 / 抖音的分享帖

一个 [Claude Code](https://claude.com/claude-code) 技能 · 给个人开发者 · 中文社媒发布包生成器

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-技能-blueviolet)](https://claude.com/claude-code)
[![For](https://img.shields.io/badge/发布到-小红书%20%7C%20B站%20%7C%20抖音-ff69b4)](#)

<br>

做完项目想发社媒，但卡在这里：<br>
标题怎么起？开场说什么？视频怎么剪？封面放哪句话？

<br>

**`/vibe-share` 自己读你的 README、git 提交记录、源码和设计稿**，产出一份可以直接拿去拍的发布包：

✓ 小红书 / B 站 / 抖音 **各 3 个标题候选**（文学钩子版 + 可检索关键词版 + 混合版）<br>
✓ 每平台**逐句配音稿**（时间码 · 画面 · 念白 · 语气）<br>
✓ **封面怎么构图** · 用作品哪一帧 · 字写什么放哪<br>
✓ **录视频要打什么字**（具体那 7 个字，不是"打一段"）<br>
✓ 灵感来自电影？**精确到秒**的引用方案 + 字幕标注 + 版权建议

<br>

> *创作者口吻，不是营销话术。但兼顾算法 —— 标题含可搜索关键词，冷启也有流量。*

<br>

[为什么](#为什么) · [产出什么](#产出什么) · [安装](#安装) · [怎么用](#怎么用) · [示范](#示范) · [和普通 AI 的差别](#和普通-ai-写的差别) · [设计理念](#设计理念)

</div>

---

## 为什么

做完一个小作品准备发社媒的时候，你需要：

- 一个不像 AI 写的**标题**
- 一个能抓人但不油腻的**开场**
- 录视频时**对着讲就行**的配音稿
- **每个平台**差异化的文案（不是一套贴三遍）
- 封面写什么、字放哪
- 录视频时**具体打哪句字**（不是"打一段字"这种抽象指令）
- 如果灵感有出处，**具体引用哪几秒**、版权怎么标

常规 AI 一张口都是 *"本项目旨在为用户提供……结合了……的优势"*。一眼 AI 味。

**vibe-share 是一套强制走创作分享的 prompt。** 内置写作红线硬性禁止：

- ✗ CTA：*"你会怎么做？""快来试试""欢迎留言"*
- ✗ 营销句式：*"让 xxx / 一键 xxx / 带你 xxx / 专为 xxx 打造"*
- ✗ 标题党模板：*【xxx】xxx🔥 / "绝了""震惊"*
- ✗ 扁平开场：*"最近做了个 xxx""大家好今天给大家分享"*
- ✗ 评论区小号自问自答
- ✗ **只引用不落地**：提到电影必须给出"几秒几帧"的具体插入方案
- ✗ **100 字不落地**：正文前 100 字必须说清"它是什么 + 给谁用 + 能做什么"，一个陌生读者读完要能复述
- ✗ **圈内词裸用**：第一次出现"Claude Code""skill""vibe coding""prompt"时必须带人话解释
- ✗ **标题单轨**：只给一个文学钩子标题 = 放弃冷启流量 = 新号零曝光。每平台必须给 3 候选

---

## 产出什么

跑完后会在你的项目根目录写出一份 `SHARE.md`，共 **9 个模块**。

### 1 · 标题三选 + 开场钩子

**标题** · 每平台 3 个候选，明确标注用途：

| 版本 | 用途 | 取舍 |
|---|---|---|
| 文学钩子版 | 给刷到你主页的人 / 好友转发 | 搜索流量 ≈ 0 |
| 关键词版 | 冷启、SEO（命中 `作品类型` `使用场景` `技术栈` `受众` 里至少 2 个）| 可能略平 |
| **混合版** · 默认推荐 | 前半文学钩子 + 后半落地关键词 | 兼顾抓眼和可搜 |

示例（项目：一扇下雨的网页窗，打字会被雾吃掉）：

- 文学钩子版：*深夜想给谁发一句"还记得吗"，打到一半删掉了*
- 关键词版：*用 Three.js 做了个打字雾气网页小工具｜情绪释放向*
- 混合版：*做了扇永远下雨的窗 — 打字会被雾一笔笔吃掉的网页小工具*

附带 **SEO 关键词池** 5–10 个，平铺进正文里提升搜索覆盖。

**开场钩子** · 3 个候选，都必须满足**画面 / 具体场景 / 未完成感**三选一。禁止"最近做了个 xxx""大家好今天给大家分享"这种扁平开头。

示例（Tears in Rain 案例，候选 A）：

> 深夜想给谁发一句"还记得吗"，打到一半删掉了。<br>
> 后来我把它打在了一扇下雨的窗上，看着雾把它盖掉。

### 2 · 演讲思路

不是逐字稿，是**大纲**——对着镜头聊就行，不用背。按顺序：开场钩子 → 一眼画面 → 灵感从哪来 → 想做什么 → 做的过程卡点 → 现场演示 1-2 个交互 → 收尾（**禁止 CTA**）。

### 3 · 完整配音稿

三个平台各一版。每一句带 **时间码 · 画面 · 念白 · 语气** 四列，可以直接照着念。

| 平台 | 时长 | 念白量 | 结构 |
|---|---|---|---|
| 抖音 | ≈ 25 秒 | 45 字 | 留白比话多 |
| 小红书 | ≈ 45 秒 | 100 字 | 画面 + 一点灵感 |
| B 站 | ≈ 4 分钟 | 段落长稿 | Cold Open → 自介 → 灵感 → 演示 → 卡点 → 致谢 → 收尾 |

### 4 · 电影 / 作品引用方案

如果你的灵感有具体出处（电影 / 画作 / 音乐），skill **不会只说"灵感来自 xxx"**。它会给你：

- **具体片段时间点**（例如 `01:29:00–01:31:00`）
- 建议**截取哪几秒**（通常 3–5 秒）
- **插在配音稿的哪一句之后**
- **画面处理**：慢放到 85% / 保留原声 / 静音叠自己旁白 / 滤镜
- **字幕标注**完整写法：`In the Mood for Love (2000) · dir. Wong Kar-wai`
- **平台差异**：B 站直接用 / 小红书改静态剧照 / 抖音换致敬滤镜

### 5 · 平台差异化文案

**不是**一套文案贴三遍。每平台按调性独立生成：

| 平台 | 调性 | 正文字数 | hashtag |
|---|---|---|---|
| 小红书 | 第一人称随笔，画面感优先 | 150–300 字 | 5–8 个，大词 + 垂类混搭 |
| B 站 | 完整叙事，允许技术深度 | 150–250 字 | 逗号分隔，≤10 个 |
| 抖音 | 极短 + 画面主导 | ≤50 字 | 3–5 个真实相关 |

### 6 · 封面设计

三个平台各自给**完整构图**，不是"建议用醒目画面"这种废话。每张封面都明确：

- **用作品里哪一帧当底**（"字刚写完" vs "雾吃到一半" vs "台词浮现" 传达完全不同情绪）
- **玻璃 / 画面上写什么字**（具体那 3–7 字、字放在画面的哪个位置）
- **文字叠加层**：标题 / 副标 / 署名的字号 / 颜色 / 位置
- **色调**：主色 + 点缀色
- **各平台差异**：小红书 3:4 / B 站 16:9 / 抖音 9:16 首帧——抖音的字必须在上 1/3，因为底部信息栏会挡

### 7 · 拍摄前设置

让你**打开浏览器就能照做**的操作清单：

- 浏览器全屏的具体步骤（Mac: `Ctrl+Cmd+F` → `View → Always Show Toolbar` 关掉）
- 分辨率 / 帧率推荐（至少 1080p 60fps，快运动场景 30fps 会糊）
- 录屏软件（Mac: OBS / ScreenFlow；Windows: OBS / ShareX）
- 音频方案（Mac 录网页音装 BlackHole）
- **作品内参数的具体建议值**。例如 Tears in Rain：雨量 70% / 玻璃模糊 60% / 雾气亮度 75% / 折射 50%
- 背景图 / 素材选择建议（具体到"用哪张剧照"）

### 8 · Demo 录制清单

每一镜都写成**可执行卡片**，不是"打一段字演示一下"。示例：

> **镜头 C · 雾气回填（核心镜头）**（15 秒 × 3 take）
> - 画面：全屏，字在画面中间偏上
> - 输入：`如果多一张船票`（7 字，呼应台词库）
> - 卖点：per-pixel fog reclaim
> - 备注：**从打完到字消失任何一帧都不能剪**

每一镜都标出：画面 / 具体打什么字 / 时长 / 录几 take / 体现什么卖点 / 不能剪的关键帧。

### 9 · 剪辑节奏

分平台的**秒数级时间轴**。例如抖音 25 秒版本：

```
0–2s     首帧钩子 + 念白开场
2–4s     手动触发消散（镜头 E）
4–14s    核心：完整雾气回填（镜头 C，不剪）
14–18s   台词浮现（镜头 D）
18–22s   换背景（镜头 G）
22–25s   片尾 + 作品名
```

小红书 30–60 秒、B 站 3–5 分钟各自也有完整时间轴。照着剪即可。

---

## 安装

### Claude Code

```bash
# 全局安装（所有项目都能用）
git clone https://github.com/chenjiangxi/vibe-share /tmp/vibe-share-src
mkdir -p ~/.claude/skills
cp -r /tmp/vibe-share-src/skills/vibe-share ~/.claude/skills/
rm -rf /tmp/vibe-share-src
```

或用 Plugin 一键装：

```
/plugin install https://github.com/chenjiangxi/vibe-share
```

零依赖。没有 Python，没有 MCP，没有 requirements.txt。<br>
**一个 SKILL.md 而已。**

---

## 怎么用

```
你   ❯  cd ~/my-cool-project
你   ❯  /vibe-share

AI   ❯  看了一下。这是一个叫 {项目名} 的作品——
        {扒 README 后的一句话描述}
        灵感好像来自 {从 idea.md 里扒到的}。

        两个问题要你拍板：
        1. 受众更偏文艺青年还是独立开发者？
        2. 这次最想讲灵感故事、还是技术做法？

你   ❯  文艺青年 · 灵感故事

AI   ❯  SHARE.md 已生成在项目根目录，包含：

        · 3 个开场钩子候选
        · 三平台完整配音稿（抖音 25s / 小红书 45s / B 站 4min）
        · 电影引用方案，精确到秒
        · 每个镜头打什么字
        · 三平台封面构图

        改成自己的口吻再发。
```

---

## 示范

[examples/tears-in-rain/SHARE.md](./examples/tears-in-rain/SHARE.md) 是跑在一个真实作品上的完整产出。

> **Tears in Rain** —— 一扇永远下雨的起雾窗户，打字会被雾气悄悄盖掉，然后浮现一句旧电影的台词。

它**扒了什么** / 对应**产出了什么**：

| 扒到的 | 变成了 |
|---|---|
| `README.md` 的「创作理念」 | 开场钩子："深夜想给谁发一句'还记得吗'，打到一半删掉了。" |
| `idea1.md` 里提到王家卫 | 《花样年华》`01:29:00` 封洞那 4 秒的引用方案 + 字幕标注写法 |
| `git log` 里 `per-pixel fog reclaim for organic dissolve` | B 站 4 分钟主片里「创作卡点」那 2 分钟的完整叙述 |
| `quotes.js` 里的电影台词库 | 镜头 C 建议打「如果多一张船票」（呼应台词库内部） |
| `picture/` 目录下的备选图 | 拍摄前设置里的背景图推荐 |

---

## 和普通 AI 写的差别

|  | 常规 AI 生成 | **vibe-share 生成** |
|--|------------|--------------------|
| 标题 | 【震惊】我做了个神器🔥 | 3 候选：文学钩子 / 关键词 / 混合版，兼顾抓眼和可搜 |
| 开场 | 大家好今天给大家分享一个项目 | 想象一扇永远在下雨的起雾玻璃。 |
| 100 字内 | 一堆"本项目旨在"还没说清是啥 | 前 100 字强制落地"是什么 + 给谁用 + 能干嘛" |
| 圈内词 | 直接甩 skill / prompt / MCP | 第一次出现必带人话解释 |
| 灵感 | "灵感来自《花样年华》" | 《花样年华》01:29:00，截封洞那 4 秒 + 慢放 85% |
| 演示 | "打一段字演示一下" | 镜头 C 打「如果多一张船票」（7 字，呼应台词库） |
| 文案 | 三平台一套复制 | 三平台各自调性、各自长度 |
| 封面 | "用醒目画面吸引点击" | 3:4 竖版 · 字写「还记得吗」· 雾吃到 60% · 左上叠副标 |
| 调性 | 卖货 | 分享（但不放弃搜索流量） |

---

## 设计理念

### 为什么是"创作分享"，不是"产品发布"

产品发布是为了转化。它需要 CTA、需要 hashtag 矩阵、需要痛点场景、需要"立刻点击"。

vibe coding 做出来的东西大多不是产品——是作品。作品被分享出去是因为做的人想让人看见，不是因为要 KPI。

强行套用产品发布的话术写作品介绍，只会让作品看起来像 AI 做的。

### 为什么要扒 git log

`git log` 是金矿。commit message 经常暴露创作过程里的卡点和顿悟——比如 `per-pixel fog reclaim for organic dissolve` 就是一个完整的故事。这种细节在 README 里看不到，但它是作品最能打动人的地方。

### 为什么拒绝"一键全自动"

skill 跑起来时，如果项目信息不够清楚，最多问你 1–2 个问题。这是刻意的——让作者 commit 一次判断，产出才不会全是空壳。

不问用户、什么都推断的"一键全自动"最容易变成废话生成器。

### 为什么一个 SKILL.md 够了

vibe-share 的本体只是一份 `SKILL.md`，不需要任何依赖。

因为真正起作用的不是代码——是**清晰的边界**。什么不能写比什么能写更重要。

---

## 路线图

- [x] 核心 SKILL.md — 自扒项目、生成发布包
- [x] 示范案例 — `examples/tears-in-rain/`
- [ ] 更多领域的 examples（插画、音乐、写作、硬件）
- [ ] 海外版本（Reddit / Hacker News / Product Hunt）
- [ ] 子变体：写作类 / 视觉类 / 音乐类 / 硬件类 各自调优
- [ ] 内置"再改一遍" workflow（基于反馈迭代同一份 SHARE.md）

---

## FAQ

**Q：会不会写出来还是像 AI？**<br>
A：写作红线禁止了所有 AI 套话。产出的调子是"作者在随手讲"。但你还是要拿去**改成自己的口吻**——这是草稿，不是成稿。

**Q：只能生成中文吗？**<br>
A：是。目标是小红书 / B 站 / 抖音。英文平台（Reddit / Hacker News / Product Hunt）需要 fork 一份。欢迎 PR。

**Q：它帮我录视频吗？**<br>
A：不。它给你完整的拍摄前设置、镜头清单、配音稿和剪辑时间轴。录的事你来。

**Q：要不要原封不动发？**<br>
A：不要。生成的是脚手架，必须改成自己的口吻。特别是开场钩子，按**你自己真实的那个瞬间**重写。

**Q：它会联网吗？**<br>
A：不会。只读你本地的项目文件。

---

## 贡献

- 发 issue 聊想法
- 发 PR 改进 `SKILL.md` 或补 examples
- 用它发了自己的作品，欢迎告诉我链接

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=chenjiangxi/vibe-share&type=Date)](https://star-history.com/#chenjiangxi/vibe-share&Date)

---

<div align="center">

MIT License © [chenjiangxi](https://github.com/chenjiangxi)

*"做完了，分享一下。"*

</div>

---

## English (short)

**vibe-share** is a [Claude Code](https://claude.com/claude-code) skill that turns a just-finished vibe coding project into a publishing kit for Chinese social platforms (Xiaohongshu 小红书 / Bilibili B站 / Douyin 抖音).

Run `/vibe-share` in any project directory. Claude auto-reads README, git log, source code and design docs, then writes `SHARE.md` containing opening hooks, full voiceover scripts with timecodes, film/artwork citation plans with exact timestamps, platform-specific captions, cover designs, a detailed shot list (what to type in each take), and editing timelines.

**Creator-sharing, not product-marketing.** Hard constraints against CTAs, clickbait templates, and AI-slop phrasing. Output is in Chinese.

Install:

```
/plugin install https://github.com/chenjiangxi/vibe-share
```

MIT License.
