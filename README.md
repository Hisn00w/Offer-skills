# Offer-skills

`Offer-skills` 是一个面向中文求职简历的可复用技能包。它可以根据你的简历信息生成真正可编辑的 HTML 简历，也可以根据你上传的参考简历图片复刻版式，最后在浏览器中继续编辑并导出 PDF。

## 核心能力

- 根据姓名、求职方向、教育经历、实习/工作经历、项目、技能和照片生成 HTML 简历。
- 从 18 个编号模板中选择版式；模板包含单栏、双栏、侧栏、时间轴、卡片、顶部横幅、居中作品集、黑白学术和双页布局。
- 接收用户上传的简历截图或设计参考图，分析栏位、间距、字体层级、颜色和单双页结构，再生成可编辑 HTML。
- HTML 正文使用真实文本，不使用截图代替文字，不需要 Word，也不依赖服务器。
- 浏览器内支持文字编辑、照片替换、字体、文字颜色、加粗和导出 PDF。
- 内置秋招投递进度记录 HTML，可记录日期、公司、岗位、进度、下一步和备注，并支持筛选、统计、CSV/JSON 备份和 PDF 打印。

## 使用方式

### 方式一：选择技能包自带模板

把简历信息告诉 AI，并指定使用 `$Offer-skills`。AI 会根据内容密度和目标岗位选择合适的编号模板，填充后生成新的 HTML 文件。

示例：

> 请使用 `$Offer-skills`，根据我提供的教育经历、实习经历、项目经历和技能，制作一份后端开发岗位简历。优先选择 14 号双栏模板，输出 HTML，不要输出 Word。生成后我要在浏览器中编辑并导出 PDF。

### 方式二：上传图片复刻模板

上传一张简历截图或模板图片，并告诉 AI：

> 请复刻这张图片的简历版式，保留它的栏位、间距、字体层级、颜色和单双页结构，但最终输出必须是可编辑的 HTML 文本。

AI 会把图片作为视觉参考，而不是把图片直接放进简历正文。复刻后的文字、标题、时间、项目和技能仍然可以在浏览器中编辑。

### 方式三：记录秋招投递进度

使用 `Offer-skills` 的投递进度功能时，AI 会把 `assets/application-tracker.html` 放到桌面并告诉你保存路径。用浏览器打开即可使用。你可以把邮件、招聘网站或手机截图发给 AI，让 AI 按照截图中的信息整理为记录；也可以直接在浏览器中新增和编辑。

进度表支持：

- 日期、公司、岗位、进度、下一步和备注。
- 搜索、按进度筛选、投递总数/进行中/Offer/已拒绝/本月投递统计。
- 浏览器本地自动保存，不依赖服务器。
- 导出 CSV、备份/导入 JSON，以及打印或保存为 PDF。

![秋招投递进度 HTML 预览](assets/application-tracker-overview.svg)

### 方式四：让 AI 查询邮箱通知

告诉 AI 你使用的邮箱类型（例如 Gmail、Outlook、QQ 邮箱、163 邮箱或学校邮箱）以及要登录的邮箱地址。AI 可以使用浏览器查看招聘相关邮件，把新的投递、测评、筛选、面试、拒信或 Offer 更新到桌面的投递进度 HTML 中。

如果邮箱尚未登录，AI 会让你在浏览器中完成登录验证。完成后，告诉 AI“每天检查一次投递邮箱”，AI 可以创建每日定时任务；也可以指定每天的检查时间。定时检查有新进度时更新 HTML，没有变化时反馈“无新增进度”。


## 浏览器编辑与导出

打开生成的 `.html` 文件后：

1. 点击“编辑”，直接修改简历文字。
2. 选中文字后，可在工具栏中选择“字体”、设置“文字颜色”或点击“加粗”。
3. 点击“替换照片”，选择本地证件照。
4. 点击“导出 PDF”，在浏览器打印窗口中选择“另存为 PDF”。

