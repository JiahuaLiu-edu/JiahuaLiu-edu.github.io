# 个人网站日常更新与维护指南

这份指南用于网站框架搭建完成后的日常内容维护，包括修改个人信息、更新经历、新增或编辑 Plog、管理图片、本地预览和发布到 GitHub Pages。

日常维护通常不需要修改 `_layouts/`、`assets/css/` 或 JavaScript。需要更改布局、动画、搜索逻辑、深色模式或响应式设计时，再处理框架代码。

## 1. 项目在哪里

项目目录：

```text
/Users/liujiahua/.copilot/chats/a7c6ba6f-4a51-427a-bec9-33cc5a606a29/JiahuaLiu.edu.github.io
```

推荐使用 VS Code 打开整个目录，而不是只打开某一个文件。

主要内容文件：

| 位置 | 用途 | 日常是否常改 |
|---|---|---|
| `index.md` | “关于我”页面、个人简介和经历 | 经常 |
| `_plogs/` | 每篇学习 Plog 的正文和卡片信息 | 经常 |
| `hobbies.md` | “学习之外”页面内容 | 经常 |
| `images/` | 网站和 Plog 使用的图片 | 经常 |
| `_config.yml` | 网站标题、账号信息、顶部导航名称 | 偶尔 |
| `plogs.md` | Plog 列表、搜索和标签功能 | 一般不改 |
| `_layouts/` | 页面结构 | 不建议日常修改 |
| `assets/css/main.css` | 页面样式 | 不建议日常修改 |

## 2. 每次更新的标准流程

每次维护按下面的顺序操作：

1. 用 VS Code 打开项目目录。
2. 修改 Markdown 文件，必要时把新图片放入 `images/`。
3. 启动本地预览。
4. 在浏览器检查桌面端、手机端和深色模式。
5. 使用 Git 检查本次修改。
6. 提交并推送到 GitHub。
7. 等待 GitHub Pages 更新后检查线上网站。

## 3. 启动本地预览

在 VS Code 中选择“终端 -> 新建终端”。确认终端当前位于项目目录，然后运行：

```bash
bundle exec jekyll serve --host 127.0.0.1 --port 4001
```

看到类似以下内容代表启动成功：

```text
Server address: http://127.0.0.1:4001/
Server running... press ctrl-c to stop.
```

浏览器打开：

```text
http://127.0.0.1:4001/
```

常用页面：

```text
首页：http://127.0.0.1:4001/
Plog：http://127.0.0.1:4001/plogs/
学习之外：http://127.0.0.1:4001/hobbies/
```

Markdown、HTML 和 CSS 修改后，Jekyll 通常会自动重新生成。刷新浏览器即可看到结果。

停止预览服务：在运行服务的终端按 `Control + C`。

### 修改 `_config.yml` 后

`_config.yml` 的变化通常不会被自动读取。修改后需要：

1. 在终端按 `Control + C` 停止服务。
2. 再次运行启动命令。
3. 刷新浏览器。

### 提示端口已被占用

如果看到：

```text
Address already in use - bind(2) for 127.0.0.1:4001
```

说明已经有一个预览服务在运行。先直接打开 `http://127.0.0.1:4001/`，不要重复启动。

如果旧服务卡住，找到原来运行 Jekyll 的终端，按 `Control + C`，再重新启动。

## 4. 修改顶部三个模块名称

打开 `_config.yml`，找到：

```yaml
links:
  - title: About Me
    url: /
  - title: My Plogs
    url: /plogs/
  - title: Beyond Study
    url: /hobbies/
```

只修改 `title`，不要随意修改 `url`。例如：

```yaml
links:
  - title: 个人介绍
    url: /
  - title: 学习记录
    url: /plogs/
  - title: 生活随笔
    url: /hobbies/
```

修改完成后重启 Jekyll。

顶部导航名称和页面内部大标题是两套内容：

