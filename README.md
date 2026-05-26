# Dividend ETF Planner / 红利ETF定投计划工具

一个纯静态、无后端、可本地打开的红利ETF定投计划工具。当前默认以 **512890 红利低波ETF** 为示例，支持输入年度总投入 X、当前价格、阶段高点、持仓成本，自动生成月中/月末双定投、下跌增强加仓、上涨止盈与再平衡现金池计划。

> 免责声明：本项目仅用于投资计划测算与执行纪律管理，不构成任何投资建议。ETF属于权益资产，存在亏损风险。

## 功能特性

- 年度总投入资金 X 拆分：基础定投、下跌增强、再平衡资金
- 月中 + 月末双定投
- 自动计算 -5%、-8%、-12%、-16%、-20% 下跌增强线
- 自动计算 +25%、+40%、+60% 上涨弱止盈线
- 再平衡现金池重新投入规则
- 参数保存在浏览器 localStorage
- 支持打印 / 另存 PDF
- 纯静态页面，无需后端、无需登录

## 快速开始

直接用浏览器打开：

```bash
open index.html
```

或启动本地静态服务：

```bash
python3 -m http.server 8080
```

然后访问：

```text
http://localhost:8080
```

## 项目结构

```text
etf-planner/
├── index.html
├── docs/
│   └── strategy.md
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── workflows/
│       └── pages.yml
├── .editorconfig
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── package.json
└── README.md
```

> 维护说明：公开仓库只保留开源协作所需文件；历史版本、草稿和发布中间产物保存在维护者的私有仓库中。

## 默认策略

| 资金池 | 默认比例 |
|---|---:|
| 基础定投 | 70% |
| 下跌增强 | 20% |
| 再平衡 | 10% |

## 默认规则

- 阶段高点 H：最近120个交易日最高收盘价，每月第一个交易日更新。
- 基础定投：每月15日前后和25-28日各投入一次，共24次。
- 下跌增强：相对 H 回撤 -5%、-8%、-12%、-16%、-20% 时分5档加仓。
- 上涨止盈：相对整体持仓成本 C 上涨 +25%、+40%、+60% 时分别卖出总仓位5%、5%、10%。
- 再平衡回补：再平衡池按 -5%、-8%、-12%、-16%、-20% 分5档重新投入。

## GitHub Pages 部署

本项目包含 GitHub Actions 配置。进入仓库 Settings → Pages，将 Source 设为 GitHub Actions，推送 `main` 分支后即可部署。

## License

MIT
