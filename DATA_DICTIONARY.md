# Data Dictionary

This document defines the fields in each JSON record. Preserve the stated key order at every level.

## Top-level fields

| Field | Type | Meaning |
|---|---|---|
| `pair_id` | string | Unique identifier for the record; corresponds to the JSON file name. |
| `causal_structure_type` | enum string | Cause/effect structure. Allowed values: `single_cause_single_effect`, `multi_cause_single_effect`. |
| `is_self_causal` | boolean | Whether a cause explicitly mentions the focal company. |
| `causes` | array of Cause objects | Events annotated as causes of the effect; at least one is required. |
| `effects` | array of Effect objects | Outcome events associated with the cause; typically one. |
| `causal_reasoning_chain` | array of ReasoningStep objects | Ordered steps describing the proposed mechanism from cause to effect. |
| `rationale` | string | Evidence-grounded explanation of the proposed cause–effect link. |
| `counterfactual_analysis` | string | Assessment of the likely outcome if the cause were absent or different. |
| `adversarial_confounders` | array of Confounder objects | Alternative explanations that could contribute to the observed effect. |
| `confidence_score` | number, 0–1 | Annotator's overall confidence in the attribution; at most two decimal places. |
| `reasoning_type` | string | Category of the main mechanism connecting cause and effect. |
| `business_models` | array of BusinessModel objects | Structured analysis using an allowed business or systems framework. |
| `license` | object | License name and URL associated with the record. |

## Cause object

Key order: `source_doc_id`, `causal_salience`, `text`, `date`, `entities`, `sectors`, `country`, `sentiment`, `source_info`, `causal_strength_score`.

| Field | Type | Meaning |
|---|---|---|
| `source_doc_id` | string or null | Stable source-document identifier. Null indicates that no internal identifier is available. |
| `causal_salience` | enum string | Relative importance of the cause: `primary` or `secondary`. A record with multiple causes has exactly one primary cause. |
| `text` | string | Specific description of the causal event and its relevant mechanism. |
| `date` | ISO date string | Date of the cause event, formatted `YYYY-MM-DD`. |
| `entities` | array of strings | Named entities implicated in the cause event. |
| `sectors` | array of strings | Industry or domain categories relevant to the cause. |
| `country` | string | Country most relevant to the cause event. |
| `sentiment` | Sentiment object | Sentiment direction, intensity, and target associated with the cause. |
| `source_info` | SourceInfo object | Bibliographic metadata for the source article. |
| `causal_strength_score` | integer, 1–10 | Annotator's assessment of the cause's contribution to the effect. |

## Effect object

Key order: `text`, `date`, `entities`, `sectors`, `country`, `effect_type`, `impact_direction`, `impact_strength_score`, `direct_or_indirect`, `sentiment`, `stock_change_pct`, `stock_change_direction`, `source_info`.

| Field | Type | Meaning |
|---|---|---|
| `text` | string | Specific description of the observed outcome. |
| `date` | ISO date string | Date of the effect event; it must be later than every cause date and within the protocol's maximum cause–effect interval. |
| `entities` | array of strings | Named entities affected by the effect. |
| `sectors` | array of strings | Industry or domain categories relevant to the effect. |
| `country` | string | Country most relevant to the effect. |
| `effect_type` | string | Category of the outcome event. |
| `impact_direction` | enum string | Effect direction: `positive`, `negative`, `mixed`, or `neutral`. |
| `impact_strength_score` | integer, 1–10 | Assessment of the effect's magnitude, coverage, and persistence. For stock movements, follow the protocol's percentage bands. |
| `direct_or_indirect` | enum string | Transmission path: `direct` or `indirect`. |
| `sentiment` | Sentiment object | Sentiment direction, intensity, and target associated with the effect. |
| `stock_change_pct` | number | Signed percentage change in stock price for a stock-movement effect. |
| `stock_change_direction` | enum string | Stock-price direction: `up` or `down`; it must agree with the sign of `stock_change_pct`. |
| `source_info` | SourceInfo object | Bibliographic metadata for the source article. |

## Sentiment object

Key order: `direction`, `intensity`, `target`.

| Field | Type | Meaning |
|---|---|---|
| `direction` | enum string | Sentiment polarity: `positive`, `negative`, or `neutral`. |
| `intensity` | number, 0–1 | Strength of the sentiment; at most two decimal places. |
| `target` | string | Entity or group toward which the sentiment is directed. |

## SourceInfo object

Key order: `title`, `url`, `published_date`, `publisher`.

| Field | Type | Meaning |
|---|---|---|
| `title` | string | Title of the cited source article. |
| `url` | string | Canonical source URL with tracking parameters removed. |
| `published_date` | ISO date string | Date the source article was published. |
| `publisher` | string | Name of the source publisher. |

The event `date` and source `published_date` are different fields: event dates determine cause–effect chronology; publication dates describe the source article.

## ReasoningStep object

Key order: `step_id`, `description`, `logic_operator`.

| Field | Type | Meaning |
|---|---|---|
| `step_id` | integer | Position of the step in the reasoning chain. |
| `description` | string | Mechanistic statement describing a transition or event in the chain. |
| `logic_operator` | enum string | Relationship between steps: `cause_event`, `AND`, `THEN`, or `RESULT`. |

## Confounder object

Key order: `text`, `impact`.

| Field | Type | Meaning |
|---|---|---|
| `text` | string | Alternative explanation that could contribute to the effect. |
| `impact` | string | Channel through which the alternative explanation may affect the outcome. |

## BusinessModel object

Key order: `model`, `details`. Allowed models: `PorterFiveForces`, `PESTEL`, and `SystemDynamics`.

| Model | `details` key order | Field meanings |
|---|---|---|
| `PorterFiveForces` | `force`, `role_in_chain`, `industry_barriers`, `commentary` | Competitive force; its role in the causal chain; barrier level (`low`, `medium`, or `high`); mechanism commentary. |
| `PESTEL` | `pestel_factor`, `pestel_impact_score`, `conditions_score`, `commentary` | Relevant PESTEL factor; impact score; enabling-conditions score; mechanism commentary. |
| `SystemDynamics` | `feedback_loop_type`, `time_delay`, `conditions_score`, `commentary` | Feedback-loop category; delay in days; conditions score; mechanism commentary. |

Business-model scores use the 0–1 scale with at most two decimal places. The `time_delay` field is written as a number of days.

## License object

Key order: `name`, `url`.

| Field | Type | Meaning |
|---|---|---|
| `name` | string | Name of the license applied to the record. |
| `url` | string | URL for the license terms. |

## General conventions

- Dates use `YYYY-MM-DD`.
- Every effect date is later than all cause dates and within the permitted cause–effect interval.
- 0–1 scores use at most two decimal places; strength scores are integers from 1 to 10.
- Cause and effect use distinct source articles.
- Source URLs should be canonical and directly reachable where possible.
- For stock movements, the percentage sign, direction, impact direction, and impact-strength score must be consistent.