- 顶部导航名称：修改 `_config.yml` 中的 `links`。
- 首页大标题：修改 `index.md` 中的 `# 关于我`。
- Plog 页大标题：修改 `plogs.md` 中的标题文字。
- 学习之外大标题：修改 `hobbies.md` 中的标题文字。

## 5. 修改网站标题和个人账号

打开 `_config.yml`，找到：

```yaml
title: 华仔's 个人主页

owner:
  name: 刘家华 (James Liu)
  avatar: avatar.jpg
  email: JiahuaLiu_edu@foxmail.com
  github: JiahuaLiu-edu
  bilibili: "https://space.bilibili.com/219525656?spm_id_from=333.1007.0.0"
```

字段含义：

| 字段 | 用途 |
|---|---|
| `title` | 浏览器标签页和网站标题 |
| `name` | 作者姓名 |
| `avatar` | `images/` 目录中的头像文件名 |
| `email` | 邮箱入口 |
| `github` | GitHub 用户名 |
| `bilibili` | Bilibili 主页完整链接 |

YAML 对空格和缩进敏感：

- 使用空格缩进，不要使用 Tab。
- 保持同一级字段对齐。
- 含有特殊字符的值建议用英文双引号包住。
- 不要删除每行字段名后面的冒号。

修改 `_config.yml` 后必须重启本地服务。

## 6. 修改“关于我”页面

打开 `index.md`。文件开头的以下部分叫 Front Matter，不要删除：

```yaml
---
layout: page
---
```

### 修改个人简介

直接修改 `# 关于我` 后面的文字。常用 Markdown 语法：

```markdown
# 一级标题
## 二级标题
**粗体文字**
*斜体文字*
[南开大学计算机学院](https://cc.nankai.edu.cn)
```

### 修改首页照片

当前首页照片代码为：

```html
<img src="/images/sphoneshot_beam_bnw.png" class="floatpic">
```

替换图片时，可以保留文件名并覆盖 `images/sphoneshot_beam_bnw.png`，也可以放入一个新文件并修改路径：

```html
<img src="/images/new-profile-photo.jpg" class="floatpic">
```

### 修改一条经历

每条经历位于一个 `timeline-item` 中。日常只需要修改以下内容：

- Logo 图片路径和 `alt`。
- 职位名称 `timeline-role`。
- 单位名称 `timeline-company`。
- 时间 `timeline-time`。
- 介绍文字 `timeline-details`。

示例：

```html
<div class="timeline-item timeline-item--current">
  <div class="timeline-dot" style="background: #ffffff;">
    <img src="/images/logo/example.png" alt="组织名称">
  </div>
  <div class="timeline-card">
    <div class="timeline-header">
      <div class="timeline-role">职位名称 <span class="timeline-sep">|</span> <span class="timeline-company">组织名称</span></div>
      <span class="timeline-time">Sept. 2026 - Present</span>
    </div>
    <div class="timeline-details">
      在这里填写经历介绍。
    </div>
  </div>
</div>
```

`timeline-item--current` 表示当前经历。已经结束的经历可以只保留 `timeline-item`。

复制或删除经历时，要复制或删除完整的 `<div class="timeline-item"> ... </div>` 区块，避免破坏 HTML 标签配对。

## 7. 修改“学习之外”页面

打开 `hobbies.md`：

```yaml
---
layout: page
permalink: /hobbies/index.html
title: 学习之外
---
```

`---` 下方就是正文，可以使用普通 Markdown：

```markdown
## 学习之外

这里记录摄影、音乐、旅行和校园生活。

### 摄影

最近拍摄的一些照片。

![落日](/images/hobbies/sunset.jpg)
```

不要随意修改 `permalink`，否则顶部导航可能找不到页面。

## 8. 新增一篇 Plog

这是日常更新中最重要的操作。

### 第一步：准备封面图片

推荐在 `images/` 下新建 `plogs/` 子目录，集中存放 Plog 图片：

```text
images/
└── plogs/
    ├── pytorch-first-model.jpg
    ├── algorithm-week-01.png
    └── campus-autumn.jpg
```

