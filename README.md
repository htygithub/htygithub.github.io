# Web of CHENNYO

一个使用 MkDocs 和 Material 主题搭建的中文个人网站。

## 下次如何打开预览

1. 在 Windows 文件资源管理器中打开 `D:\cheonyo-web`。
2. 点击窗口顶部的地址栏，输入 `powershell`，按回车。
3. 在打开的窗口中粘贴下面这一行，再按回车：

```powershell
.\.venv\Scripts\python.exe -m mkdocs serve
```

4. 保持这个窗口打开，在浏览器地址栏输入 `http://127.0.0.1:8000/`。
5. 要停止预览，回到命令窗口，按 `Ctrl+C`。

如果提示端口已被占用，可以使用：

```powershell
.\.venv\Scripts\python.exe -m mkdocs serve -a 127.0.0.1:8001
```

然后访问 `http://127.0.0.1:8001/`。

## 修改内容

- 网站名称、主题、导航：`mkdocs.yml`
- 主页：`docs/index.md`
- 课程列表：`docs/course/index.md`
- 示例文章：`docs/course/example.md`
- 友链：`docs/friends/index.md`
- 关于：`docs/about/index.md`
- 页面样式：`docs/stylesheets/extra.css`

用文本编辑器打开对应文件，修改后保存即可。预览运行时，浏览器会自动刷新。
新增文章的方法写在示例课程文章末尾。

## 首次安装或重建工具环境

本机需安装 Python 3，然后在项目文件夹中依次运行：

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

## 生成静态网页

```powershell
.\.venv\Scripts\python.exe -m mkdocs build --strict
```

生成的网页位于 `site/` 文件夹。本地预览地址只供这台电脑使用。

## 发布到 GitHub Pages

- GitHub 仓库：https://github.com/htygithub/.github.io
- 网站地址：https://htygithub.github.io/.github.io/
- Pages 设置：https://github.com/htygithub/.github.io/settings/pages

每次将网站内容推送到 `main` 分支，GitHub Actions 都会自动安装工具、生成网页，并将网页发布到 `gh-pages` 分支。源文件保存在 `main`，生成的网页保存在 `gh-pages`。

首次推送后：

1. 打开 GitHub 仓库，点击顶部的 **Actions**，等待 **Publish website** 显示绿色对勾。
2. 点击仓库顶部的 **Settings**，再点击左侧的 **Pages**。
3. 在 **Build and deployment** 下，将 **Source** 设为 **Deploy from a branch**。
4. 将 **Branch** 设为 **gh-pages**，旁边的文件夹设为 **/ (root)**，点击 **Save**。
5. 等待发布完成，访问 Pages 页面显示的网站链接。

如果暂时看不到 `gh-pages`，请先等待 Actions 成功，再刷新设置页面。
通常需要几分钟，GitHub 提示发布可能需要最多约 10 分钟。

以后修改内容并保存后，在项目文件夹中依次运行：

```powershell
git add .
git commit -m "Update website content"
git push
```

`.venv/`、`site/` 和 `__pycache__/` 已被忽略，不会提交到源文件分支。
