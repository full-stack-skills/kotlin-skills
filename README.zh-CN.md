# Kotlin Skills

[English](README.md)

面向 AI 编程代理的生产级 Kotlin 技能包。仓库沿用 `rust-skills` 的分层模式：语言语义、构建工程、并发、测试、审查和无损迁移分别建模，并可按任务组合使用。

技能组合与验收流程见[仓库架构](docs/ARCHITECTURE.md)。

## 初始技能集（7 个）

| 技能 | 职责 |
|---|---|
| `kotlin-stable` | Kotlin 稳定语言语义与 JVM 互操作边界 |
| `kotlin-gradle-build` | Gradle Kotlin DSL、模块、工具链、依赖与 CI |
| `kotlin-coroutines` | 结构化并发、Flow、取消和生命周期安全 |
| `kotlin-testing` | 单元、集成、协程、属性与端到端测试 |
| `kotlin-code-review` | 以正确性为先的 Kotlin 代码审查 |
| `kotlin-java-migration` | Java 到 Kotlin 的无损实现流程 |
| `kotlin-java-migration-testing` | 源测试、测试资产和逐用例差分验收 |

## 迁移完成标准

只有当源项目的生产对象和公开契约全部入账、源语言测试及具体用例 100% 在 Kotlin 中无损实现、测试资产逐字节复制、两套完整测试均通过且每个差分用例均为 `MATCH` 时，才可声明迁移完成。覆盖率只是辅助证据，不能替代行为一致性。

大型迁移必须建立独立的 `<project>-test` Gradle 模块承担整体验收；生产模块内的测试只承担局部单元或组件验证。

## 验证

```bash
python3 scripts/validate_skills.py
python3 scripts/validate_skills.py --check-examples
```

第二条命令需要 Java 21 和 Gradle。CI 使用与 Kotlin 2.4.10 兼容的 Gradle 9.5.0，并执行全部 golden 示例。

## 许可证

Apache License 2.0。
