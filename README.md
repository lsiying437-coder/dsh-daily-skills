# dsh-daily-skills

日常通用 skill 集合，与渗透/逆向/SRC 等专项工作无关，纯写作、文档、图表、协作、工具类。
用途：把这批 skill 原样部署到另一台机器的 `~/.dsh/skills/` 下，让那台机器具备同样的日常能力。

## 清单（20 个）

| Skill | 用途 | 额外依赖 |
|---|---|---|
| `session-handoff` | 生成 AI 会话交接快照与续接提示词，换 session 不丢上下文 | 无（含 scripts） |
| `grill-me` | 就一个方案/设计反复拷问，直到达成共识、把决策树每个分支都问清 | 无 |
| `answer-me-with-html` | 把回答渲染成一页可视化 HTML 解释器 | 自带 CLI（需 node） |
| `diagram-generator` | 流程图、时序图、架构图、ER 图、思维导图等，输出 mermaid / graphviz / plantuml / SVG | 可选 graphviz、plantuml |
| `docs-generator` | 任务导向的技术文档（README、API 文档、架构说明） | 无 |
| `browser-automation` | 浏览器自动化 + Windows 桌面自动化统一入口 | Playwright；桌面部分需 OpenReverse |
| `cha-inkstage` | 写作类任务的路由入口（技术文章 / 文档 / 剧本 / 世界观 / 悬疑 / 成人） | 无 |
| `ink-tech` | 技术文章写作 | 无 |
| `ink-docs` | 项目文档写作 | 无 |
| `ink-seq` | 剧情续写 | 无 |
| `ink-cast` | 角色设定 | 无 |
| `ink-world` | 世界观设定 | 无 |
| `ink-dialogue` | 脚本对白 | 无 |
| `ink-voice` | 文风定制 / 仿写 | 无 |
| `ink-thriller` | 悬疑惊悚题材 | 无 |
| `ink-dark` | 黑暗题材 | 无 |
| `ink-adult` | 成人向文学写作 | 无 |
| `ink-analysis` | 分析报告写作 | 无 |
| `game-assets` | 游戏美术素材：像素/HD 精灵、图集、地块、音效与配乐 | Meowa CLI（外部工具） |
| `quarkclouddrive` | 夸克网盘：上传下载、分享转存、批量重命名、相册整理 | 需登录夸克账号 |

## 部署

```bash
git clone <本仓库地址> ~/dsh-daily-skills
mkdir -p ~/.dsh/skills
cp -R ~/dsh-daily-skills/skills/* ~/.dsh/skills/
```

重启 DSH 桌面版后生效。逐个核对：

```bash
for d in ~/dsh-daily-skills/skills/*/; do
  n=$(basename "$d")
  [ -f "$HOME/.dsh/skills/$n/SKILL.md" ] && echo "ok   $n" || echo "MISS $n"
done
```

## 不在本仓库、需单独装的

| Skill | 来源 |
|---|---|
| `gongwen`（中文公文 DOCX，GB/T 9704-2012） | `https://github.com/mizzlelover/gongwen-gbt9704-skill.git`（本机锁定 commit `6a5e47a`） |
| `ego-browser` | ego 浏览器安装时自带（本机为 `~/.local/share/ego/ego-skills` 的软链），装 ego 后自然出现 |
| `office` / `office-docx` / `office-xlsx` / `office-pptx` / `office-render` / `office-export-pdf` / `office-recalculate` | DSH 官方 bundle `@deepseek-ai/dsh-skill-office`，装 DSH 即有 |
| 全部安全/逆向/渗透类 skill | 不在本次迁移范围 |

## 来源与许可

- 除 `gongwen` 外，这些 skill 均为本机收集的副本，各自目录内保留原 `LICENSE` / `licenses/` 文件，未改动内容。
- 本仓库仅供同账号设备之间同步使用。
- `ink-*` 与 `cha-inkstage` 属自建写作体系，可自由修改。
