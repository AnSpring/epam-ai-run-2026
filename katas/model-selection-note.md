# Model Selection Note

**Date:** 2026-06-08  
**Author:** Anastazja — Data Quality Engineer  
**Project:** Personal learning project — EPAM AI Run Mission 2026 / Bootcamp 4.0  
**Task:** Generate a PySpark function that filters out records where `consent_flag` is False or null before writing to the Silver layer in a Medallion architecture on Databricks.  
**Committed location:** [GitHub repo path / Obsidian vault — to be filled on commit]

---

## Evaluation Criteria

| # | Criterion | Why it matters for this task |
|---|-----------|------------------------------|
| 1 | Correctness of consent logic | Function must exclude both False AND null — missing either case is a data quality defect |
| 2 | PySpark DataFrame API compliance | Databricks / Unity Catalog environment requires native DataFrame API; no pandas, no UDFs |
| 3 | Explicit null handling | As a DQ Engineer, implicit null behaviour is a risk — intent must be readable without PySpark internals knowledge |
| 4 | Docstring and readability | Code goes into a course artefact and a shared repo; must be reviewable by a peer without context |

---

## Prompt Used

```
Write a PySpark function `apply_consent_filter(df: DataFrame) -> DataFrame`
that filters out records where consent_flag is False or null.
The function should be compatible with Databricks / Unity Catalog environment.
Include: explicit null handling, docstring, and a brief inline comment
explaining the consent logic. Do not use pandas or UDFs.
```

---

## Output Comparison

### Model A: OpenAI Codex

> ```python
> from pyspark.sql import DataFrame
> from pyspark.sql import functions as F
>
> def apply_consent_filter(df: DataFrame) -> DataFrame:
>     """
>     Return only rows where `consent_flag` is explicitly True.
>     Rows with `consent_flag` set to False or NULL are removed.
>     This uses standard PySpark DataFrame operations and is compatible
>     with Databricks / Unity Catalog environments.
>     """
>     # Keep only records with an explicit positive consent value.
>     return df.filter(
>         F.col("consent_flag").isNotNull() & (F.col("consent_flag") == F.lit(True))
>     )
> ```

### Model B: Claude (via CodeMie / claude.ai)

> ```python
> from pyspark.sql import DataFrame
> from pyspark.sql.functions import col
>
> def apply_consent_filter(df: DataFrame) -> DataFrame:
>     """
>     Filter records to retain only those with explicit consent.
>     Removes rows where consent_flag is False or null. This ensures data
>     processing respects user privacy settings and regulatory requirements
>     (e.g., GDPR, CCPA).
>     Args:
>         df: Input DataFrame with a consent_flag column (boolean or nullable boolean).
>     Returns:
>         DataFrame: Filtered DataFrame containing only rows where consent_flag is True.
>     Raises:
>         AnalysisException: If consent_flag column does not exist in the DataFrame.
>     """
>     # Only retain rows where consent_flag is explicitly True (excludes False and null)
>     return df.filter(col("consent_flag") == True)
> ```

---

## Scorecard

| Criterion | Model A score (1–3) | Model A evidence | Model B score (1–3) | Model B evidence |
|-----------|---------------------|-----------------|---------------------|-----------------|
| Correctness of consent logic | 3 | Explicitly chains `isNotNull()` and `== True` — both False and null are excluded with no ambiguity | 2 | `col == True` works in PySpark because null comparisons return null (filtered out), but correctness depends on implicit engine behaviour rather than stated intent |
| PySpark DataFrame API compliance | 3 | Uses `F.col`, `F.lit`, standard filter — fully Databricks-compatible, no UDFs | 3 | Uses `col` from `pyspark.sql.functions`, standard filter — fully Databricks-compatible, no UDFs |
| Explicit null handling | 3 | `isNotNull()` is written out — reader immediately sees null exclusion as a deliberate decision | 1 | Null handling is implicit; a reviewer without deep PySpark knowledge cannot tell from the code alone that nulls are excluded |
| Docstring and readability | 2 | Short docstring covers intent and compatibility; one inline comment explains the logic | 3 | Full Google-style docstring with Args, Returns, Raises, Example — significantly richer; regulatory context (GDPR, CCPA) is explicitly noted |
| **Total** | **11** | | **9** | |

---

## Decision

**Selected model:** OpenAI Codex

**Rationale:** Codex scored higher on the two highest-priority criteria for a Data Quality Engineer: correctness of consent logic and explicit null handling. In a Silver layer transformation, relying on implicit PySpark null semantics to exclude nulls — as Claude's output does — is an unacceptable risk: the behaviour is correct today but invisible to a reviewer and fragile under schema changes. Claude produced a richer docstring, but documentation quality is easily improved with a follow-up prompt; implicit null handling is harder to catch and fix.

---

## Active Constraint

**What could change this decision within 30 days:**  
If the next course assignments shift toward MD artefact generation rather than PySpark code, Claude's superior documentation depth and structured output quality would make it the stronger choice for that task type.

---

## Revision History

| Version | Date | Change |
|---------|------|--------|
| 1.0 | 2026-06-08 | Initial commit — Kata 1, Model Selection |
