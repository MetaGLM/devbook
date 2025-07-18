# OpenAPI 规范文件

本目录包含 ZHIPU AI 的 OpenAPI 3.0.1 规范文件，采用模块化设计，按功能分类组织。

## 文件结构

```
openapi/
├── index.json          # 主索引文件，引用所有模块
├── chat.json           # 聊天对话 API
├── embedding.json      # 文本嵌入 API
├── audio.json          # 音频处理 API
├── image.json          # 图像生成 API
├── video.json          # 视频生成 API
├── file.json           # 文件管理 API
├── tool.json           # 工具 API
├── assistant.json      # 助手 API
├── openapi.json        # 完整规范文件（已废弃，保留兼容性）
└── README.md           # 本说明文件
```

## 模块说明

### 1. chat.json - 聊天对话 API
- **路径**: `/paas/v4/chat/completions`
- **功能**: 提供 AI 聊天对话能力
- **特性**: 
  - 支持流式和非流式响应
  - 多种模型选择
  - 完整的消息格式定义
  - 工具调用支持

### 2. embedding.json - 文本嵌入 API
- **路径**: `/paas/v4/embeddings`
- **功能**: 将文本转换为向量表示
- **特性**:
  - 支持多种嵌入模型
  - 可配置向量维度
  - 兼容 OpenAI Embedding API
  - 批量处理支持

### 3. audio.json - 音频处理 API
- **路径**: 
  - `/paas/v4/audio/speech` - 文本转语音
  - `/paas/v4/audio/transcriptions` - 语音转文本
  - `/paas/v4/audio/customization` - 语音定制
- **功能**: 音频合成、识别和定制
- **特性**:
  - 多种语音合成模型
  - 多语言支持
  - 语音克隆功能

### 4. image.json - 图像生成 API
- **路径**: `/paas/v4/images/generations`
- **功能**: 从文本生成图像
- **特性**:
  - 使用 CogView-3-Plus 模型
  - 多种图像尺寸和风格
  - 高质量图像输出

### 5. video.json - 视频生成 API
- **路径**: 
  - `/paas/v4/videos/generations` - 视频生成
  - `/paas/v4/async-result/{id}` - 异步结果查询
- **功能**: 从文本或图像生成视频
- **特性**:
  - 支持多种视频生成方式
  - 异步处理机制
  - 多种视频格式

### 6. file.json - 文件管理 API
- **路径**:
  - `/paas/v4/files` - 文件列表和上传
  - `/paas/v4/files/{file_id}` - 文件管理
  - `/paas/v4/files/{file_id}/content` - 文件下载
- **功能**: 文件上传、下载和管理
- **特性**:
  - 支持多种文件格式
  - 分页查询
  - 文件状态跟踪

### 7. tool.json - 工具 API
- **路径**: `/paas/v4/tools/web-search`
- **功能**: 网络搜索工具
- **特性**:
  - 实时网络搜索
  - 多种搜索类型
  - 结果过滤和排序

### 8. assistant.json - 助手 API
- **路径**:
  - `/paas/v4/assistants` - 助手管理
  - `/paas/v4/assistants/{assistant_id}` - 单个助手操作
- **功能**: AI 助手的创建和管理
- **特性**:
  - 助手配置和定制
  - 工具集成
  - 文件附件支持

## 使用方法

### 1. 使用索引文件
```bash
# 使用主索引文件（推荐）
mint openapi-check openapi/index.json
```

### 2. 使用单个模块
```bash
# 只检查特定模块
mint openapi-check openapi/chat.json
mint openapi-check openapi/embedding.json
```

### 3. 在文档中引用
```json
{
  "openapi": "openapi/chat.json"
}
```

## 开发规范

### 1. 文件命名
- 使用小写字母和连字符
- 文件名应反映功能模块
- 保持简洁明了

### 2. 结构规范
- 每个文件包含完整的 OpenAPI 3.0.1 结构
- 包含 info、servers、security 等必要字段
- 使用统一的错误响应格式

### 3. 引用规范
- 使用相对路径引用
- 路径使用 URL 编码格式
- 保持引用的一致性

### 4. 版本控制
- 遵循语义化版本控制
- 重大变更需要更新主版本号
- 保持向后兼容性

## 维护指南

### 1. 添加新 API
1. 确定功能模块归属
2. 在对应模块文件中添加路径定义
3. 更新索引文件中的引用
4. 更新文档说明

### 2. 修改现有 API
1. 在对应模块文件中修改
2. 确保向后兼容性
3. 更新相关文档
4. 测试 API 规范有效性

### 3. 删除 API
1. 标记为废弃状态
2. 在下一个主版本中移除
3. 更新相关文档和示例

## 验证和测试

### 1. 规范验证
```bash
# 验证所有模块
mint openapi-check openapi/*.json

# 验证索引文件
mint openapi-check openapi/index.json
```

### 2. 文档生成
```bash
# 生成完整文档
mint openapi openapi/index.json

# 生成模块文档
mint openapi openapi/chat.json
```

## 注意事项

1. **兼容性**: 保持与现有系统的兼容性
2. **一致性**: 确保各模块间的参数和响应格式一致
3. **文档同步**: 及时更新相关文档和示例
4. **测试覆盖**: 确保所有 API 都有相应的测试用例

## 相关链接

- [OpenAPI 3.0.1 规范](https://spec.openapis.org/oas/v3.0.1)
- [Swagger Editor](https://editor.swagger.io/)
- [ZHIPU AI 开发者文档](../README.md) 