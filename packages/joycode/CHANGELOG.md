# 更新记录

## 0.2.0

- 按 JoyCode 模型目录中的 `extJson.adapterType` 自动选择 Chat Completions、Responses 或 Anthropic Messages，使 `/models` 返回的 GPT、Claude 及其他模型都能使用正确的 SDK 和网关。
- 请求转发支持 `Request` 输入，并正确清理宿主生成的鉴权头及长度/主机头。
- 修复 Anthropic Messages 与 Responses 的正常非流式 JSON 被误判为无效响应的问题；`flatten` 仅用于 Chat Completions。

验证：38 项回归测试通过；真实 JoyCode 账号的 `joycode_modelList` 返回 15 个模型，覆盖 10 个 chat、4 个 `openai-response` 和 1 个 `anthropic`。

## 0.1.1

- 支持浏览器登录京东账号，自动接收并验证 JoyCode 票据，保存租户和登录类型。
- 接入 IDE 同款额度接口，展示套餐、已用/剩余积分及有效期文字。
- 按账号动态同步模型列表和积分消耗倍率，正确识别 0× 免费模型。
- 补齐聊天请求所需的真实账号元数据，修复已登录却无法回复的问题。
- 将 HTTP 200 流式响应中的裸 JSON 错误转换为明确错误，避免客户端空白等待；权限错误不再误判为登录过期。
- 保留多轮消息与工具调用，加入 JoyCode 图标并缩短本地插件目录名。

验证：25 项回归测试通过；JoyAI-Code-1.6 的真实流式回复、工具调用往返和 magpie provider test 通过；用户确认 Claude 桌面端可使用。

## 0.1.0

- 本地供应商插件原型：手动 ptKey 登录、静态模型列表、签名网关转发及可选纯文本压平模式。
