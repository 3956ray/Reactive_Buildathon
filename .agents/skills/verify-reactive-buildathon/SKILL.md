---
name: verify-reactive-buildathon
description: 为 Reactive Buildathon 执行真实用户路径验证、保存证据并维护 Feature Map；当前空项目阶段报告启动阻塞，不将基础检查冒充功能验证。
---
# Reactive Buildathon verification（草稿）

这是借鉴 Pstack 的 Codex 适配入口，不是完整 Pstack 插件安装。可选调用，队友无需使用相同 agent。
从仓库根目录读取 `docs/verification/RUNBOOK.md`、`docs/verification/features/README.md` 和 `docs/COLLABORATION.md`。所有共享流程以这些文档为准，避免复制出两份 Feature Map。

## Launch
目前没有应用或启动命令，不能启动。先调查实际产品源码、README、package scripts、测试配置、环境示例、登录与种子数据；勿运行 `_bmad/` 作为产品。将发现记录到 Runbook，缺失要求向用户确认。

## Doctor
先检查当前目录、git commit/工作区、应用入口和实际启动配置。没有应用时返回 blocked，不以 HTTP 200 或 skill 校验成功宣称产品可用。
有应用后记录准确实例 URL、进程/会话所有者、构建版本、登录状态和可用种子数据。实例异常先 doctor，再重置本次创建的实例；不操作未知共享实例。

## Drive
仅执行 Feature Map 中已有确认需求和实际入口的功能。优先现有用户路径测试工具；网页通过浏览器真实点击，CLI 走真实命令，API 走公开入口。不能通过内部 setter 或测试后门伪造成功。当前没有可执行功能。

## Evidence
依 Runbook 保存操作与结果、退出码/日志/截图及真实副作用。明确模拟边界。证据放在独立于临时实例的持久目录；不要写入密钥。

## Cleanup
仅停止本次创建且记录的进程/会话，删除本次临时数据，不按进程名称批量杀进程。失败路径也清理。清理后逐个确认本次证据文件仍存在且非空。

## 维护
源码变化后核对受影响 Feature Map，再真实执行对应流程。完整维护必须覆盖全部已登记功能；未覆盖则报告部分完成或 blocked。区分文档漂移、驱动工具缺口和产品回归；不为了匹配错误实现改写需求。此技能不授权产品修复、PR 发布、自动合并或部署。
只有完成至少一个真实功能的启动、doctor、驱动、证据、清理及证据存活检查后，才把草稿状态改为已验证，并附运行记录。
