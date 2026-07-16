# 个人主页维护指南（写给叶耀文）

> 模板：[RayeRen/acad-homepage](https://github.com/RayeRen/acad-homepage.github.io)（Jekyll）
> 网址：https://yaowenye.github.io/

---

## 一、为什么一个静态网页有 178 个文件？

因为**你写的不是网页，是网页的原料**。

GitHub 收到你 push 的内容后，会在服务器上跑一个叫 **Jekyll** 的程序，它把你的 Markdown + 配置 + 样式**编译**成真正的 HTML，再发布出去。这跟你写论文的流程是同构的：

| 你写论文 | 这个网站 |
|---|---|
| `main.tex`（你的内容） | `_pages/about.md` |
| `\author{}` 等导言区 | `_config.yml` |
| `elsarticle.cls`（期刊模板） | `_sass/`（111 个文件） |
| 字体、宏包 | `assets/`（32 个文件） |
| `pdflatex` 编译 | GitHub 自动跑 Jekyll |
| 输出 `main.pdf` | 输出网站 |

**你不会去改 `.cls` 文件，同理也不要碰 `_sass/` 和 `assets/`。**

### 文件地图

| 路径 | 是什么 | 你要动吗 |
|---|---|---|
| **`_pages/about.md`** | **网站的全部内容**（单页站，全在这一个文件） | ✅ **90% 的时间只改这里** |
| **`_config.yml`** | 你的身份：姓名、头像、邮箱、ORCID、GitHub | ✅ 偶尔 |
| **`images/`** | 头像 + 论文配图 | ✅ 加图时 |
| `_data/navigation.yml` | 顶部导航栏 | ⚠️ 只在增删章节时 |
| `_includes/` | 页面零件（侧边栏、页头） | ❌ |
| `_layouts/` | 页面骨架 | ❌ |
| `_sass/` (111) | 排版引擎 | ❌ 永不 |
| `assets/` (32) | JS/CSS 资源 | ❌ 永不 |
| `google_scholar_crawler/` | 自动抓引用数 | ❌ |
| `Gemfile` `Gemfile.lock` | 依赖清单 | ❌ |

---

## 二、日常操作：三个高频场景

### 场景 1：加一条 News（最常用）

打开 `_pages/about.md`，找到 `# 🔥 News`，**在最上面加一行**（新的在前）：

```markdown
- *2026.08*: &nbsp;🎉 论文被 XXX 接收。
```

格式拆解：
- `*2026.08*` — 斜体日期
- `&nbsp;` — 一个空格（HTML 写法，不加的话 emoji 会贴着日期）
- 后面随便写

### 场景 2：加一篇带配图的论文

这是模板里最"吓人"的一块，其实只是**填空**。整块结构如下，改 5 个地方即可：

```html
<div class='paper-box'><div class='paper-box-image'><div><div class="badge">①期刊名 年份</div><img src='images/②图片文件名.jpg' alt="sym" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[③论文标题](④论文链接)

**Yaowen Ye**, 其他作者

[**Code**](链接) \| [**PDF**](链接)
- ⑤要点一
- ⑤要点二
</div>
</div>
```

| 填空 | 说明 |
|---|---|
| ① | 左上角小徽章，如 `bioRxiv 2026` |
| ② | 图片放进 `images/`，这里写文件名 |
| ③④ | 标题和链接 |
| ⑤ | 几条要点，用 `-` 开头 |

**三条铁律：**
1. `<div>` 和 `</div>` 必须**成对**。少一个，整页排版会崩。
2. `markdown="1"` **不能删**。它告诉 Jekyll「这个 HTML 块里面还要按 Markdown 解析」。删了之后你的 `**加粗**` 会原样显示成星号。
3. `<div class='paper-box-text' markdown="1">` 后面**必须空一行**，否则 Markdown 不生效。

不带图的论文更简单，直接一行 `- **标题** — 作者，*期刊*` 就行（见 Revisiting Senolytics 那条）。

### 场景 3：加一个章节

两步，**缺一不可**：

1. `_pages/about.md` 里加 `# 🎓 Awards`
2. `_data/navigation.yml` 里加：
   ```yaml
     - title: "Awards"
       url: "/#-awards"
   ```

**锚点怎么算？** 这是最容易踩的坑。规则：**emoji 去掉 → 剩下的转小写 → 空格变连字符**。因为 emoji 后面有个空格，所以**开头会多一个连字符**：

| 标题 | 锚点 |
|---|---|
| `# 🔥 News` | `#-news` |
| `# 💬 Talks and Conferences` | `#-talks-and-conferences` |

⚠️ **标题行末尾不要留空格**，否则锚点会变成 `#-news-`，导航就点不动了。（模板原本的 `# 📝 Publications ` 就带着这个空格，已修掉。）

---

## 三、图片怎么加

1. 图片放进 `images/`，命名用小写英文，别用中文和空格。
2. **先压缩再上传**：宽度 ≤ 1100px，控制在 300KB 以内。
3. 在 `about.md` 里引用：`<img src='images/你的文件名.jpg' width="100%">`

配图区在电脑上占 40% 宽（最大 400px）。**横图效果最好**；竖图会被拉得很高。

---

## 四、怎么发布

改完文件后：

```bash
git add .
git commit -m "update publications"
git push
```

推上去后**等 1–3 分钟**，GitHub 自动编译并更新 https://yaowenye.github.io/ 。

- 进度看这里：仓库页面 → **Actions** 标签。绿勾 = 成功，红叉 = 有错，点进去看日志。
- 页面没变？多半是浏览器缓存，`Ctrl + F5` 强刷。

### 本地预览（可选，但强烈推荐）

不想每次都靠 push 试错的话：

```bash
bundle install    # 只需第一次
./run_server.sh   # 然后浏览器打开 http://localhost:4000
```

改文件会自动刷新。**排版类改动建议先本地看一眼再 push。**

---

## 五、已经帮你修掉的 3 个线上问题

| 问题 | 原来 | 现在 |
|---|---|---|
| **学历写错** | "M.Ind. degree ... in 2022"（2022 是入学年，学位也不对） | M.Sc. in Bioinformatics, 2025 |
| **`repository` 格式错** | `"https://github.com/YaowenYe"`（完整 URL） | `"YaowenYe/YaowenYe.github.io"` — 这个字段是用来拼 CDN 地址的，填 URL 会导致引用数功能永远拉不到数据 |
| **Google Scholar 占位符** | `user=YOUR_GOOGLE_SCHOLAR_ID` | 已清空 —— 原样留着会在侧边栏渲染出一个**点不开的死链** |

### 想开启引用数显示？

如果你有 Google Scholar 主页：
1. `_config.yml` 里 `googlescholar` 填你的主页完整链接。
2. 编辑 `.github/workflows/google_scholar_crawler.yaml`，把里面的 Scholar ID 换成你的。
3. 仓库 Settings → Actions → 允许 workflow 写入权限。

没有 Scholar 主页就不用管，现在这样是干净的。

---

## 六、备用素材

`images/immunekg_concept.jpg` 是 immuneKG 的概念图（SOTA vs Biology-Driven 那张）。目前用的是四联主图 `immunekg.jpg`。想换的话，把 `about.md` 里的文件名一改即可——**概念图是横图，在配图区里其实比竖的四联图更清楚**，可以两个都试试看哪个顺眼。
