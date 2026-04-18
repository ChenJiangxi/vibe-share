# vibe-share

> 把刚做完的 vibe coding 项目，转成一份能直接发小红书 / B 站 / 抖音的发布包。  
> 不是营销话术，是**创作者分享**。

这是一个 [Claude Code](https://claude.com/claude-code) skill。安装后，在你刚做完的项目目录里说一句「帮我准备发布内容」或输入 `/vibe-share`，Claude 会自扒你的项目（README、git log、源码、设计文档），然后在项目根目录写出一份完整的 `SHARE.md`。

---

## 它给你什么

- **三个候选开场钩子** —— 有画面、有具体场景、有未完成感。不是"大家好今天给大家分享"
- **演讲思路** —— 录视频时对着讲就行的大纲
- **完整视频配音稿** —— 抖音 / 小红书 / B 站 三个版本，逐句带**时间码 / 画面 / 念白 / 语气提示**
- **电影 / 作品引用方案** —— 如果你的灵感有具体出处（比如某部电影的某一场戏），给你具体到**哪几秒可以剪进去、插在哪句配音之后、版权怎么处理、字幕怎么标**
- **平台差异化文案** —— 小红书 / B 站 / 抖音 各自定制的标题、正文、hashtag，不是一套文案贴三遍
- **封面设计** —— 三个平台各自的完整构图：用哪一帧当底、字写什么、字叠加在哪个位置、色调怎么搭
- **拍摄前设置** —— 浏览器配置 / 分辨率帧率 / 录屏软件推荐 / 作品内参数建议值（例如滑块调到多少最上镜）
- **Demo 录制清单** —— 每一镜具体**录什么画面、打什么字、录几秒、录几 take**，不是"打一段字"这种抽象指令
- **剪辑节奏** —— 分平台的秒数级时间轴，照着时间码剪即可

---

## 为什么做这个

做 vibe coding 项目最让人犯难的不是写代码，是做完之后要发社媒——要想标题、想开场、想演讲思路、想每个平台的差异、想封面写什么、想录视频时打什么字。常用的 AI 工具一张口全是营销八股，生成出来的东西一眼就知道是 AI 写的。

这个 skill 强制自己走**创作者分享**的路子，不是**产品推广**的路子。内置的写作红线包括：

- 禁止 CTA（"你会怎么做？""快来试试""欢迎留言"）
- 禁止营销句式（"让 xxx"、"一键 xxx"、"带你 xxx"）
- 禁止标题党模板（【】xxx🔥、"绝了""震惊"）
- 禁止扁平开场（"最近做了个 xxx"、"大家好今天给大家分享"）
- 禁止评论区预置（不让你用小号自问自答）
- 禁止**引用而不落地**：提到电影 / 画作时必须给出具体可插入的镜头方案，不是只甩名字

---

## 装一下

### 方式 A · 手动安装（最稳）

```bash
git clone https://github.com/chenjiangxi/vibe-share.git
mkdir -p ~/.claude/skills
cp -r vibe-share/skills/vibe-share ~/.claude/skills/
```

然后重启 Claude Code 即可。

### 方式 B · 作为 Plugin 安装

在 Claude Code 里：

```
/plugin install https://github.com/chenjiangxi/vibe-share
```

---

## 怎么用

1. `cd` 到你刚做完的项目目录
2. 打开 Claude Code
3. 直接说「帮我准备发布内容」，或输入 `/vibe-share`

Claude 会并行读你的 `README.md` / `idea.md` / `plan.md` / `BRIEF.md` / `git log` / 主入口源码 / `picture/` 等截图目录，去理解项目在做什么、灵感哪里来、有什么可交互的功能。需要时最多问你 1–2 个关键问题（比如"最想讲灵感故事还是技术故事"），然后在项目根目录输出 `SHARE.md`。

---

## 示范输出

看一眼 [examples/tears-in-rain/SHARE.md](./examples/tears-in-rain/SHARE.md) 就知道产出长什么样。这是用 `vibe-share` 跑在一个真实的小作品上的结果：

**原项目**：[Tears in Rain](https://github.com/chenjiangxi/tears-in-rain) —— 一扇永远下雨的起雾窗户，打字会被雾气悄悄盖掉，然后浮现一句旧电影的台词。

**产出的 `SHARE.md` 里有**：

- 开场钩子候选 A："深夜想给谁发一句'还记得吗'，打到一半删掉了。后来我把它打在了一扇下雨的窗上，看着雾把它盖掉。"
- B 站 4 分钟配音稿，分 7 段：Cold Open / 自介 / 灵感故事 / 功能演示 / 创作卡点 / 技术致谢 / 收尾
- 《花样年华》吴哥窟片段精确到 `01:29:00–01:31:00`，截封洞那 4 秒 + 慢放 85%，保留 Yumeji's Theme 配乐，字幕叠 `In the Mood for Love (2000) · dir. Wong Kar-wai`
- 《银翼杀手》Roy Batty 独白精确到 `01:49:00–01:50:30`，截白鸽飞起的 3 秒
- 每个镜头具体打哪句字：镜头 C 打「如果多一张船票」（7 字，呼应台词库），镜头 E 打「还记得吗」，镜头 F 打「雨」配合调滑块
- 三平台封面构图：小红书 3:4 雾吃 60%、B 站 16:9 左右分栏、抖音 9:16 首帧字必须在上 1/3（底部信息栏会挡）

---

## 适用场景

- ✓ 刚做完一个有点意思的个人项目 / vibe coding 作品，准备发社媒
- ✓ 作品本身是视觉 / 交互 / 概念向，适合短视频展示
- ✓ 你想要**创作分享**的调子，不是**产品推广**的调子

不太适合的场景：

- ✗ 正式产品发布（可能需要更偏商业的 landing page 和 copywriting）
- ✗ 面向海外英文平台（这个 skill 的产出是中文，面向小红书 / B 站 / 抖音）
- ✗ 纯后端 / 工程类项目，没什么能演示的画面

---

## 贡献

发 issue 或 PR。如果你用它发了自己的作品，欢迎告诉我链接。

如果你想把这个 skill 适配到其他方向（比如英文平台版、技术教程版、商业产品版），欢迎 fork 一份改。

---

## License

MIT. 见 [LICENSE](./LICENSE).

---

## English (short)

**vibe-share** is a [Claude Code](https://claude.com/claude-code) skill that turns your just-finished vibe coding project into a publishing kit for Chinese social platforms (Xiaohongshu 小红书 / Bilibili B站 / Douyin 抖音).

Install, then run `/vibe-share` (or just ask Claude to "prepare publishing content") in any project directory. Claude auto-reads the project (README, git log, source, design docs) and writes `SHARE.md` containing:

- Three candidate opening hooks (画面 + 具体场景, not marketing slogans)
- A narrative speaking outline
- Complete voiceover scripts with timecodes for Douyin (~25s), Xiaohongshu (~45s), and Bilibili (~4min)
- Film/artwork citation plans with exact timestamps and fair-use guidance
- Platform-specific titles, captions and hashtags
- Cover designs per platform (composition + what text to write on-screen)
- Pre-recording setup (browser, resolution, screen recorder, in-app parameter values)
- A detailed shot list (each shot specifies what to type, duration, takes)
- Editing timelines per platform

Core principle: **creator-sharing**, not product-marketing. No CTAs, no clickbait, no AI-slop phrasing. Output is in Chinese.

Install:

```
/plugin install https://github.com/chenjiangxi/vibe-share
```

Or clone and copy `skills/vibe-share/` into `~/.claude/skills/`.

MIT License.
