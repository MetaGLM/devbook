# ZHIPU AI 开发者文档

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

4. **OPENAPI定义校验**

> OPEN API 接口的定义基于 OPENAPI 3.0.1 规范，在各自模块的json文件中定义，例如： `openapi/chat.json` ，并在 `openapi/index.json` 文件中进行索引。

   ```bash
   mint openapi-check openapi/chat.json
   ```

5. **断链校验**
   ```bash
   mint broken-links
   ```

**[`OEPNAPI`接口定义](openapi/openapi.json) 推荐使用 https://editor.swagger.io/ 在线编辑，或使用 Webstorm 本地编辑可视化**

## 项目结构

```
devbook/
├── cn/                    # 中文文档
│   ├── api/              # API 文档
│   │   ├── agents/       # 智能体相关
│   │   ├── audio/        # 音频相关
│   │   ├── chat/         # 聊天对话相关
│   │   ├── embedding/    # 文本嵌入相关
│   │   ├── file/         # 文件管理相关
│   │   ├── image/        # 图像生成相关
│   │   ├── tools/        # 工具相关
│   │   └── video/        # 视频生成相关
│   ├── guide/            # 使用指南
│   ├── issue/            # 常见问题
│   └── update/           # 更新日志
├── en/                    # 英文文档
│   ├── api/              # API 文档
│   │   ├── agents/       # 智能体相关
│   │   ├── audio/        # 音频相关
│   │   ├── chat/         # 聊天对话相关
│   │   ├── embedding/    # 文本嵌入相关
│   │   ├── file/         # 文件管理相关
│   │   ├── image/        # 图像生成相关
│   │   ├── tools/        # 工具相关
│   │   └── video/        # 视频生成相关
│   ├── guide/            # 使用指南
│   ├── issue/            # 常见问题
│   └── update/           # 更新日志
├── openapi/              # OpenAPI 规范文件
│   ├── openapi.json      # 完整的 OpenAPI 规范（已废弃，保留兼容性）
│   ├── index.json        # 各模块 API 的索引，作为主入口点
│   ├── chat.json         # 聊天对话 API 规范
│   ├── embedding.json    # 文本嵌入 API 规范
│   ├── audio.json        # 音频处理 API 规范
│   ├── image.json        # 图像生成 API 规范
│   ├── video.json        # 视频生成 API 规范
│   ├── file.json         # 文件管理 API 规范
│   ├── tool.json         # 工具 API 规范
│   └── assistant.json    # 助手 API 规范
├── resource/             # 静态资源
│   ├── favicon.svg
│   ├── logo_icon.png
│   └── logo.png
├── style.css             # 样式文件
├── docs.json             # 文档配置
├── LICENSE               # 许可证
├── CONTRIBUTING.md       # 贡献指南
└── CODE_OF_CONDUCT.md    # 行为准则
```

## OpenAPI 规范文件

项目采用模块化的 OpenAPI 规范文件结构，按功能模块拆分为多个 JSON 文件：

### 模块化文件结构

- **chat.json** - 聊天对话相关 API
  - `/paas/v4/chat/completions` - 聊天完成接口
  - 支持流式和非流式响应
  - 包含完整的消息格式和参数定义

- **embedding.json** - 文本嵌入相关 API
  - `/paas/v4/embeddings` - 文本嵌入接口
  - 支持多种模型和向量维度
  - 兼容 OpenAI Embedding API

- **audio.json** - 音频处理相关 API
  - `/paas/v4/audio/speech` - 文本转语音
  - `/paas/v4/audio/transcriptions` - 语音转文本
  - `/paas/v4/audio/customization` - 语音定制

- **image.json** - 图像生成相关 API
  - `/paas/v4/images/generations` - 图像生成接口
  - 支持多种风格和尺寸
  - 使用 CogView-3-Plus 模型

- **video.json** - 视频生成相关 API
  - `/paas/v4/videos/generations` - 视频生成接口
  - 支持多种视频生成方式
  - `/paas/v4/async-result/{id}` - 异步结果查询

- **file.json** - 文件管理相关 API
  - `/paas/v4/files` - 文件列表和上传
  - `/paas/v4/files/{file_id}` - 文件信息获取和删除
  - `/paas/v4/files/{file_id}/content` - 文件内容下载

- **tool.json** - 工具相关 API
  - `/paas/v4/tools/web-search` - 网络搜索工具

- **assistant.json** - 助手相关 API
  - `/paas/v4/assistants` - 助手列表和创建
  - `/paas/v4/assistants/{assistant_id}` - 助手管理

### 优势

1. **模块化管理** - 按功能模块拆分，便于维护和更新
2. **独立开发** - 各模块可以独立开发和测试
3. **清晰结构** - 开发者可以快速定位相关 API
4. **版本控制** - 便于跟踪各模块的变更历史
5. **团队协作** - 不同团队可以并行开发不同模块

## 开发规范

### 文档结构

- API 文档基于对应的 OpenAPI JSON 文件自动生成
- 每个 API 模块都有独立的中英文文档
- 文档包含完整的参数说明、示例代码和错误处理

### 命名规范

- 文件名使用小写字母和连字符
- API 路径使用 RESTful 风格
- 参数名使用 snake_case
- 响应字段使用 snake_case

### 版本控制

- 遵循语义化版本控制
- 重大变更需要更新主版本号
- 向后兼容的变更更新次版本号
- 补丁修复更新修订版本号

## 快速开始

1. 克隆项目到本地
2. 安装依赖：`npm install`
3. 启动开发服务器：`npm run dev`
4. 访问 `http://localhost:3000` 查看文档

## 贡献指南

欢迎贡献代码和文档！请查看 [CONTRIBUTING.md](CONTRIBUTING.md) 了解详细的贡献流程。

## 许可证

本项目采用 MIT 许可证，详见 [LICENSE](LICENSE) 文件。

## 联系我们

- 官网：https://open.bigmodel.cn/
- 开发者社区：https://chat.z.ai/
- 邮箱：user_feedback@z.ai