# Prompt Template: PySpark Transformation Function Generator

**Date:** 2026-06-08  
**Author:** Anastazja Bobrowa - Data Quality Engineer  
**Project:** Personal learning project - EPAM AI Run Mission 2026 / Bootcamp 4.0  
**Model:** Codex (selected in Kata 1)  
**DIAL location:** https://chat.lab.epam.com/share/QSLQnvitQNZZJQ4KvMwp97HR5Nr63hyq5hddy8CPRBzxj5Doys6GEyzfzYz2DJHvtnY14qSneN4bJor8iCJsxCcpDipgBN5Xxn2ER61Xyze2yF8fwrPtFbrpETDProVNNPLyjsQNVUpN5PucZQd1MtE56**Committed 
**Location:** https://github.com/AnSpring/epam-ai-run-2026/blob/main/katas/kata2-shared-prompt/prompt-or-skill-template.md

---

## Purpose

Generate a production-ready PySpark transformation function from a plain-language data rule description, for use by a Data Engineer working on a Medallion architecture pipeline on Databricks.

---

## Variable Placeholders

| Placeholder               | Description                                                                                   | Example value                                                                           |
| ------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `{{transformation_rule}}` | Plain-language description of what the function must do — what to filter, clean, or transform | "Filter out records where consent_flag is False or null before writing to Silver layer" |
| `{{source_layer}}`        | The Medallion layer the function reads from                                                   | `Bronze`                                                                                |
| `{{target_layer}}`        | The Medallion layer the function writes to                                                    | `Silver`                                                                                |
| `{{partition_column}}`    | Column used for Delta table partitioning in the target layer                                  | `market_code`                                                                           |

---

## Output Format Instruction

Return a Python code block only. No preamble, no explanation after the code block.

The function must include:
- Google-style docstring (Args, Returns, Raises)
- Explicit null handling where relevant
- One inline comment explaining the business logic
- Native PySpark DataFrame API only - no pandas, no UDFs
- Compatible with Databricks / Unity Catalog environment

---

## Prompt Body

```
You are a Senior Data Engineer working on a Databricks Medallion architecture project.

Write a PySpark function based on the following specification:

Transformation rule: {{transformation_rule}}
Source layer: {{source_layer}}
Target layer: {{target_layer}}
Partition column: {{partition_column}}

Requirements:
- Function name must reflect the transformation rule (e.g., apply_consent_filter, deduplicate_by_customer)
- Input: a PySpark DataFrame
- Output: a transformed PySpark DataFrame
- Include a Google-style docstring with Args, Returns, and Raises sections
- Handle null values explicitly where the rule involves nullable columns
- Add one inline comment explaining the business logic in plain English
- Use native PySpark DataFrame API only — no pandas, no UDFs
- Code must be compatible with Databricks / Unity Catalog environment

Return a Python code block only. No explanation before or after the code.
```

---

## Test Run (Author)

**Input values used:**
- `{{transformation_rule}}` = "Filter out records where consent_flag is False or null before writing to Silver layer"
- `{{source_layer}}` = Bronze
- `{{target_layer}}` = Silver
- `{{partition_column}}` = market_code

**Output quality:** Output was usable as-is — Codex generated a correctly named function `apply_consent_filter` with explicit `isNotNull()` check, Google-style docstring, and a single inline comment explaining the consent logic; no revision was needed.

---

# No peer review as I have an individual plan
## Peer Review

**Reviewer:** [Name — Role]  
**Date reviewed:** YYYY-MM-DD  
**Model used by reviewer:** [Model name]

**Reviewer input values used:**
- `{{transformation_rule}}` = [value reviewer used]
- `{{source_layer}}` = [value reviewer used]
- `{{target_layer}}` = [value reviewer used]
- `{{partition_column}}` = [value reviewer used]

| Review question | Reviewer answer |
|----------------|-----------------|
| Could you run the template without asking the author anything? | Yes / No — [one sentence] |
| Was the output format what you expected? | Yes / No — [one sentence] |
| Would you use this template on your own work? | Yes / No — [one sentence] |
| One concrete improvement suggestion | [One sentence] |

---

## Revision History

| Version | Date | Change | Author |
|---------|------|--------|--------|
| 1.0 | 2026-06-08 | Initial commit | Anastazja |
| 1.1 | YYYY-MM-DD | Post-review update | [Name] |
