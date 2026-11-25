# 公开发布 2026.10.29

首次公开发布 Sorftime Winnie 的两个跨境卖家 Skill 包。

## Amazon 卖家全链路 Skill

- 18 个 Skill，覆盖 Sorftime 数据层、全链路编排、市场分析、选品、供应链与利润、关键词、Listing、图片与 A+、广告、VOC/竞品、专利风控。
- 包含安装器、环境自检、文件完整性校验、数据证据台账、工作流地图和使用入口。
- 包内运行守卫要求取数前检查凭证与余额；缺失数据必须标记，不允许编造或静默跳过。

## Walmart US 全链路 Skill

- 主流程覆盖选品、市场、实时前台核验、供应链、利润、关键词、Listing、Rich Media、合规、投放与复盘。
- 4 个配套 Skill 分别用于 Walmart 前台关键词搜索、商品详情、评论采集与评论真实性检查。
- 固定 Walmart US，Sorftime `domain=21`、1688 `domain=601`。
- 明确降级边界：不含 Walmart CPC 出价能力，不使用恒为 0 的 `WFSFee` 字段做利润判断。

## 安全与完整性

- ZIP 完整性检查通过。
- Amazon 包内置校验结果：`skills=18 issues=0`。
- 未发现 `.env`、私钥、证书、实际 API Key、Cookie 或 Account-SK。
- 两个 ZIP 的 SHA-256 值见 `SHA256SUMS.txt`。
- 包内第三方组件继续遵守各自许可证。

## 已知边界

- 使用数据能力需要使用者自己的 Sorftime 账号与额度。
- 生图需要使用者自行配置兼容的 Provider Key。
- 专利结果是风险初筛，不是法律意见。
- Walmart 费用与平台规则以提交时的官方最新规则为准。

