# Z.AI 开发者文档

智谱 AI 平台开发者文档的源代码仓库，基于 Mintlify 构建的现代化文档站点。

## 🚀 快速开始

### 环境要求

- Node.js 16.0 或更高版本
- npm 或 yarn 包管理器

### 本地开发

1. **安装 Mintlify CLI**
   ```bash
   npm i -g mint
   ```

2. **克隆项目**
   ```bash
   git clone <repository-url>
   cd devbook
   ```

3. **启动开发服务器**
   ```bash
   mint dev
   ```
   
   服务器将在 `http://localhost:3000` 启动，支持热重载。


## 📁 项目结构

```
devbook/
├── .github/                    # GitHub 配置文件
│   ├── ISSUE_TEMPLATE/         # Issue 模板
│   ├── PULL_REQUEST_TEMPLATE.md # PR 模板
│   └── workflows/              # GitHub Actions 工作流
├── cn/                         # 中文文档
│   ├── api/                    # API 参考文档
│   │   ├── chat/              # 对话 API
│   │   ├── tools/             # 工具 API
│   │   └── video/             # 视频生成 API
│   └── guide/                  # 使用指南
│       ├── llm/               # 语言模型指南
│       ├── overview/          # 概览
│       ├── tools/             # 工具指南
│       └── video/             # 视频生成指南
├── en/                         # 英文文档
│   ├── api/                    # API Reference
│   │   ├── chat/              # Chat API
│   │   ├── tools/             # Tools API
│   │   └── video/             # Video API
│   └── guide/                  # Guides
│       ├── llm/               # Language Models
│       ├── overview/          # Overview
│       ├── tools/             # Tools
│       └── video/             # Video Generation
├── openapi/                    # OpenAPI 规范文件
│   └── openapi.json           # API 接口定义
├── resource/                   # 静态资源
│   ├── favicon.svg            # 网站图标
│   └── logo.png               # Logo 图片
├── docs.json                   # Mintlify 配置文件
├── style.css                   # 自定义样式
└── README.md                   # 项目说明文档
```

## 📝 文档编写指南

### 文件组织

- **双语支持**: 文档分为 `cn/` (中文) 和 `en/` (英文) 两个目录
- **模块化**: 按功能模块组织文档，包括 API 参考和使用指南
- **MDX 格式**: 支持 Markdown 和 React 组件的混合使用

### 添加新页面

1. 在相应的语言目录下创建 `.mdx` 文件
2. 在 `docs.json` 中的 `navigation` 部分添加页面配置
3. 确保中英文版本保持同步

### API 文档

- API 文档基于 `openapi/openapi.json` 自动生成
- 支持交互式 API 测试界面
- 修改 OpenAPI 规范后会自动更新文档

## 🛠️ 开发工具

### 代码规范

- 使用 GitHub Actions 进行 PR 检查
- 遵循项目的代码规范和提交规范
- 参考 `CONTRIBUTING.md` 了解贡献指南

### 本地预览

开发过程中可以实时预览文档效果：
- 修改文档内容后自动刷新
- 支持多语言切换预览
- 内置搜索功能测试

## 🔗 相关链接

- [Z.AI 官网](https://bigmodel.cn/)
- [Mintlify 文档](https://mintlify.com/docs)
- [GitHub 仓库](https://github.com/THUDM)
- [Discord 社区](https://discord.com/channels/1346756824233148527/1359832169333395496)

## 📄 许可证

本项目采用相应的开源许可证，详见 `LICENSE` 文件。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！请先阅读 `CONTRIBUTING.md` 和 `CODE_OF_CONDUCT.md`。