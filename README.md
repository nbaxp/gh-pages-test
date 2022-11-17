# github pages test

不需要手动创建 gh-pages 分支和配置项目,只需要添加 .github/workflows/gh-pages.yml 文件,push 到 main 分支时会自动构建并提交到 gh-pages 分支

```yaml
---
name: push to gh-pages
on:
  push:
    branches: [main]

jobs:
  All_ON_PUSH:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: "16.x"
      - run: npm install
      - run: npm run build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist

```
