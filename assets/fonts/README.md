# 本地字体

页面通过 `assets/fonts/fonts.css` 加载本地 Inter、Noto Sans SC 与 Noto Serif SC，无 Google Fonts CSS、preconnect 或远程字体依赖；HTML 与共享样式的字体族、字重及衬线引用保持原样。

## 固定来源

| 包 | 精确版本 | 来源与许可 |
| --- | --- | --- |
| `@fontsource-variable/inter` | `5.3.0` | 原字节复用 workbench 已固定字体；[来源](fusion/sources.json)、[许可](fusion/inter/LICENSE) |
| `@fontsource-variable/noto-sans-sc` | `5.3.0` | 同上；[许可](fusion/noto-sans-sc/LICENSE) |
| `@fontsource-variable/noto-serif-sc` | `5.3.1` | [npm 固定版本元数据](https://registry.npmjs.org/@fontsource-variable%2Fnoto-serif-sc/5.3.1)、[保留的元数据](serif-sources/npm-metadata-5.3.1.json)、[许可](noto-serif-sc/LICENSE) |

[package-lock.json](package-lock.json) 使用 npm 原生 `resolved`、`integrity` 固定三个公开字体包，不是页面运行或安装步骤。Serif 下载 tarball 的 SHA512 已与版本元数据中的 npm integrity 一致；Inter 与 Sans 复用已按原锁验证的工作台字体。精确取得过程见 [sources.json](sources.json)。不安装系统字体，不修改工作台原字体资产。

三个字体目录保留原 `index.css`、`package.json`、元数据、完整许可证及原 CSS 引用的所有 normal 字体分片，无按设计页文字裁剪。`fonts.css` 保留上游全部 209 个 face、unicode-range、font-display 和可变字重，仅把 Variable 字体族名称映射到设计页既有名称，并改成本地相对 URL。Inter/Sans 为 100–900，Serif 为 200–900，覆盖设计原用 400/500/600 字重。上游未覆盖字符仍使用原有系统 fallback；不承诺全 Unicode 覆盖。

`fusion/SOURCES.md` 为供体历史来源说明的原字节副本，其中应用路径属于供体；本设计稿的入口是本目录 `fonts.css`。没有另建逐文件 hash 注册表。变更字体时更新标准锁、保留许可证，并检查 CSS 引用及离线浏览器加载。
