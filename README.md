# Learning Verifiable Financial Formulas from Templates

**Hybrid symbolic solving for FinReason Cup 2026 — Task 1**  
**Author:** Umar Tabbsum · **Team:** `ut1776`

This project explores whether arithmetic formulas behind templated financial questions can be learned from labeled examples rather than hand-written one template at a time. The system fingerprints question templates, searches a bounded arithmetic grammar, reuses learned intermediate steps, verifies candidate expressions with exact rational arithmetic, and abstains when it cannot find a supported program.

## Reported results

| Measure | Result |
|---|---:|
| Held-out seen-template questions answered correctly | 191 / 290 |
| Precision among answered held-out questions | 99.5% |
| Reasoning steps matched | 332 / 518 |
| Official test questions answered | 406 / 928 |
| Official test questions correct | 377 / 928 |
| Combined final-answer score | 0.336 |
| Official rank | 27 / 27 |
| Hidden-template score | 0.055 |

These are results reported in the paper, not independent reproduction results. The high held-out precision applies to questions the system chose to answer from seen templates; it should not be mistaken for overall test performance.

## Method

1. Fingerprint question text by masking numeric values and retaining trace-slot identifiers.
2. Extract numeric leaves and represent values exactly.
3. Search a bounded arithmetic grammar using value signatures and meet-in-the-middle matching.
4. Reuse learned intermediate steps in later expressions.
5. Verify accepted expressions with rational arithmetic and format to the answer specification.
6. Abstain if no supported formula is found.

## Limitations

Exact arithmetic checks the expression that was recovered; it does not prove that the expression is the intended rule for arbitrary unseen inputs. A template-level learner cannot automatically solve templates with no labeled examples. The paper reports substantially weaker hidden-template performance and an official rank of 27/27.

The archived scripts include absolute paths such as `/home/claude/...` and depend on the organizers' `finreason_task1` package and data layout. They are not yet a turnkey, independently reproducible package.

## Explore

- [Research presentation](./index.html)
- [Methodology and reproducibility notes](./docs/METHODOLOGY.md)
- [Source repository](https://github.com/u19725505-star/finreason-verifiable-financial-formulas)

The paper, selected source files, figures, and reviewed result tables will be added in a separate import. Organizer datasets, submission artifacts, registration records, email correspondence, and IEEE administrative documents are deliberately excluded pending rights and privacy review.

## Citation

Umar Tabbsum, “Learning Verifiable Financial Formulas from Templates: Hybrid Symbolic Solving for FinReason Cup 2026, Task 1.”

No license has been selected. Reuse rights should not be assumed.
