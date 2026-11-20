# 验证运行手册

状态：BLOCKED / DRAFT。当前没有应用代码。此文档是接入清单，尚未证明可执行。

| 项目 | 调查结论 |
| --- | --- |
| 产品启动/构建命令 | 不存在 |
| 用户入口/端口 | 未定义 |
| 测试工具 | 无产品测试；BMAD 的 Python 测试属于工具自身 |
| 登录/钱包 | 未定义，不能假设需要钱包 |
| 数据准备/迁移 | 未定义 |
| 实例隔离 | 待应用确定后检查端口、数据目录、账户与外部状态 |
| 已验证产品功能 | 0 |

## 应用出现后的首次接入
从产品源码与文档确定准确启动命令、依赖版本、环境变量名称、数据准备与就绪条件。不得记录 secret 值。明确启动失败怎样清理。已有服务先确认归属，不默认复用；支持并行时使用独立端口和数据目录。
Doctor 必须确认正确构建、实例所有权、认证与数据可用性。仅存活的进程不是可用实例。
若前置数据缺失或产品期望不明确，记录阻塞并向用户确认。首批 Feature Map 建立 3–5 个真实用户目标，不用健康检查充数。

## 一次验证记录
目录：`artifacts/verification/<唯一 run-id>/`，临时实例数据放在另一个临时目录。
记录：时间与时区、commit/dirty 状态、执行人/agent、功能 ID、需求依据、环境、启动命令、实例归属、doctor 结果、逐步操作、可观察结果、真实副作用、证据相对路径、未验证内容、清理结果。
结果分类：PASS（范围内真实路径通过）、FAIL（与已确认预期不符）、BLOCKED（前置条件不足）、NOT RUN（未执行）。模拟通过单独注明，不能当真实链路通过。
结束时关闭本次浏览器上下文/进程并删除本次临时状态；随后检查每个证据文件存在且非空。失败也必须走清理。敏感截图与日志分享前脱敏。

## 参考来源与限制
- https://github.com/cursor/plugins/tree/main/pstack
- https://github.com/cursor/plugins/blob/main/pstack/skills/create-verification-skill/SKILL.md
- https://github.com/cursor/plugins/blob/main/pstack/skills/maintain-verification-skill/SKILL.md
- https://www.youtube.com/watch?v=I_oMJk6barY
前三项已读取。视频原链接抓取被限流，未获得原视频或完整逐字稿；不声称已读演讲。采用 Pstack 的真实操作、Feature Map、证据持久保存和维护原则，未复制 Cursor 的配置或模型路由。
