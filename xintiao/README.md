# 薪跳

按实际工作时长估算实时薪资的手机优先网页工具。现有页面中的显示名称为“时薪”；本次归档不改动产品代码或线上界面。

## 功能

月薪、时薪或自定时段收入输入；累计收入和工作时长；开始、暂停、继续、结束；自动结束设置；刷新恢复；金额隐藏和本地结果卡下载。

计算口径：每秒薪资 = 月薪 ÷ 每月工作天数 ÷ 每天工作小时数 ÷ 3600。暂停期间不累计。

## 项目结构

```text
xintiao/
├── dist/
│   ├── index.html
│   ├── style.css
│   └── app.js
├── AGENTS.md
├── README.md
└── release-state.json
```

这是直接编写的 HTML/CSS/JavaScript；`dist/` 同时是可编辑的网站源码和可发布文件，不需要安装依赖或执行构建。

## 本地预览

在仓库根目录运行：

```sh
python3 -m http.server 8765 --directory xintiao/dist
```

打开 http://localhost:8765/ 。如已安装 Node.js，可用 `node --check xintiao/dist/app.js` 检查 JavaScript 语法。

## 保存与发布约定

用户要求：后续修改项目时完成必要验证，再同步到本仓库；等用户明确确认后才更新 Cloudflare。

- GitHub 保存源码版本，不代表该版本已经上线。
- 当前 Cloudflare Pages 项目：`shixin-time`；网址：https://shixin-time.pages.dev/ 。
- 现有发布方式是 Direct Upload，GitHub 本次归档没有连接或启用 Cloudflare 自动部署。
- 本次归档的三个网页文件与上一次部署时使用的本地文件完全一致；本次没有重新部署。
- 获得发布确认后，只上传 `xintiao/dist/` 中的网页文件。保留原 Cloudflare 项目和网址，除非用户另有要求。
- 将来如要配置 Git 自动部署，先向用户说明项目类型迁移、分支触发和费用限制，再取得同意。
- `release-state.json` 记录上次实际部署的文件指纹。仅同步 GitHub 时，不更新其中的已部署指纹；发布成功并验证后才更新。

## 数据

薪资和计时记录保存在各用户浏览器的 localStorage。本仓库不含用户实际工资记录、服务器数据库或接口密钥。

## 验证重点

修改后检查收入计算、开始/暂停/继续/结束、刷新恢复以及手机布局；涉及新功能时增加相关验证。无须为单纯源码归档重复全套浏览器测试。