工具栏位于简历上方，不会遮挡简历内容；打印或导出 PDF 时会自动隐藏。

## 18 个 HTML 模板缩略图

![Offer-skills 18 款 HTML 简历模板总览](assets/template-overview.jpg)

缩略图展示的是模板的实际 HTML/PDF 版式。标记为“双页”的模板会在 PDF 中产生明确的第一页和第二页。

| 编号 | 主要结构 | 页数 | 文件 |
|---:|---|---:|---|
| 01 | 经典蓝线单栏 | 一页 | `assets/templates-html/01-大厂极简简历模板.html` |
| 02 | 灰蓝标题带 | 一页 | `assets/templates-html/02-大厂极简简历模板.html` |
| 03 | 中英双语时间轴 | 一页 | `assets/templates-html/03-大厂极简简历模板.html` |
| 04 | 深色顶部横幅 | 一页 | `assets/templates-html/04-大厂极简简历模板.html` |
| 05 | 左侧信息栏 | 一页 | `assets/templates-html/05-大厂极简简历模板.html` |
| 06 | 黑白时间轴 | 双页 | `assets/templates-html/06-大厂极简简历模板.html` |
| 07 | 右侧蓝色边栏 | 一页 | `assets/templates-html/07-大厂极简简历模板.html` |
| 08 | 蓝色双栏 | 双页 | `assets/templates-html/08-大厂极简简历模板.html` |
| 09 | 黑白卡片 | 双页 | `assets/templates-html/09-大厂极简简历模板.html` |
| 10 | 蓝灰色标题条 | 一页 | `assets/templates-html/10-大厂极简简历模板.html` |
| 11 | 衬线字体分隔 | 一页 | `assets/templates-html/11-大厂极简简历模板.html` |
| 12 | 居中作品集 | 双页 | `assets/templates-html/12-大厂极简简历模板.html` |
| 13 | 黑白侧栏 | 一页 | `assets/templates-html/13-大厂极简简历模板.html` |
| 14 | 蓝线双栏 | 双页 | `assets/templates-html/14-大厂极简简历模板.html` |
| 15 | 现代蓝色标题带 | 一页 | `assets/templates-html/15-大厂极简简历模板.html` |
| 16 | 紧凑双栏 | 双页 | `assets/templates-html/16-大厂极简简历模板.html` |
| 17 | 学术黑白双页 | 双页 | `assets/templates-html/17-大厂极简简历模板.html` |
| 18 | 现代蓝色双页 | 双页 | `assets/templates-html/18-大厂极简简历模板.html` |

## 文件结构

```text
Offer-skills/
├── README.md
├── SKILL.md
├── agents/openai.yaml
├── references/
│   └── email-monitoring.md
└── assets/
    ├── fictional-resume-photo.png
    ├── resume-data-template.json
    ├── resume-template-editable.html
    ├── resume-template-two-page.html
    ├── application-tracker.html
    ├── application-tracker-overview.svg
    ├── template-overview.jpg
    └── templates-html/
        ├── 01-大厂极简简历模板.html
        ├── ...
        └── 18-大厂极简简历模板.html
```

所有编号模板都是 HTML 文件；正文、标题、时间、项目和技能为可编辑文本。模板只引用 `assets/fictional-resume-photo.png` 这一张虚构示例照片。

## 其他资源

- `assets/resume-data-template.json`：匿名简历信息数据结构。
- `assets/resume-template-editable.html`：紧凑的一页 HTML 示例。
- `assets/resume-template-two-page.html`：双页 HTML 示例。
- `assets/application-tracker.html`：空白秋招投递进度记录 HTML，可直接在浏览器中编辑和备份。
- `assets/application-tracker-overview.svg`：秋招投递进度 HTML 的虚构示例预览图。
- `assets/fictional-resume-photo.png`：虚构示例证件照。
- `assets/template-overview.jpg`：18 个模板的缩略图总览。
