<!--
Sync Impact Report
==================
Version change: 1.0.0 -> 2.0.0
Modified principles:
  - I. Directorio `constitution/` como fuente de verdad -> I. Public-Interest Mission
  - II. Gobernanza por capas -> II. Ethics, Privacy & Compliance
  - III. Normas declarativas y verificables -> III. Open Science & Reproducibility
  - IV. Responsabilidad por dominio -> IV. Explainability & Model Transparency
  - V. Revisión de cumplimiento -> V. Spec-Driven Technical Standards
Added sections:
  - Additional Constraints
  - Development Workflow & Quality Gates
Removed sections:
  - Governing Documents (the previous Toolyo-specific document inventory)
Follow-up TODOs:
  - RATIFICATION_DATE remains a TODO because the original adoption date was not provided.
-->

# HomeVal Constitution

## Core Principles

### I. Public-Interest Mission

HomeVal MUST democratize access to real-estate valuation data across Spain. The project
MUST operate as an open-source, public-interest engine that reduces information
asymmetry for buyers, renters, urban researchers, and journalists. Features and
technical decisions MUST be evaluated against this mission so that access to useful
valuation information is not restricted to privileged market participants.

### II. Ethics, Privacy & Compliance

HomeVal MUST comply with the GDPR and applicable Spanish data-protection regulations.
The system MUST store zero personally identifiable information (PII). Spatial data and
analytics MUST operate only on aggregated cadastral polygons, postal codes, and census
tracts (*secciones censales*). Data models, ingestion pipelines, APIs, exports, logs,
and observability data MUST be reviewed to prevent direct or indirect re-identification.
These constraints protect residents while preserving the public value of aggregated
analysis.

### III. Open Science & Reproducibility

Datasets, engineered features, models, evaluation metrics, and material transformations
MUST be documented and transparent enough to reproduce the published results. Data
pipelines and model-training workflows MUST be reproducible from open public data feeds,
including Catastro, INE, and OpenStreetMap where applicable. A change to a source,
transformation, feature, model, or metric MUST identify its provenance and effect on
results. Reproducibility is required to enable independent scrutiny and correction.

### IV. Explainability & Model Transparency

Every price prediction MUST expose feature-attribution metrics, including SHAP values or
an explicitly documented equivalent, that identify the exact drivers of the result.
Attributions MUST communicate the direction and magnitude of each material feature's
contribution, including positive and negative value where applicable. The product MUST
not present a prediction as an unexplained black-box output; users need enough context
to assess limitations and make informed decisions.

### V. Spec-Driven Technical Standards

Every feature MUST follow the SpecKit workflow in order:
`/constitution` -> `/specify` -> `/clarify` -> `/plan` -> `/tasks` -> `/analyze` ->
`/implement`. Code MUST preserve strict type safety and comprehensive test coverage.
Spatial functionality MUST include performance benchmarks for its indexing and query
paths before merge. A feature is not complete until its specification, implementation,
tests, and required spatial benchmarks provide evidence that these standards are met.

## Additional Constraints

HomeVal MUST use aggregated geographic units as the smallest spatial scope for stored
data and analytics. No feature may introduce address-level, household-level, or
person-level storage without a formal constitutional amendment that is demonstrably
compatible with the zero-PII rule; such an amendment MUST NOT weaken applicable law.

Public-data ingestion MUST retain source attribution, acquisition metadata, and the
transformation steps needed to reproduce derived datasets. Model releases MUST identify
the training data, feature definitions, evaluation population, metrics, and known
limitations. Documentation and user-facing explanations MUST distinguish observed data,
inferences, and estimates.

## Development Workflow & Quality Gates

All feature work MUST pass these gates before merge:

1. The complete SpecKit workflow MUST be followed and its artifacts MUST be available
   for review.
2. Tests MUST cover changed behavior, including regression cases. Strict type checking
   MUST pass without introducing unreviewed type escapes.
3. Data, privacy, and compliance checks MUST confirm that no PII is stored or emitted.
4. Model changes MUST include reproducible evaluation metrics and feature attributions.
5. Spatial changes MUST include indexing and query performance benchmarks with recorded
   methodology and measurable results.
6. Reviewers MUST verify alignment with this constitution and document any approved
   deviation through a formal amendment or an explicitly recorded exception.

## Governance

This constitution is the highest-level project governance document. If an implementation
practice conflicts with it, the constitution prevails until formally amended.

**Amendment procedure:**
1. A proposed amendment MUST state the affected principle or section, rationale,
   compatibility impact, and migration requirements.
2. The amendment MUST be reviewed for mission alignment, GDPR and Spanish compliance,
   privacy impact, reproducibility, explainability, testing, and spatial performance.
3. The approved amendment MUST update this document and its Sync Impact Report in the
   same change.
4. Affected SpecKit artifacts and implementation guidance MUST be updated after the
   amendment when the amendment changes feature-development requirements.

**Versioning policy (semantic):**
- **MAJOR**: removal or incompatible redefinition of a principle or governance rule.
- **MINOR**: addition of a principle or material expansion of governance requirements.
- **PATCH**: clarification, wording, typo correction, or other non-semantic refinement.

**Compliance review expectations:**
- Every pull request and formal review MUST verify the applicable principles and quality
  gates.
- Compliance reviews MUST record evidence for privacy, provenance, explainability, tests,
  and spatial benchmarks when those areas are affected.
- Suspected PII exposure, irreproducible outputs, unexplained predictions, or missing
  required benchmarks MUST block release until resolved or formally amended.

**Version**: 2.0.0 | **Ratified**: TODO(RATIFICATION_DATE): original adoption date not provided | **Last Amended**: 2026-10-26
