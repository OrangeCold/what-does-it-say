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
- [lark-whiteboard](https://github.com/larksuite/cli) — 飞书画板图表绘制（全景图、匹配图）
- [beautiful-feishu-whiteboard](https://github.com/zarazhangrui/beautiful-feishu-whiteboard) — 核心洞察图的 SVG 渲染（35 种配色风格 + 画板硬规则）

**触发方式：**

在 Claude Code 中对说"检视阅读"、"快速了解一本书"、"这本书讲了什么"、"生成读书笔记"等指令即可触发。

## 安装

### 1. 安装依赖 Skill

将四个依赖 skill 下载到 `~/.claude/skills/` 目录：

```bash
# 安装微信读书 skill
curl -L https://cdn.weread.qq.com/skills/weread-skills.zip -o /tmp/weread-skills.zip
unzip /tmp/weread-skills.zip -d ~/.claude/skills/weread

# 安装飞书文档和画板 skill（通过 lark-cli）
# 参考 https://github.com/larksuite/cli 获取安装指引

# 安装 beautiful-feishu-whiteboard skill（核心洞察图 SVG 渲染）
# 将该 skill 目录放入 ~/.claude/skills/beautiful-feishu-whiteboard/
```

### 2. 安装本 Skill

```bash
# 克隆仓库并将 skill 链接到 Claude Code skills 目录
git clone <repo-url> /tmp/what-does-it-say
cp -r /tmp/what-does-it-say/skills/what-does-it-say ~/.claude/skills/what-does-it-say
```

### 3. 安装 CLI 工具

```bash
# 安装 lark-cli（飞书官方 CLI）
# 参考 https://github.com/larksuite/cli

# 安装飞书画板 CLI（用于 SVG 图表渲染）
npx -y @larksuite/whiteboard-cli@^0.2.11 -v
```

### 4. 配置环境变量

```bash
# 设置微信读书 API Key
export WEREAD_API_KEY="your-api-key"

# 建议写入 shell 配置文件（~/.zshrc 或 ~/.bashrc）使其持久化
echo 'export WEREAD_API_KEY="your-api-key"' >> ~/.zshrc
```

### 5. 验证安装

在 Claude Code 中运行以下检查：

```bash
echo $WEREAD_API_KEY          # 应输出非空字符串
lark-cli --version             # 应输出版本号
npx -y @larksuite/whiteboard-cli@^0.2.11 -v  # 应输出版本号
ls ~/.claude/skills/what-does-it-say/SKILL.md  # 应存在
ls ~/.claude/skills/weread/                     # 应存在
ls ~/.claude/skills/lark-doc/                   # 应存在
ls ~/.claude/skills/lark-whiteboard/            # 应存在
ls ~/.claude/skills/beautiful-feishu-whiteboard/ # 应存在
```

所有检查通过后，在 Claude Code 中说"帮我检视阅读《原则》"即可开始使用。

## 交流群

加入飞书群，交流使用心得、反馈问题：

<p align="center">
  <img src="docs/飞书群.png" alt="飞书群二维码" width="300" />
</p>
