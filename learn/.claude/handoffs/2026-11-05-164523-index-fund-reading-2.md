# Handoff: 《指数基金投资指南》第3章读完，接第4章

## Session Metadata
- Created: 2026-11-05 16:45:23
- Project: /Users/panruiqi/learn
- Branch: main
- Session duration: 约 Nov 5 全天（含利率/央行传导的插入讨论）

### Recent Commits (for context)
  - [none relevant: 个人阅读任务，无代码提交]

## Handoff Chain

- **Continues from**: [2026-11-04-160457-index-fund-reading.md](./2026-11-04-160457-index-fund-reading.md)
  - Previous title: 在 learn 目录继续阅读《指数基金投资指南》
- **Supersedes**: 上一份的“阅读进度/锚点”部分（偏好与格式规则仍有效）

> 先读上一份的“必须保留的阅读偏好”：中文、只发真实原文与原图、每段约2500字、图表随正文发、页脚 *原文与原图照录，未核验现行产品、费率及规则。*

## Current State Summary

第3章（宽基指数 + 行业指数）已全部读完：恒生、H股等宽基之后，行业部分依次读过必需消费、医药、可选消费、养老、银行、证券、金融、地产、军工、环保、白酒（表3.35），以及章末“投资者笔记”和章节装饰原图均已恢复发送。下一步是第4章“如何挑选适合投资的指数基金”（价值投资三原则、四类估值指标等开篇内容记录显示已有接触，但用户的“继续”应从第4章正文开头核对后发送，避免重复）。期间用户另外学习了中国利率与货币政策传导链（政策利率→银行资金成本→贷款定价；贷款损失准备≠存款准备金；DR007 vs LPR），该讨论已结束。

## Codebase Understanding

## Architecture Overview

文件驱动阅读流：原 EPUB（唯一依据）→ zipfile 读 XHTML → 原文发送；图片从 EPUB images/ 原样提取到“阅读插图”目录后内嵌。无应用代码。

## Critical Files

| File | Purpose | Relevance |
|------|---------|-----------|
| /Users/panruiqi/Downloads/2637-指数基金投资指南/指数基金投资指南.epub | 原书 | 正文与图唯一依据 |
| /Users/panruiqi/Downloads/2637-指数基金投资指南/阅读插图 | 已提取原图（约65张，含表3.35、投资者笔记、章节装饰） | 内嵌图片路径 |
| /var/folders/nh/6d3ppt0j1dg5wyk0qxd4c5bh0000gn/T/index-fund-guide-0ljlot_k/text | 临时正文缓存，仅到 part0025（第4章标题页） | 可能被清理；第4章正文需从EPUB的 text/part0026.html 起恢复 |
| /Users/panruiqi/learn/学习笔记/03-估值与选基.md | 精简学习笔记 | 可追加第3章后半与第4章 |

### Key Patterns Discovered

EPUB 内 text/part0026+ 为第4章正文（part0027 约30KB 为主体）；章节图片在 images/ 下，按 alt/引用映射。

## Work Completed

### Tasks Finished

- [x] 第3章行业指数全部读完并恢复所有原书基金表格
- [x] 章末投资者笔记、章节装饰图恢复
- [x] 利率传导链讨论（学习者答对多题）

## Files Modified

| File | Changes | Rationale |
|------|---------|-----------|
| 阅读插图/ 下多张图片 | 新提取原图 | 随正文内嵌 |

## Decisions Made

| Decision | Options Considered | Rationale |
|----------|-------------------|-----------|
| 利率学习按资金传导链顺序 | 按概念罗列 vs 传导链 | 更易理解因果 |

## Pending Work

## Immediate Next Steps

1. 读本文件与上一份偏好；用户加载交接时只简短确认。
2. 用户说“继续”：从EPUB恢复 text/part0026.html、part0027.html 到新的空临时目录（zipfile，python3 -I），核对第4章开头，发约2500字并带对应原图。
3. 若发现第4章开头已发过的部分，按用户最近已读内容衔接，不重复。

### Blockers/Open Questions

- [ ] 确认第4章已发到哪一句（观察记录显示价值投资三原则与估值指标已出现）

### Deferred Items

- 用户问过看盘软件推荐，已答，无待办。

## Context for Resuming Agent

## Important Context

阅读偏好不变：只发原文+原图，不加总结/考题；用户提问再解释。书为2017年，数据与规则可能过时。系统无 `python` 命令，用 `python3`。

## Assumptions Made

- 第3章已结束，下一个是第4章。

## Potential Gotchas

- 临时缓存只到 part0025，没有第4章正文，需重新解压。
- 官方网页抓取曾被 fake-IP 的 SSRF 规则拦截。

## Environment State

### Tools/Services Used

- python3 zipfile；无服务运行。

### Active Processes

- None

### Environment Variables

- None

## Related Resources

- [上一份交接](./2026-11-04-160457-index-fund-reading.md)
- /Users/panruiqi/learn/学习笔记/03-估值与选基.md
