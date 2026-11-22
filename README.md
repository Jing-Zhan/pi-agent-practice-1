# pi-agent-practice-1

Pi Agent 课程作业（系统设计与分析）实验报告仓库。报告按实践课分目录存放，每份报告的截图放在对应目录的 `images/` 下，使用相对路径引用，可直接在 GitHub 网页查看。

| 实践课 | 内容 | 报告 |
|---|---|---|
| 实践课3 | Pi Agent 源码安装与编译（本地源码开发环境） | [practice-03/README.md](practice-03/README.md) |

## 实践课3 速览

目标：在小组组织仓库的基础上建立本地源码开发环境，完成依赖安装、本地编译、产物验证，并用源码入口完成一次真实会话。

| 项目 | 结果 |
|---|---|
| 小组组织仓库 | <https://github.com/Learning-Rate-LR/pi-hunnu-2026> |
| 实际 clone 地址 | <https://github.com/Learning-Rate-LR/pi-hunnu-2026.git> |
| 提交编号 | `1e0fe20497ede31346957636d1ee38a2e61f69d0`（`main`） |
| 环境 | Node.js v24.14.0、npm 11.9.0、Git 2.45.1.windows.1 |
| 依赖安装 | `npm install --ignore-scripts` → `added 333 packages`，退出码 `0` |
| 本地编译 | `npm run build` → 11 个包依次构建，`Built packages\coding-agent\dist\bundle (56 files, 8.3 MiB)`，退出码 `0` |
| 产物验证 | `Test-Path .\packages\coding-agent\dist\bundle\cli.js` = `True`；`--version` = `0.86.1` |
| 源码入口会话 | `.\pi-test.bat` 运行 `packages/coding-agent/src/cli.ts`，模型 `deepseek-flash` 已返回真实回复 |

四个问题的一句话回答：

- **源码在哪里**：`D:\大三上作业\系统设计与分析\pi-hunnu-2026`，来自小组组织仓库 `main` 分支的提交 `1e0fe20`。
- **依赖装在哪里**：仓库根目录的 `node_modules`（npm workspaces 统一提升，21 689 个文件、263 MB），不是全局安装。
- **构建执行了什么**：按根 `package.json` 的 `scripts.build` 依次进入 11 个子包执行各自构建，最后由 `scripts/build-coding-agent-bundle.mjs` 打包成 `dist/bundle/cli.js`。
- **正在运行哪个版本**：`0.86.1`，即仓库 `packages/coding-agent/package.json` 的版本；界面提示 `New version 1.6.0 is available`，说明运行的不是发布版而是本仓库源码。

## 目录结构

```text
pi-agent-practice-1/
└── practice-03/
    ├── README.md          # 实践课3 实验报告（正文）
    └── images/            # 12 张操作截图（S1–S6 与困难记录）
```

## 说明

- 报告中的命令、输出、退出码均为本机实际执行结果，截图为本机实际操作时截取。
- 报告与截图不含 API Key、`auth.json` 或授权回调地址。
- 首次 `npm run build` 曾因上游模型目录变化失败，定位与修复过程记录在报告的"遇到的困难与解决过程"一节。