建议：

- 文件名使用小写英文、数字和短横线。
- 不使用空格、中文括号或特殊符号。
- 照片优先使用 JPG；需要透明背景时使用 PNG。
- 封面尽量控制在 1 MB 左右，避免页面加载太慢。
- 不要误改 `images/nk-logo-reverse.png`，这是手动调整过的深色南开 Logo。

### 第二步：新建 Markdown 文件

在 `_plogs/` 目录新建文件，例如：

```text
_plogs/pytorch-first-model.md
```

文件名规则：

- 使用小写英文、数字和短横线。
- 不使用空格。
- 文件名尽量描述文章主题。
- 文件名会成为文章网址的一部分，发布后尽量不要再改。

### 第三步：粘贴 Plog 模板

```markdown
---
layout: plog
title: 第一次完成 PyTorch 图像分类实验
date: 2026-09-13
category: 计算机视觉
tags:
  - PyTorch
  - CV
  - 深度学习
cover: /images/plogs/pytorch-first-model.jpg
cover_alt: PyTorch 图像分类实验界面
cover_shape: wide
summary: 从数据准备到训练验证，第一次完整跑通一个小型图像分类实验。
---

最近完成了第一个 PyTorch 图像分类实验。

## 这次做了什么

在这里写学习过程、项目记录或阶段性复盘。

## 遇到的问题

- 问题一
- 问题二

## 阶段总结

在这里记录真正理解了什么，以及下一步准备做什么。
```

保存文件后，Plog 列表会自动：

- 生成新卡片。
- 生成站内详情页。
- 按日期排序。
- 将标题、摘要、分类和标签加入搜索范围。
- 将新标签加入标签筛选栏并自动去重。

不需要修改 `plogs.md`、搜索 JavaScript 或 CSS。

## 9. Plog 字段说明

| 字段 | 必填 | 作用 |
|---|---|---|
| `layout` | 是 | 固定写 `plog` |
| `title` | 是 | 卡片和详情页标题 |
| `date` | 是 | 发布日期和排序依据，格式为 `YYYY-MM-DD` |
| `category` | 建议 | 封面上的分类名称 |
| `tags` | 建议 | 搜索与标签筛选使用 |
| `cover` | 建议 | 封面图片路径 |
| `cover_alt` | 建议 | 图片无法显示及无障碍阅读时使用 |
| `cover_shape` | 否 | 卡片封面的形状 |
| `cover_fit` | 否 | 图片在封面区域内的缩放方式 |
| `summary` | 是 | 卡片摘要和详情页导语 |
| `external_url` | 否 | 知乎等完整技术文章的外部链接 |

### 封面形状

```yaml
cover_shape: wide
```

可使用当前网站已有的形状：

| 值 | 适合内容 |
|---|---|
| `wide` | 横向照片、风景、截图 |
| `square` | Logo、正方形插图 |
| `tall` | 人像、竖向照片 |

Logo 或需要完整展示的图片，增加：

```yaml
cover_fit: contain
```

普通照片一般不写 `cover_fit`，让图片自然铺满卡片。

### 标题包含冒号时

YAML 中的英文冒号可能被当成语法。稳妥写法是加引号：

```yaml
title: "学习复盘：第一次完成分类实验"
```

### 添加知乎或其他外部文章

在 Front Matter 中增加：

```yaml
external_url: https://zhuanlan.zhihu.com/p/123456789
```

Plog 详情页底部会自动出现“查看完整技术文章”入口。站内 Plog 内容仍然保留，卡片也仍然打开站内详情页。

没有外部文章时，删除这一行或不填写即可，不要写成无效的占位链接。

## 10. 编辑、暂存或删除 Plog

### 编辑

打开 `_plogs/` 中对应的 `.md` 文件，修改 Front Matter 或正文即可。

修改文件名会改变文章网址。只改文章标题时，修改 `title`，不要改文件名。

### 暂时不展示

