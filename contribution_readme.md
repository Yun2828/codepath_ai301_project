# Contribution [1]: Math parity pyspark

**Contribution Number:** 1
**Student:** Yun
**Issue:** [github.com/Yun2828/Daft](https://github.com/Yun2828/Daft)
**Status:** Phase I, II, III, IV Complete

## Why I Chose This Issue

I chose this issue because it connects to my interest in making machine learning models faster, smaller, and more efficient for real-world inference. PyTorch AO focuses on model optimization techniques like quantization, which can reduce memory usage and improve inference performance. Since I am interested in LLM inference optimization, this issue gives me a beginner-friendly way to start learning how production ML libraries document and support modern quantization workflows.

This issue also feels like a good fit for my current skill level because it is documentation-focused but still technical. I do not need to write CUDA kernels or run large GPU benchmarks, but I do need to understand the difference between the deprecated AQT workflow and the newer quantize_ API. Through this contribution, I hope to learn more about PyTorch AO, quantization concepts, open-source documentation practices, and how maintainers guide users toward current best practices.

---

## Understanding the Issue

### Problem Description

Adding math expression that is featuer parity with pyspark.

## Reproduction Process

### Environment Setup

Created virtual enviroment and install dependencies.

### Steps to Reproduce

1. Followed the instruction on claude.md and readme.md

### Reproduction Evidence

- **Commit showing reproduction:** [github.com/Yun2828/Daft](https://github.com/Yun2828/Daft)
- **My findings: There's a similar functions that does the same thing as I was trying to do.**

---

## Solution Approach

### Analysis

Need to add two new math expression.

### Proposed Solution

Write the expression and tests.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** Write two expressions.

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]

1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [X] Test case 1: [Description]
- [X] Test case 2: [Description]
- [ ] Test case 3: [Description]

## Pull Request

**PR Link:** [github.com/Eventual-Inc/Daft/pull/7209](https://github.com/Eventual-Inc/Daft/pull/7209)

**PR Description:**

## Description

Add PySpark-parity aliases to_degrees and to_radians for Daft's existing degrees and radians functions, using snake_case naming. They delegate to the already-registered builtins, reusing the existing Rust kernels.

Related to [#3793](https://github.com/Eventual-Inc/Daft/issues/3793)

## Changes Made

Adds to_degrees and to_radians as PySpark-parity aliases for Daft's existing degrees and radians math functions, using Daft's snake_case naming convention (per [#3793](https://github.com/Eventual-Inc/Daft/issues/3793): "should all be snake_case instead of pyspark's mixed casing").

* to_degrees is an alias for degrees (converts radians → degrees)
* to_radians is an alias for radians (converts degrees → radians)

These are thin wrappers that delegate to the already-registered degrees/radians builtins, so they reuse the existing Rust kernels — no new math kernel and no Rust changes are needed.

Files changed:

* daft/functions/numeric.py — new to_radians/to_degrees functions delegating to radians/degrees
* daft/functions/ **init** .py — import the new functions and add them to **all**
* daft/expressions/expressions.py — Expression.to_radians() / Expression.to_degrees() methods for chaining (e.g. col("a").to_degrees())
* daft/series.py — matching Series.to_radians() / Series.to_degrees() methods
* tests/recordbatch/numeric/test_numeric.py — test_table_numeric_to_degrees_to_radians_aliases, asserting the aliases produce identical results to the functions they alias

Testing: New test passes; the full tests/recordbatch/numeric/test_numeric.py and tests/expressions/test_expressions.py suites pass (509 tests) under DAFT_RUNNER=native.

Note: Since these are aliases, an expression like col("a").to_degrees() reprs as its canonical builtin name degrees(col(a)). This is intentional (both resolve to the same registered function), so the aliases are deliberately umpy-drivenparametrized trig tests and covered by a dedicated equivalence t
Question for snake_casePython API (function + Expression/Series methods). Does the Spark Conmatically fromthe function registry, or should I also wire a toDegrees/toRs mapping tofully close out the Spark Connect parity aspect of the issue?

## Related Issues

Related to [#3793](https://github.com/Eventual-Inc/Daft/issues/3793)

**Maintainer Feedback:**

- The original issue is meant to be feature parity with pyspark. It is not intended to replicate the exact pyspark apis.

**Status:** Closed

---

## Learnings & Reflections

### Technical Skills Gained

Learned how to use python API.

### Challenges Overcome

Understanding the codebase.

### What I'd Do Differently Next Time

Pay more attention to understanding the problem.

---

## Resources Used

- [github.com/Yun2828/Daft](https://github.com/Yun2828/Daft)
