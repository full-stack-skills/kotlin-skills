# Kotlin Skills

[中文](README.zh-CN.md)

Production-oriented Kotlin skills for AI coding agents. The repository follows the same layered model as `rust-skills`: language semantics, build engineering, concurrency, testing, review, and lossless source-language migration are separate composable skills.

See [repository architecture](docs/ARCHITECTURE.md) for the composition and acceptance flow.

## Initial skill set (7)

| Skill | Responsibility |
|---|---|
| `kotlin-stable` | Stable Kotlin language semantics and JVM interop boundaries |
| `kotlin-gradle-build` | Gradle Kotlin DSL, modules, toolchains, dependencies, and CI |
| `kotlin-coroutines` | Structured concurrency, Flow, cancellation, and lifecycle safety |
| `kotlin-testing` | Unit, integration, coroutine, property, and end-to-end testing |
| `kotlin-code-review` | Correctness-first Kotlin review with actionable findings |
| `kotlin-java-migration` | Lossless Java-to-Kotlin implementation workflow |
| `kotlin-java-migration-testing` | Complete source-test parity, asset parity, and differential acceptance |

## Migration completion contract

A migration is complete only when all source production objects and public contracts are accounted for, 100% of source tests and concrete cases are implemented in Kotlin, source test assets are copied byte-for-byte, both complete suites pass, and every differential case is `MATCH`. Coverage is supporting evidence, never a substitute for behavioral parity.

Large migrations must add a dedicated `<project>-test` Gradle module for whole-project acceptance. Tests inside production modules remain local unit or component tests.

## Validation

```bash
python3 scripts/validate_skills.py
python3 scripts/validate_skills.py --check-examples
```

The second command requires Java 21 and Gradle. CI uses Kotlin 2.4.10-compatible Gradle 9.5.0 and executes every golden example.

## License

Apache License 2.0.