最稳妥的方法是把文章文件临时移出 `_plogs/`，放到项目外的备份目录。只要文件还在 `_plogs/` 中，就会被 Jekyll 收录。

也可以在本地保存草稿，但不要把草稿文件放在 `_plogs/` 下并推送。

### 删除

删除 `_plogs/` 中对应的 Markdown 文件后，该卡片和详情页会在下次构建时消失。相关封面图片如果没有被其他页面使用，也可以随后删除。

删除前建议先运行：

```bash
rg "图片文件名" .
```

确认图片没有被其他文章引用。删除属于不可逆内容操作，最好先提交当前版本或保留备份。

## 11. 在正文中插入内容

### 图片

```markdown
![实验结果曲线](/images/plogs/training-curve.png)
```

### 链接

```markdown
[南开大学计算机学院](https://cc.nankai.edu.cn)
```

### 小标题

```markdown
## 实验过程

### 数据准备
```

### 列表

```markdown
- 第一项
- 第二项
- 第三项
```

### 引用

```markdown
> 能解释实验结果，比单纯跑出更高的准确率更重要。
```

### 行内代码和代码块

````markdown
使用 `model.eval()` 切换到验证模式。

```python
model.eval()
with torch.no_grad():
    output = model(images)
```
````

Markdown 段落之间留一个空行，否则可能被渲染成同一段。

## 12. 图片替换与管理

替换图片有两种方式。

### 保持原文件名覆盖

优点是不需要修改 Markdown 路径。覆盖后浏览器可能显示缓存，使用强制刷新：

- macOS Chrome：`Command + Shift + R`
- Windows Chrome：`Control + F5`

### 使用新文件名

把新图片放进 `images/`，再修改 Markdown 中的路径。此方式更容易判断线上是否更新，也能保留旧图片用于回退。

路径推荐以 `/images/` 开头：

```yaml
cover: /images/plogs/new-cover.jpg
```

注意文件扩展名和大小写必须完全一致。例如 `.JPG` 与 `.jpg` 在 GitHub Pages 上可能被视为不同文件。

## 13. 发布前检查

至少检查以下内容：

- 首页能正常打开。
- 三个顶部模块都能切换。
- 新 Plog 卡片存在，标题、日期和摘要正确。
- 点击卡片能进入站内详情页。
- 封面和正文图片正常显示。
- 搜索能够搜到新标题或摘要。
- 新标签出现在筛选栏，点击后结果正确。
- 外部文章链接打开的是正确网址。
- 浅色和深色模式都可读。
- 手机宽度下没有文字或图片溢出。
- 页面中没有草稿、占位文字、私人信息或无效链接。

执行一次完整构建检查：

```bash
bundle exec jekyll build
```

命令以 `done` 结束且没有红色错误，通常表示构建成功。RubyGems 的版本提醒属于现有环境警告，不等同于网站构建失败；重点看是否出现 `Error`、`Liquid Exception` 或退出失败。

## 14. 用 Git 检查并发布

### 查看发生了什么变化

```bash
git status
```

查看具体文字差异：

```bash
git diff
```

先确认列表里没有误删文件、临时截图或不准备发布的内容。

### 暂存本次修改

推荐明确指定文件，不要在没检查时直接暂存所有内容。例如新增一篇 Plog 和一张封面：

```bash
git add _plogs/pytorch-first-model.md images/plogs/pytorch-first-model.jpg
```

修改首页时：

```bash
git add index.md
```

再次检查：

```bash
git status
git diff --staged
```

### 创建提交

```bash
git commit -m "Add PyTorch learning plog"
```

提交说明应简短描述本次内容，例如：

```text
Update personal introduction
Add September algorithm plog
Replace CV experiment cover
Update hobbies page
```

### 推送到 GitHub

```bash
git push origin main
```

推送后 GitHub Pages 会自动重新构建。通常等待几十秒到几分钟，再检查线上网站。

网站仓库：

```text
https://github.com/JiahuaLiu-edu/JiahuaLiu-edu.github.io
```

## 15. 常见问题

