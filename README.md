# What Does It Say

使用 AI Agent 辅助阅读的 Skill 集合。通过接入微信读书数据源和飞书文档能力，自动化生成结构化的阅读分析报告。

## 包含的 Skill

### [what-does-it-say](skills/what-does-it-say/SKILL.md) — 检视阅读助手

输入微信读书上的书名，自动采集书籍数据（目录、热门划线、书评、个人笔记），根据书籍类型生成一份结构化的飞书检视阅读文档。

**核心能力：**

- 从微信读书自动获取书籍信息、目录、热门划线和个人笔记
- 根据书籍类型（小说文学、技术实践、哲学思想、商业管理等 9 种类型）自动适配分析策略
- 生成包含三张可视化图表的飞书文档：书籍全景图、核心洞察图、读者匹配图
- 基于 5W1H 框架做深度内容分析，提出启发思考的问题

**依赖：**

- [weread](https://cdn.weread.qq.com/skills/weread-skills.zip) — 微信读书数据源
- [lark-doc](https://github.com/larksuite/cli) — 飞书文档创建与编辑
- [lark-whiteboard](https://github.com/larksuite/cli) — 飞书画板图表绘制

**触发方式：**

在 Claude Code 中对说"检视阅读"、"快速了解一本书"、"这本书讲了什么"、"生成读书笔记"等指令即可触发。
