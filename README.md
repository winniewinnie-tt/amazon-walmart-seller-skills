# Sorftime Winnie 跨境卖家全链路 Skill

面向 Amazon 与 Walmart US 卖家的 AI Agent 技能包。下载解压后，按包内的安装脚本即可接入 Codex、Claude Code、WorkBuddy 或其他支持 `SKILL.md` 的 Agent 环境。

## 公开下载

| 技能包 | 内容 | 下载 |
|---|---|---|
| Amazon 卖家全链路 Skill | 18 个 Skill，覆盖数据层、市场、选品、供应链、利润、关键词、Listing、图片/A+、广告、VOC、专利风控 | [下载 ZIP](https://github.com/winniewinnie-tt/amazon-walmart-seller-skills/releases/latest/download/Sorftime-Amazon-Fullchain-Skill-Winnie-2026.10.29.zip) |
| Walmart US 全链路 Skill | 1 个主流程 Skill + 4 个前台核验配套 Skill | [下载 ZIP](https://github.com/winniewinnie-tt/amazon-walmart-seller-skills/releases/latest/download/Sorftime-Walmart-Fullchain-Skill-Winnie-v2.0.0.zip) |

发布页：[查看全部版本、校验值和更新说明](https://github.com/winniewinnie-tt/amazon-walmart-seller-skills/releases)

## 一分钟安装

### Amazon

```bash
unzip Sorftime-Amazon-Fullchain-Skill-Winnie-2026.10.29.zip
cd "Amazon卖家全链路Skill（10.27更新版）-Winnie"
python3 install.py --dest ~/.codex/skills
```

安装后重启或刷新 Agent。Amazon 包默认也支持安装到 `~/.agents/skills`；如需覆盖升级，先阅读包内 `安装说明.md`。

### Walmart US

```bash
unzip Sorftime-Walmart-Fullchain-Skill-Winnie-v2.0.0.zip
bash walmart-chain-v2-tag/install.sh ~/.codex/skills
cp -R walmart-chain-v2-tag/companion-skills/* ~/.codex/skills/
```

安装后新开一个 Agent 会话，然后输入：

```text
使用 walmart-chain-v2-tag 做沃尔玛全流程分析。
```

Windows、Claude Code、WorkBuddy 和其他宿主安装方式见 [INSTALL.md](INSTALL.md)。

## 使用前准备

- 两个包都不包含 Sorftime Account-SK、第三方 Provider Key、Cookie、许可证私钥或用户数据。
- 使用者需要使用自己的 Sorftime 账号，并在本机完成 MCP 或 CLI 配置。
- 生图能力需要使用者自行配置兼容的 Provider Key；没有 Key 时只输出视觉策略、Storyboard 和 Prompt。
- 专利结果只用于商业风险初筛，不构成法律意见。
- Walmart 平台规则、佣金与履约费会变化，正式上架前以 Walmart Seller Center 当前规则为准。

## 完整性校验

下载 ZIP 和 `SHA256SUMS.txt` 后运行：

```bash
shasum -a 256 -c SHA256SUMS.txt
```

Amazon 包解压后还可以运行：

```bash
python3 verify_package.py
```

预期输出：`skills=18 issues=0`。

## 授权与第三方组件

每个包内的来源声明、使用边界和第三方许可证继续有效。转发或二次分发时不得删除署名、联系方式、服务入口和第三方 `LICENSE` 文件。详见 [NOTICE.md](NOTICE.md)。

## 全链路地图

### Amazon

![Amazon 卖家全链路工作流地图](media/amazon-workflow-map.png)

### Walmart US

![Walmart 全链路工作流地图](media/walmart-workflow-map.png)

## 数据服务入口

Sorftime 注册、开通、查看账户或额度不足时：

- https://open.sorftime.com/home?tag=MDIz
- 优惠码：`023`

本仓库用于公开发布与下载，不接收或收集账号密钥。

