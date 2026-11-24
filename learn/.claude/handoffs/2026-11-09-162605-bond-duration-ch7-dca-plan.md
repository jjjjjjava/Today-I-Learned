# Handoff: 第7章债券基金/资产配置已读；久期教学进行中；定投计划与隆基规则落地

## Session Metadata
- Created: 2026-11-09 16:26:05
- Project: /Users/panruiqi/develop/自用/Today-I-Learned/learn
- Branch: develop
- Session duration: 2026-11-09 下午，约2小时（读第6、7章 + 隆基复核 + 建定投计划）

### Recent Commits (for context)
  - fad605b docs: add New Hope research and sync remaining learning state
  - 073b991 docs: add Longi investment research and confirmed PB strategy
  - 6042da8 Merge branch 'develop' of ssh://ssh.github.com:443/jjjjjjava/Today-I-Learned into develop

## Handoff Chain

- **Continues from**: [2026-11-07-220734-new-hope-pb-aktools.md](./2026-11-07-220734-new-hope-pb-aktools.md)
  - Previous title: 新希望 PB 同源数据复核；指数基金第5章待续
- **Supersedes**: 上份的阅读锚点（第5章 part0040 已过时，见下）。新希望等待策略、隆基策略仍有效。

> 先读本份，再按需看上份。

## Current State Summary

用户继续精读《指数基金投资指南》。本轮已发完第6章（三个定投实例、读者案例、章末笔记位置）和第7章（货币基金、债券基金前半及后半、图7.3/7.4、家庭资产配置两条原则）。读到债券基金"利率低位选短期，利率高位选长期"及3%~3.5%参考线后，用户问不懂，正用 teach 技能教学：已讲"利率"含义（票面利率 vs 到期收益率），用户三层判断（价格与到期收益率反向、旧债跌价逻辑等）已答对。**当前停在**：teach 流程下一步，让用户自己从"未来收到固定的钱"推出长期债为何更利率敏感（久期），再讲书中历史利率线只是参照、不保证收益。同时已新建 `我的定投计划.md`（四步总纲）并把隆基的投入封顶/暂停线/分批退出规则落到隆基调研文档。

## Codebase Understanding

### Architecture Overview
- 个人知识库，无软件实现。EPUB 是原文与原图唯一依据；笔记在 `笔记/`，研究文档在 learn/ 根。
- 单一来源原则：隆基全部参数只写 `隆基绿能投资调研文档.md`；`我的定投计划.md` 只引用不复制。

### Critical Files

| File | Purpose | Relevance |
|------|---------|-----------|
| HANDOFF.md | 交接入口 | 仍指向旧 handoff，**需改指向本份** |
| 我的定投计划.md | 四步定投计划（未提交，新文件） | 现金流、收入等 `____` 待用户填 |
| 隆基绿能投资调研文档.md | 隆基参数唯一来源（未提交，已改） | 含投入封顶、暂停线、分批退出 |
| 新希望投资调研文档.md | 新希望等待策略 | 未变 |
| 书/指数基金投资指南.epub | 原书 | 续读依据 |
| 笔记/00-全书地图.md、04-定投买卖与计划.md、05-配置与心态.md | 笔记 | 第5～7章笔记仍待补 |
| /tmp/ch5/ | 提取的正文(.html.txt)与 img/（图7.1～7.4、表6.x、表7.1） | 临时文件，丢失需从 EPUB 重取 |

### Key Patterns Discovered
- python3 -I + zipfile/re 从 EPUB 提取正文与图；正文后缀 `.html.txt`。
- 发书规则：按原文逐段完整发出，图用 `![](路径)` + `[查看原图](file://…)`，不总结替代原文。
- 解释概念用 teach 技能（先探起点、推导、不堆结论）。

## Work Completed

### Tasks Finished

