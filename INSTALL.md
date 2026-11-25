# 安装说明

两个发行包都使用普通的 `SKILL.md` 目录结构。把包含 `SKILL.md` 的目录复制到宿主可识别的 skills 目录，重启或刷新 Agent 后即可被发现。

常用目录：

| 宿主 | 建议目录 |
|---|---|
| Codex | `~/.codex/skills` 或 `~/.agents/skills` |
| Claude Code | `~/.claude/skills` |
| WorkBuddy | `~/.workbuddy/skills` |
| 其他 Agent | 该宿主文档指定的 skills 目录 |

## Amazon 卖家全链路

### macOS / Linux

```bash
unzip Sorftime-Amazon-Fullchain-Skill-Winnie-2026.10.29.zip
cd "Amazon卖家全链路Skill（10.27更新版）-Winnie"
python3 install.py --dest ~/.codex/skills
```

先查看安装计划：

```bash
python3 install.py --dest ~/.codex/skills --dry-run
```

已有同名 Skill 时，安装器默认停止，避免旧 Skill 与新清单混装。确认覆盖升级后使用：

```bash
python3 install.py --dest ~/.codex/skills --force
```

安装器会先把旧版本移动到 `.backup-AmazonFullchain-时间戳`。

### Windows PowerShell

```powershell
Expand-Archive .\Sorftime-Amazon-Fullchain-Skill-Winnie-2026.10.29.zip -DestinationPath .
Set-Location ".\Amazon卖家全链路Skill（10.27更新版）-Winnie"
py -3 .\install.py --dest "$HOME\.codex\skills"
```

### 安装后验证

```bash
python3 doctor.py --dest ~/.codex/skills
python3 verify_installed.py --dest ~/.codex/skills
```

## Walmart US 全链路

### macOS / Linux

```bash
unzip Sorftime-Walmart-Fullchain-Skill-Winnie-v2.0.0.zip
bash walmart-chain-v2-tag/install.sh ~/.codex/skills
cp -R walmart-chain-v2-tag/companion-skills/* ~/.codex/skills/
```

`install.sh` 只安装主流程 Skill。复制 `companion-skills/` 后，才会同时获得前台关键词搜索、商品详情、评论采集与评论真实性检查能力。

### Windows PowerShell

```powershell
Expand-Archive .\Sorftime-Walmart-Fullchain-Skill-Winnie-v2.0.0.zip -DestinationPath .
New-Item -ItemType Directory -Force "$HOME\.codex\skills" | Out-Null
Copy-Item -Recurse .\walmart-chain-v2-tag "$HOME\.codex\skills\walmart-chain-v2-tag"
Copy-Item -Recurse .\walmart-chain-v2-tag\companion-skills\* "$HOME\.codex\skills"
```

### 安装后检查

```bash
cd ~/.codex/skills/walmart-chain-v2-tag
python3 scripts/preflight_guard.py --channel auto --required 1 --json
```

有 Sorftime MCP 时，也可以在 Agent 中先调用 `common_usage_query` 检查余额。

## Claude Code 与 WorkBuddy

把目标目录替换成对应宿主的 skills 目录即可。

Amazon：

```bash
python3 install.py --dest ~/.claude/skills
python3 install.py --dest ~/.workbuddy/skills
```

Walmart：

```bash
bash walmart-chain-v2-tag/install.sh ~/.claude/skills
cp -R walmart-chain-v2-tag/companion-skills/* ~/.claude/skills/

bash walmart-chain-v2-tag/install.sh ~/.workbuddy/skills
cp -R walmart-chain-v2-tag/companion-skills/* ~/.workbuddy/skills/
```

## 故障排查

### Agent 没有发现 Skill

1. 确认目标目录下存在 `SKILL.md`。
2. 确认目录名与 frontmatter 中的 `name` 一致。
3. 重启宿主，或新开一个会话。

### Amazon 安装器提示冲突

这是防混装保护。先查看 `--dry-run` 输出，确认后再使用 `--force`。

### Walmart 提示未配置 Sorftime 或额度不足

先完成自己的 Sorftime MCP/CLI 配置，再运行 `preflight_guard.py`。不要把 Account-SK 发到公开仓库、Issue、评论区或聊天群。

### ZIP 文件名在 Windows 显示乱码

优先使用 7-Zip、Bandizip 或 Windows 11 文件资源管理器解压。解压后运行 `verify_package.py` 检查 Amazon 包完整性。

