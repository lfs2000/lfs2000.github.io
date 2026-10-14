# HW 的博客

使用 Hexo 8 和 Fluid 主题，站点地址为 https://liufanshi.top。

## 本地开发

需要 Node.js 20.19.0 或更新版本。

```bash
npm ci
npm run server
```

打开 http://localhost:4000。站点配置在 `_config.yml`，Fluid 主题配置在 `_config.fluid.yml`，文章和相册在 `source/`。

```bash
npx hexo new "文章标题"
npm run clean
npm run build
```

文章应保留 front matter 中的 `date`，因为永久链接包含日期；缺失时 Hexo 会使用文件时间，重新检出可能改变链接。`public/` 是生成目录，不应直接编辑或提交。

## 部署

推送到 `main` 或手动运行 Deploy Hexo 工作流后，GitHub Actions 会按锁文件安装依赖，将生成结果发布到 `gh-pages` 分支。本地 `npm run deploy` 未配置部署插件，请使用工作流发布。

GitHub 仓库 Settings → Pages 应选择从 `gh-pages` 分支的根目录发布。自定义域名文件为 `source/CNAME`，内容必须与 `_config.yml` 中的 `url` 对应；DNS 和 HTTPS 需要在域名服务商及 GitHub Pages 中配置。

`_multiconfig.yml` 为忽略的本地文件，默认构建不会加载它，请修改上述正式配置文件。