- [x] 第6章三个定投实例与四个读者案例正文发送
- [x] 隆基PB双口径复核一致：近15个月PB中位数2.325；固定估值下预算约7期耗尽；净资产衰减年化约14.9%~18.3%（压力测试显示PB回升仍可能亏损）
- [x] 隆基文档落地投入封顶、暂停线、分批退出规则
- [x] 新建 `我的定投计划.md`（四步总纲，每月50%结余用于定投已确认）与每月投资前审阅清单
- [x] 第7章：货币基金选择与三技巧、债券基金定义/作用/怎么投资/品种、家庭资产配置两条原则、章末投资者笔记位置
- [x] 解释利率含义（到期收益率 vs 票面利率）

### Files Modified

| File | Changes | Rationale |
|------|---------|-----------|
| 隆基绿能投资调研文档.md | 增投入封顶、暂停线、分批退出规则 | 用户确认的风险规则 |
| 我的定投计划.md | 新建 | 书要求计划写在纸面 |
| obsidian workspace 配置 | 自动变动 | 无需处理 |

### Decisions Made

| Decision | Options Considered | Rationale |
|----------|-------------------|-----------|
| 每月结余50%用于定投 | 其他比例 | 原书规则，用户确认 |
| 17,500元是计算基准，非单期上限 | 硬上限 | 用户确认；总预算15万封顶 |
| 隆基参数只放隆基文档 | 多处复制 | 单一来源防不一致 |

## Pending Work

## Immediate Next Steps

1. 继续 teach：问用户"未来固定现金流 + 折现率上升，长债为何跌更多"，完成久期直觉；说明3%~3.5%是2017年书中历史参照，不是今天买卖线，国债收益率不等于债基实际收益。
2. 久期讲完后，回到阅读：发第7章章末"投资者笔记"（图7.4之后的位置），再进入第8章。
3. 补笔记：第5、6、7章写入 `笔记/04`、`05`；更新 `00-全书地图.md`；更新 HANDOFF.md 指向本份。
4. 提交未入库文件（`我的定投计划.md`、隆基文档修改）。

### Blockers/Open Questions

- [ ] 用户尚未填 `我的定投计划.md` 中收入/开支/备用金/隆基15万占总资产比例及资金来源
- [ ] 隆基实际首投年月、成交记录未记录；策略确认不等于已成交，不代用户下单
- [ ] 第5章"投资者笔记"（part0040）此前标为下一段，是否仍需补发，下次确认

### Deferred Items

- 隆基退出精确PB线与卖出比例（上轮标"待定"，本轮已写入规则，核对文档为准）
- 未查询当前利率，若涉及现价需另查

## Context for Resuming Agent

## Important Context

- 在 learn/ 目录开 pi。阅读偏好：原文完整分段发送，图要展示，不替代原文。
- 隆基核心假设（保留）：仍有恢复盈利能力、净资产侵蚀未抵消估值修复；每次投入前查五项；C类PB比例加权是用户最终选择。
- 不要把"继续研究"当续读，也不要混淆隆基已过估值关与新希望未过。
- 公共仓库历史含明文凭据（见前序记录）：不要把任何凭据写入文档。

### Assumptions Made

- 用户当前主线=teach 久期，然后回读第7章末。
- 3%~3.5%解释依据为书中配图标题与正文，未验证现价。

### Potential Gotchas

- HANDOFF.md 仍指向旧 handoff。
- /tmp 提取物可能丢失。
- 多期付息债不能套一年期简单除法算到期收益率。

## Environment State

### Tools/Services Used

- teach 技能（`.pi/skills/teach`，嵌套 .pi 仓库被忽略，其他机器需单独安装）；python3 -I 提取 EPUB；AKTools 经 codemode。

### Active Processes

- 无。

### Environment Variables

- 无。

## Related Resources

- [我的定投计划](../../我的定投计划.md)
- [隆基绿能投资调研文档](../../隆基绿能投资调研文档.md)
- [新希望投资调研文档](../../新希望投资调研文档.md)
- [上份 handoff](./2026-11-07-220734-new-hope-pb-aktools.md)
