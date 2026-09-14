# Travel Planner Agent

> 人机协作的行程规划 + 出发前自动优化 Agent 工具。从一个真实的 12 天印尼巴厘岛行程(20+ 轮人工反馈迭代)中提炼方法论。

[English intro below]

## 这是什么

一个「行程规划 Agent」的完整实践项目,包含三部分:

```
travel-planner/
├── README.md                          # 本文件:项目介绍
├── case-study/
│   └── bali-2026-iteration-log.md     # 真实案例:20+ 轮人工反馈的完整迭代日志
├── itinerary/
│   └── bali-2026/index.html           # 最终行程交付物(响应式 HTML,可外发/打印)
└── agent/
    ├── SKILL.md                       # trip-planner skill:可复用的规划指令(接入 Claude Code)
    └── OPTIMIZER.md                   # 出发前自动优化器:就绪度检查 + 事件触发重规划
```

## 核心方法论(从真实案例提炼)

1. **约束优先**:先锁定硬约束(已订包车/酒店/机票、人数、体力、证件等级),再展开规划
2. **多方案对比**:不确定时给 2–3 版方案 + 对比表(强度/在途时间/体验/成本),让用户拍板,不替用户决定
3. **在途时间显式化**:每一段标交通方式 + 纯在途耗时,累计在途是决策关键指标
4. **预订状态机**:所有项目标 `✓已订 / 建议预订 / 待退`,形成事实上的就绪度仪表盘
5. **风险预案**:行程依赖项(天气/火山/航变)给 A/B 双预案 + 明确决策时间点
6. **交付即外发**:产出单文件响应式 HTML(零依赖、兼容旧内核浏览器),可打印/可托管
7. **简洁 + 可靠来源**:每轮输出控制信息密度;事实性信息(签证/口岸/票价区间)标注来源与时效

## 快速开始(接入 Claude Code)

```bash
# 1. 安装 skill
mkdir -p ~/.claude/skills/trip-planner
cp agent/SKILL.md ~/.claude/skills/trip-planner/SKILL.md

# 2. 在任意目录对话
#    "帮我规划 10.1–10.7 的日本行程,候选地:大阪/北海道,2人,喜欢潜水和温泉"
```

规划的完整流程、输出格式、迭代协议都写在 [agent/SKILL.md](agent/SKILL.md) 中。

出发前的就绪度检查与自动优化,见 [agent/OPTIMIZER.md](agent/OPTIMIZER.md)。

## English Intro

A human-in-the-loop travel planning agent distilled from a real 12-day Indonesia trip (Bali + volcanoes + Hanoi transit) that went through 20+ feedback iterations. Includes: full iteration case study, the final responsive-HTML deliverable, a reusable Claude Code skill encoding the planning methodology, and a pre-departure readiness optimizer design.

## License

MIT
