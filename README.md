# dsh-daily-skills

日常通用 skill 集合，与渗透/逆向/SRC 等专项工作无关。用途：把这批 skill 原样部署到另一台机器的 `~/.dsh/skills/` 下。

## 清单（5 个）

| Skill | 用途 | 运行时依赖 |
|---|---|---|
| `session-handoff` | 生成 AI 会话交接快照与续接提示词，换 session 不丢上下文 | `python3`（`scripts/create_handoff.py`） |
| `grill-me` | 就一个方案/设计反复拷问，直到把决策树每个分支都问清、达成共识 | 无 |
| `answer-me-with-html` | 把回答渲染成一页可视化 HTML 解释器 | `node`（`scripts/am.mjs`） |
| `diagram-generator` | 流程图、时序图、架构图、ER 图、思维导图等，输出 mermaid / graphviz / plantuml / SVG | 可选 `graphviz`、`plantuml` |
| `docs-generator` | 任务导向的技术文档（README、API 文档、架构说明） | 无 |

## 部署

```bash
git clone <本仓库地址> ~/dsh-daily-skills
mkdir -p ~/.dsh/skills
cp -R ~/dsh-daily-skills/skills/* ~/.dsh/skills/
```

重启 DSH 桌面版后生效。验证：

```bash
for n in session-handoff grill-me answer-me-with-html diagram-generator docs-generator; do
  [ -f "$HOME/.dsh/skills/$n/SKILL.md" ] && echo "ok   $n" || echo "MISS $n"
done
```

## 不在本仓库、需单独装的

| Skill | 来源 |
|---|---|
| `gongwen`（中文公文 DOCX，GB/T 9704-2012） | `https://github.com/mizzlelover/gongwen-gbt9704-skill.git`，本机锁定 commit `6a5e47a` |
| `office` / `office-docx` / `office-xlsx` / `office-pptx` / `office-render` / `office-export-pdf` / `office-recalculate` | DSH 官方 bundle `@deepseek-ai/dsh-skill-office`，装 DSH 即有 |

## 来源与许可

- 这些 skill 为本机收集的副本，各自目录内保留原 `LICENSE` / `licenses/` 文件，未改动内容。
- 仓库公开可读，匿名即可 clone，无需 GitHub 凭据。
