# DingTalk 运维就绪

本指南定义 DingTalk 通道的专项运维检查项。

## 健康语义

- 仅当通道处于运行状态且流式连接有效时，健康检查才为真。
- 会话 webhook 目标过期后，发送前必须拒绝或刷新。

## 认证与投递

1. 校验 access token 获取与刷新生命周期。
2. 验证 session webhook 回复与 AI interaction API 的回退路径。
3. 拒绝任意 webhook 目标与不支持的媒体载荷。

## 事件处置步骤

1. 检查 DingTalk 应用凭据与 token 获取链路。
2. 验证 websocket stream mode 端点可达性。
3. 确认 reply target 缓存的新鲜度与过期处理逻辑。
4. 重启 worker 前先保留并记录上游错误返回。

## SLO 信号

- auth_fail_total
- stream_reconnect_total
- outbound_send_fail_total
- healthcheck_fail_total
