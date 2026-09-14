# 刘家华的个人主页

这是刘家华（James Liu）的个人网站，主要记录在南开大学计算机学院的学习经历、研究兴趣、项目实践与个人生活。

## 页面

| 页面 | 路径 | 内容 |
|---|---|---|
| 关于我 | `/` | 个人简介、研究方向与经历 |
| 学习 Plog | `/plogs/` | 图片与简短学习记录 |
| 生活之外 | `/hobbies/` | 兴趣与校园生活 |

## 技术栈

网站使用 Jekyll 4.2 构建，前端由 HTML、CSS 和原生 JavaScript 实现，并通过 GitHub Pages 发布。页面支持响应式布局、深色模式、时间线与滚动动画。

## 本地运行

```bash
bundle install
bundle exec jekyll serve --livereload
```

本地预览地址：`http://127.0.0.1:4000`。

## 主要文件

| 文件 | 用途 |
|---|---|
| `_config.yml` | 网站标题、作者信息和导航配置 |
| `index.md` | 首页内容 |
| `plogs.md` | 学习 Plog 卡片列表页 |
| `_plogs/` | 每篇 Plog 的 Markdown 内容 |
| `_layouts/plog.html` | Plog 详情页布局 |
| `hobbies.md` | 生活之外页面 |
| `_layouts/page.html` | 通用页面布局与页眉 |
| `assets/css/main.css` | 网站样式与深色模式 |

## License

网站代码遵循 [MIT License](LICENSE)。
