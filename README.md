# Claude Code Skills

我的 [Claude Code](https://claude.com/claude-code) 个人技能集。

## 安装

把某个 skill 文件夹复制进你的技能目录,然后在 Claude Code 里调用:

```bash
cp -r premium-design-loop ~/.claude/skills/
# 然后: /premium-design-loop
```

## 技能列表

| 技能 | 作用 |
|------|------|
| **premium-design-loop** | 把网页的视觉质感逐轮迭代到「高级」。每轮:渲染 → 12 维打分 → 优化最弱维度 → 重新打分,带前后对比截图。覆盖排版、层级、配色、光影动效、移动端、可访问性、收尾细节。面向「做得更高级 / 更贵 / 更有质感」的需求。 |

---

## 实战演示:guobi.ai 首页

用 `premium-design-loop` 对果比AI 首页做的一次真实迭代,从默认 AI 味页面到「暖版 Apple + 光影」。每张图是该轮**优化后**的状态。

### 原始

默认系统字、扁平等权卡片、大片死空白、新闻味文案——典型「AI 生成感」。

![原始](assets/01-original.png)

### 第 1 轮 · 排版与层级

衬线大标题取代 24px 弱标题、卡片加序号分级、暖色光晕背景、文案去模板化。

![第1轮](assets/02-round1.png)

### 第 2 轮 · 图标系统 + 主张

统一线性图标系统、「结论 · 判断 · 风险信号」价值条把主张落进版式、修复对比度不足的小字。

![第2轮](assets/03-round2.png)

### 第 3 轮 · 主推卡强化

日报做成视觉主导的主卡:暖金渐变实底 + 反白图标 + 「今日」实时标签。

![第3轮](assets/04-round3.png)

### 第 4 轮 · 跨栏 Hero

日报升级为跨栏全宽 hero 主卡、副标题改衬线,建立 display→sub→body 三级字阶。

![第4轮](assets/05-round4.png)

### 最终 · 暖版 Apple + 光影

超大衬线标题、漂浮暖光球、胶片颗粒质感、缓慢漂移的蓝图网格、等宽 mono 技术标签、光标视差,定位重塑为「AI 试验场」。

![最终](assets/06-final.png)
