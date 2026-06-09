# readme-template — 高星项目文档结构参考

## 顶部区域（必须）

项目名称

<p align="center">
 <img src="demo.gif" alt="demo" width="600"/>
</p>

一句话精准描述这个工具解决什么问题，为谁解决。

## 功能章节写法

好的写法（具体、有对比）：

- 自动分析 Skill 代码结构，无需手动填写文档
- 支持中英双语输出，适配国际开源社区
- 生成即可运行的代码示例，不再有"仅供参考"的伪代码

差的写法（空洞、无信息）：

- 功能强大
- 使用方便
- 高效稳定

<p align="center">
 <a href="#"><img src="https://img.shields.io/github/stars/user/repo?style=flat-square"/></a>
 <a href="#"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square"/></a>
 <a href="#"><img src="https://img.shields.io/badge/version-1.0.0-green?style=flat-square"/></a>
</p>

## 快速开始章节写法

必须在 5 分钟内让用户跑起来：

```bash
# 1. 克隆仓库
git clone https://github.com/你的用户名/项目名

# 2. 安装依赖（如果有）
npm install # 或 pip install -r requirements.txt

# 3. 运行第一个示例
# 直接可以复制粘贴执行的命令
```

## 配置表格写法

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| model | string | claude-sonnet-4 | 使用的 AI 模型 |
| language | string | zh | 输出语言，支持 zh / en |
| style | string | professional | 文档风格 |

## 项目结构写法

```
project-name/
├── SKILL.md          # 核心技能定义
├── README.md         # 本文档
├── references/
│   ├── template.md   # README 模板
│   └── style.md      # 写作规范
└── scripts/
    └── publish.sh    # 发布脚本
```