### 修改了但页面没有变化

按顺序检查：

1. 文件是否已经保存。
2. 终端中的 Jekyll 是否仍在运行。
3. 终端是否显示重新生成完成。
4. 浏览器是否刷新。
5. 是否修改了 `_config.yml`；如果是，重启 Jekyll。
6. 是否查看了正确地址和正确页面。
7. 替换同名图片时，是否进行了强制刷新。

### 新 Plog 没有出现

检查：

- 文件是否放在 `_plogs/`。
- 文件扩展名是否为 `.md`。
- 文件顶部是否有成对的 `---`。
- `layout: plog` 是否正确。
- `date` 是否使用 `YYYY-MM-DD`。
- YAML 是否使用空格缩进。
- 终端是否出现 YAML 或 Liquid 错误。

### 图片不显示

检查：

- 图片是否确实位于 `images/`。
- 路径是否以 `/images/` 开头。
- 文件名、扩展名和大小写是否完全一致。
- 路径中是否误用了反斜杠 `\`；网页路径应使用 `/`。
- 图片文件是否损坏。

### 标签没有出现

正确写法：

```yaml
tags:
  - CV
  - 深度学习
  - 实验记录
```

不要漏掉每项前面的 `-`。同一个标签应保持完全一致，例如不要混用 `Pytorch`、`PyTorch` 和 `pytorch`，否则会被识别为三个标签。

### Jekyll 报 YAML 错误

常见原因：

- 标题里有冒号但没有加引号。
- 使用了 Tab 缩进。
- `tags` 下的列表缩进不一致。
- 漏掉 Front Matter 结尾的 `---`。
- 引号只有一边。

### 推送后线上网站没有更新

检查：

1. `git push` 是否成功。
2. GitHub 仓库中是否已经出现新文件。
3. GitHub 仓库的 Actions 或 Pages 页面是否正在构建。
4. 等待几分钟后强制刷新浏览器。
5. 本地 `bundle exec jekyll build` 是否成功。

## 16. 简单回退方法

修改尚未提交时，先用下面的命令查看差异：

```bash
git diff -- 文件路径
```

不要在不清楚影响范围时使用 `git reset --hard`、批量删除或覆盖整个项目目录。

如果错误已经提交并推送，最安全的处理通常是：

1. 根据 `git log --oneline` 找到有问题的提交。
2. 使用 `git revert 提交编号` 创建一个反向提交。
3. 再次推送。

执行回退前先确认目标提交，重要内容最好额外备份。

## 17. 哪些改动适合自己完成

可以直接按本指南完成：

- 修改个人介绍、研究方向和联系方式。
- 更新工作或校园经历。
- 修改顶部三个模块的名称。
- 新增、修改或删除 Plog。
- 修改 Plog 标题、摘要、分类、标签和正文。
- 更换封面、头像和正文图片。
- 添加知乎等外部技术文章链接。
- 更新“学习之外”内容。
- 本地预览、构建检查和发布。

涉及下列情况时，建议先备份并进行代码层面的检查：

- 改变页面布局或导航结构。
- 修改 `_layouts/` 中的 HTML/Liquid。
- 修改 `assets/css/main.css`。
- 修改搜索、标签筛选、深色模式或动画逻辑。
- 新增新的内容模块、评论系统、分页或数据统计。
- 更改网址结构、仓库名称、域名或 GitHub Pages 配置。

## 18. 最短操作清单

新增 Plog 时，只需记住：

```text
1. 图片放进 images/plogs/
2. 在 _plogs/ 新建英文文件名.md
3. 复制 Plog 模板并填写字段和正文
4. 启动 Jekyll，在 /plogs/ 检查卡片和详情页
5. 检查搜索、标签、深色模式和手机端
6. git status 和 git diff
7. git add 指定文件
8. git commit
9. git push origin main
10. 检查线上网站
```

日常内容更新的核心原则是：只改内容文件和图片，先在本地确认，再提交和推送；不需要为了新增一篇文章去修改网站框架。
