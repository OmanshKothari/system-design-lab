# System Design Lab

Hands-on system design problems. Each one is designed from first principles
(requirements, estimation, API, data model, architecture, deep dives) and then
implemented, load-tested, and reviewed as a Spring Boot service.

## Problems

| #  | Problem       | Status          | Design                                        | Service                           |
|----|---------------|-----------------|-----------------------------------------------|-----------------------------------|
| 01 | URL Shortener | Phase 0 – Setup | [Design doc](01-url-shortener/docs/design.md) | [Code](01-url-shortener/service/) |

## How each problem is worked

Every problem moves through the same gated phases. A phase is complete only when
its artifact has passed review, is committed, and the problem's `PROGRESS.md`
is updated.

| Phase | Name              | Artifact                                                        |
|-------|-------------------|-----------------------------------------------------------------|
| 0     | Setup             | Repository, templates, build + lint + tests running in CI       |
| 1     | Requirements      | Functional, measurable non-functional, explicit out-of-scope    |
| 2     | Estimation        | Traffic, storage, bandwidth, memory, with every assumption stated |
| 3     | API               | OpenAPI 3 specification, including errors and status codes      |
| 4     | Data model        | Schema driven by access patterns; storage choice as an ADR      |
| 5     | High-level design | C4 context and container diagrams; flows for the main paths     |
| 6     | Deep dives        | The hardest problems identified, each with alternatives and an ADR |
| 7     | Build             | Vertical slices, each reviewed before the next                  |
| 8     | Verify            | Load test against Phase 2 numbers; observability in place       |
| 9     | Retrospective     | What breaks at 10x/100x, lessons learned, README polish         |

## Repository layout

```
system-design-lab/
├── README.md                  # This index
├── mentoring/                 # Review rules used with Claude
├── templates/                 # Design doc, ADR, and retrospective templates
└── NN-problem-name/
    ├── README.md              # Problem summary, how to run, results
    ├── PROGRESS.md            # Phase gates, decision log, open questions
    ├── docs/
    │   ├── design.md          # Living design document
    │   ├── api/               # OpenAPI specification
    │   ├── adr/               # Architecture Decision Records
    │   ├── diagrams/          # Diagram sources (Mermaid / PlantUML)
    │   └── sketches/          # Hand-drawn first drafts
    ├── service/               # Spring Boot application
    ├── infra/                 # Local runtime configuration
    └── perf/                  # Load-test scripts and results
```

## Conventions

- Architecture decisions are recorded as ADRs using [`templates/adr.md`](templates/adr.md),
  based on Michael Nygard's format.
- Architecture diagrams follow the [C4 model](https://c4model.com) and are kept as
  text source (Mermaid renders natively on GitHub).
- APIs are specified with the [OpenAPI Specification](https://spec.openapis.org/oas/latest.html).
- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org).
- First drafts are done by hand; photos live in each problem's `docs/sketches/`.

## Adding a new problem

1. Copy the folder skeleton of an existing problem (without its content) to `NN-problem-name/`.
2. Copy [`templates/design-doc.md`](templates/design-doc.md) to `docs/design.md`.
3. Add a row to the table above.
4. Update the "Current problem" line in the Claude Project instructions.

## How I work

All designs and code in this repository are my own. I use Claude strictly as a
reviewer under the rules in
[`mentoring/claude-project-instructions.md`](mentoring/claude-project-instructions.md):
it critiques and points to references, but does not write designs or code.
