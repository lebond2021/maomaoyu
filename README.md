# 毛毛雨（maomaoyu）应用数据仓库

本仓库为「毛毛雨」TVBox 极简版客户端的官方数据源，App 只读访问，匿名可用。

## 目录结构

- `catalog.json` —— 接口源清单（App 定期拉取，`version` 变大即触发配置同步）
- `sources/<id>.json` —— 9 条内置接口源配置（已把 jar / lib 改写成绝对地址）
- `jars/` —— 片源 spider jar（随仓库分发，App 首启从仓库下载后本地缓存）
- `lib/` —— 片源依赖的 js / json

## App 读取地址

- 清单：https://raw.githubusercontent.com/lebond2021/maomaoyu/master/catalog.json
- 配置：https://raw.githubusercontent.com/lebond2021/maomaoyu/master/sources/<id>.json
- jar：https://raw.githubusercontent.com/lebond2021/maomaoyu/master/jars/<name>
- 版本：`dist` 分支 https://gitee.com/lebond/maomaoyu/raw/dist/version.json

## 接口源列表

| id | 名称 | 优先级 |
|---|---|---|
| qist_jsm | TVBox jsm | 100 |
| qist_0825 | TVBox 0825 | 95 |
| dongli | 动力 TV | 88 |
| qist_0821 | TVBox 0821 | 85 |
| qist_9918 | TVBox 9918 | 80 |
| qist_0826 | TVBox 0826 | 75 |
| qist_fty | 饭太硬 fty | 70 |
| qist_0827 | TVBox 0827 | 60 |
| gao_js | 高天流云 js | 20 |

## 更新方式

本仓库由本地脚本 `gitee-sync/sync-sources.ps1` 每周自动刷新：抓上游 → 改写地址 → 下载 jar/lib → 提高 `version` → 提交。APK 由 `publish-apk.ps1` 发布到 `dist` 分支。