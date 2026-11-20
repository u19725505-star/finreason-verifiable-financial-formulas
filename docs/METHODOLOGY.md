# Methodology and reproducibility notes

This note summarizes the camera-ready paper in the supplied archive. It does not claim the archived scripts have been independently rerun.

## Task

FinReason Cup 2026 Task 1 evaluates systems on templated financial questions with typed final answers and, where specified, intermediate reasoning slots. The paper describes 2,900 labeled training cases across 290 templates, 290 labeled local-development cases, 580 leaderboard-development questions, and 928 public test questions.

## Formula-learning pipeline

- **Fingerprinting:** replace numeric tokens in question text with placeholders and pair normalized text with trace-slot identifiers.
- **Numeric extraction:** parse values into exact fractions.
- **Candidate synthesis:** search a bounded arithmetic grammar with addition, subtraction, multiplication, division, exponentiation, minimum, and maximum. Candidate expressions are pruned using their values across labeled examples.
- **Intermediate-step reuse:** learned step expressions may become leaves for later step or final-answer expressions.
- **Verification:** evaluate accepted expressions using exact rational arithmetic, then format to the answer specification. Abstain if no supported expression is found.

The paper also describes value-signature pruning, meet-in-the-middle matching, rounding-aware comparison, and bounded expression-size search.

## Reported evaluation

| Measure | Result |
|---|---:|
| Held-out seen-template answers correct | 191 / 290 |
| Precision among answered held-out questions | 99.5% |
| Reasoning steps matched | 332 / 518 |
| Official test questions answered | 406 / 928 |
| Official test answers correct | 377 / 928 |
| Combined final-answer score | 0.336 |
| Official rank | 27 / 27 |
| Hidden-template score | 0.055 |

The full ablation configuration (n=10) reports 192 answered and 191 correct. The compared configuration without learned-step chaining reports 75 correct.

## Interpretation

Exact evaluation verifies the arithmetic of a recovered expression. It does not establish that the expression is the intended financial rule for arbitrary unseen inputs. The reported 99.5% precision applies only to answered held-out questions from seen templates, not to the entire test set.

The paper attributes the official result to incomplete coverage of known templates and weak performance on hidden templates. A template-level learner cannot, by itself, recover formulas for templates with no released examples.

## Reproduction status

Archived scripts refer to absolute paths under `/home/claude/`; some import the organizers' `finreason_task1` package and expect the organizer repository's data layout. Consequently, this is not yet a turnkey reproduction package. A clean environment, configurable paths, dependency declaration, and organizer-toolkit instructions are still needed.

The source archive also contains benchmark data, prediction files, submission packages, and administrative records. They are not included here pending review of redistribution terms and privacy.
