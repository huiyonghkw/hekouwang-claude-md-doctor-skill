# Changelog

本项目遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [1.1.0] - 2026-06-18

把 Claude Code 之父 Boris Cherny / Cat Wu 的"context minimalism · 别跟模型较劲做加法"
立场接进体检逻辑。

### 新增
- **第 10 项检查「别替模型补它已经会的」**：扫教学型措辞(如何使用 / 使用教程 /
  step by step / how to use)，命中即 WARN——这类通用写法随模型升级自动变强，
  写进常驻正文只是为"很快过时的东西"每次付上下文费。
- **「减法优先」元判据**：写进 `SKILL.md`，凌驾 9 项之上——加任何一段前先问
  "能不能不写在常驻正文里"。

### 变更
- **评分改为按重要度加权**：减法核心项(#1 篇幅 / #3 可操作 / #4 路由器 / #10)权重 1.5，
  加内容项(#6 Hook / #7 记忆 / #8 人格)降到 0.6。修掉旧逻辑"一边喊越短越好、
  一边因缺工作风格块扣分、逼用户把文件写长"的自相矛盾。
- **#8 工作风格块加上限护栏**：限 3–5 行，每行须对应一个"不写就会犯的具体错"，别写性格小作文。

## [1.0.0] - 2026-06-17

首个正式版本。把"CLAUDE.md 当运行时配置、不是项目说明书"的最佳实践做成可跑在任意项目上的体检器。

### 功能
- **9 项检查的命令行体检器 `check.py`**：篇幅 / 禁止清单 / 规则可操作 / 路由非图书馆 /
  高危模块本地 CLAUDE.md / Hook 强制 / MEMORY.md 回路 / 工作风格 / 30 秒三问。
- 输出彩色文本报告或 `--json`；评分 0–100（A/B/C/D）；有 FAIL → 退出码 1（可 CI 卡关）。
- 零运行时依赖（仅 Python 3 标准库）；只读，绝不读取 `.env` / `*.key` / `*.pem`。
- **`SKILL.md` 定性复核层**：在 Claude Code 内说「检查我的 CLAUDE.md」即可机检 + 模型复核 + 代修复。
- **Docker**：`docker run --rm -v "$PWD:/work" claude-md-doctor`，免装 Python。
- **GitHub Actions CI**：语法 + good/bad 夹具 + JSON 合法性。
- 中英双语 README、MIT LICENSE、CONTRIBUTING、示例动图（CLI 实录 + 动效报告卡）。

### 商业模型
- 命令行体检器开源免费（MIT）；品牌可视化报告卡为付费增值，依赖未公开字体/版式，不在仓库内。

[1.0.0]: https://github.com/huiyonghkw/hekouwang-claude-md-doctor-skill/releases/tag/v1.0.0
