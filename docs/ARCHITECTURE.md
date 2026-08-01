# Repository architecture

```mermaid
flowchart LR
  R[User request] --> S{kotlin-stable}
  S --> B[kotlin-gradle-build]
  S --> C[kotlin-coroutines]
  S --> T[kotlin-testing]
  S --> V[kotlin-code-review]
  J[Java source project] --> M[kotlin-java-migration]
  M --> A[kotlin-java-migration-testing]
  B --> A
  C --> A
  T --> A
  A --> G[Parity gate: 100% tests + assets + MATCH]
```

The core skills solve Kotlin-native engineering tasks independently. The two migration skills compose them: implementation owns the source-object and contract ledger; acceptance owns source-test parity, copied assets, whole-project `<project>-test` execution, differential comparison, and Kotlin-only risk tests.

