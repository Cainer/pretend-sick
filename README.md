# SickBuddy 🤒 — AI 生病管理助手

> 生病了别慌，让 AI 帮你搞定一切：推测病症 → 病程预期 → 请假话术 → 证明获取 → 每日提醒。

## ✨ 核心功能

| 功能 | 说明 |
|------|------|
| 🩺 症状推测 | 文字/拍照描述症状，AI 推测可能病症并给出多种可能性 |
| 📅 病程时间线 | 告诉你第几天会怎样，第几天开始好转，不用瞎猜 |
| 📝 请假话术生成 | 根据病情 + 场景（公司/学校/正式/随意）自动生成请假消息 |
| 🏥 证明获取指南 | 推荐社区医院、线上问诊等快速开证明渠道 |
| 🔍 公司请假流程 | 查询钉钉/飞书/企微等平台的病假操作流程 |
| 🌡️ 多病交叉管理 | 感冒叠加肠胃炎？自动分析药物冲突和注意事项 |
| 📍 地理位置辅助 | 结合当地季节和流行病信息，推测更精准 |
| 💊 用药管理 | 记录用药、检查药物冲突、提醒注意事项 |
| 📊 恢复追踪 | 每日恢复评分、趋势曲线、复诊建议 |
| 🌤️ 天气+流行病 | 自动查询当地天气和当季高发病症 |
| 💊 每日提醒 | 当天可能的新症状、注意事项、是否该就医 |

## 🎯 设计哲学

1. **少问多做** — 不连续追问，缺关键信息才问一句
2. **天数匹配病症** — 请 1 天 = 轻微，3 天 = 中等，5 天+ = 较严重
3. **优先社区医院** — 社康更快更便宜，不用排大队
4. **先证明后请假** — 建议先拿证明再提交，一劳永逸

## 📦 安装

### 方式一：OpenClaw Skill 安装（推荐）

```bash
# 将本项目 clone 到 skills 目录
git clone https://github.com/Cainer/pretend-sick.git ~/.openclaw/workspace/skills/sick-buddy
```

### 方式二：手动安装

```bash
# 复制到 OpenClaw skills 目录
cp -r sick-buddy ~/.openclaw/workspace/skills/
```

## 🚀 使用

直接跟 AI 对话，不需要记命令：

```
你：我今天嗓子疼，有点低烧，想请2天假
AI：[推测病症 + 病程预期 + 请假话术 + 证明获取方案]
```

```
你：[发一张喉咙照片]
AI：让我看看... 喉咙后壁充血，扁桃体轻度肿大，可能是咽炎...
```

### CLI 工具

```bash
sick-buddy start 感冒              # 建档（自动查天气+流行病）
sick-buddy symptoms 嗓子疼         # 添加症状
sick-buddy set city 杭州           # 设置城市
sick-buddy set workplace 阿里      # 设置工作单位
sick-buddy status                  # 查看当前状态（含用药+恢复）
sick-buddy log 今天好多了           # 记录今日状态
sick-buddy history                 # 查看历史记录
sick-buddy suggest 3               # 根据天数推荐病症
sick-buddy template casual company # 生成请假模板

# 用药管理
sick-buddy medicine add 泰诺 1粒 每日3次   # 添加用药（自动检查冲突）
sick-buddy medicine list                   # 查看当前用药
sick-buddy medicine stop 泰诺              # 停用药物
sick-buddy medicine check 布洛芬           # 检查药物冲突

# 恢复追踪
sick-buddy recover score 6 喉咙好多了      # 记录恢复评分
sick-buddy recover chart                   # 查看恢复曲线
sick-buddy recover advise                  # 获取恢复建议

# 天气+流行病
sick-buddy weather 杭州            # 查询天气和当季高发病
```

## 🤧 支持的病症

| 病症 | 典型病程 | 典型请假天数 |
|------|---------|------------|
| 普通感冒 | 5-7 天 | 2-3 天 |
| 流感 | 7-14 天 | 3-5 天 |
| 新冠感染 | 7-14 天 | 5-7 天 |
| 支原体肺炎 | 2-4 周 | 5-7 天 |
| 急性肠胃炎 | 2-5 天 | 2 天 |
| 偏头痛 | 4-72 小时 | 1 天 |
| 咽炎/扁桃体炎 | 5-10 天 | 2-3 天 |
| 登革热 | 7-10 天 | 7-10 天 |
| 皮肤过敏 | 数天到数周 | 1-2 天 |
| 腰肌劳损 | 1-4 周 | 3-5 天 |
| 痛风 | 3-10 天 | 1-3 天 |
| 急性结膜炎 | 5-14 天 | 1-2 天 |
| 颈椎病急性发作 | 3-7 天 | 1-3 天 |

## 📂 项目结构

```
pretend-sick/
├── README.md              # 本文件
├── SKILL.md               # OpenClaw Skill 定义（核心 prompt）
├── package.json           # 包信息
├── src/
│   └── sick-buddy         # CLI 工具（Python）
└── knowledge/
    ├── diseases.md        # 疾病知识库
    └── leave-templates.md # 请假话术模板
```

## ⚠️ 安全声明

本工具不提供医疗诊断，所有信息仅供自我护理参考。如症状加重或持续不退，请及时就医。

## 📄 License

MIT © 2026 Cainer
