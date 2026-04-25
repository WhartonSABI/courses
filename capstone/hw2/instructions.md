# Homework 2: Did the Baseball Change?

## Overview

You’ve been hired by a sportsbook’s risk + integrity team. They suspect MLB may have quietly changed the baseball (or the ball supply) across seasons, altering how far well-hit balls travel and how often they become home runs.

You have access to pitch-tracking and batted-ball tracking measurements. Your job is to build an evidence-based case for or against the hypothesis that **the ball changed** (in a way that meaningfully affects outcomes), and quantify the size of the effect.

This assignment is intentionally open-ended, but it has **required deliverables**.

You may work **in teams of 2**.

## Data

Use the data in `hit-tracking.csv`.

### Scope

- The dataset spans **the 2015–2019 MLB seasons**.
- Within each `year`, `month` covers the months included in the sample.

### Dictionary

1. `year`
2. `month`
3. `pitcher_throws`: pitcher handedness (`L` or `R`)
4. `bat_side`: batter handedness (`L` or `R`)
5. `pitch_type`: `FF` = four-seam fastball, `FT` = two-seam fastball
6. `release_speed`: speed of the pitch **towards home plate** at 50 feet from home plate, in mph
7. `plate_speed`: speed of the pitch **as it crosses the front of home plate**, in mph
8. `hit_exit_speed`: exit velocity of the batted ball at contact, in mph (may be missing if no ball put in play)
9. `hit_spinrate`: batted-ball spin rate at contact, in rpm (may be missing)
10. `hit_vertical_angle`: launch angle (vertical plane), in degrees (may be missing)
11. `hit_bearing`: spray angle / bearing from the tip of home plate (horizontal plane), in degrees (may be missing)
12. `hit_distance`: distance from the tip of home plate to first landing point, in feet (may be missing)
13. `event_result`: categorical outcome text (examples include `home_run`, `field_out`, `single`, `double`, `force_out`, `hit_by_pitch`, etc.)

### Important Notes

- Not every row will have batted-ball measurements (`hit_*` fields). You must **explicitly handle missingness** and explain any filtering choices.
- If you claim “the ball changed,” you must also argue why your evidence is **not** just measurement noise, missingness artifacts, or a change in the mix of contact (exit velocities / launch angles) being sampled.

## Assignment Parts

### Part 0: Data Audit

Before modeling anything, get oriented in the dataset and identify the biggest pitfalls (missingness, selection, confounding).

- Summarize the dataset: row count, time coverage (`year`/`month`), counts by `pitch_type`, handedness, and `event_result`.
- Show a compact missingness summary for the contact fields (`hit_exit_speed`, `hit_spinrate`, `hit_vertical_angle`, `hit_bearing`, `hit_distance`), and comment on whether missingness appears to vary by `year`.
- Define the two outcomes you’ll analyze later:
  - A continuous “carry” outcome (e.g., `hit_distance` on balls where distance is observed)
  - A binary home run outcome: `is_home_run = 1` if `event_result == "home_run"`, else `0`

**Deliverables:**
- A short “data audit” section (keep it tight: 1–2 tables + 1 figure + 3–6 bullets).

### Part 1: Pitch Aerodynamics

The ball isn’t only hit; it’s also pitched. If the ball’s surface or drag properties changed, it could show up as changes in how pitches slow down on their way to the plate.

Use pitch-speed measurements to quantify pitch deceleration. Compute and analyze:

- Speed loss: \(\Delta v = \texttt{release\_speed} - \texttt{plate\_speed}\)

Then evaluate whether \(\Delta v\) changes across years after accounting for obvious factors (at least `pitch_type`; optionally handedness).

Important: you should also discuss alternative explanations (e.g., sampling changes, pitcher population changes, measurement changes) and what you can/can’t rule out with this dataset.

**Deliverables:**
- A plot showing the distribution of \(\Delta v\) overall and by year (optionally by `pitch_type`)
- A short conclusion: does pitch deceleration provide evidence consistent with a ball change?

### Part 2: Batted Ball Carry

Your client ultimately cares about whether batted balls appear to carry differently across years.

Do both of the following:

1. **Exploration:** Explore how `hit_distance` relates to other measurements, and how those relationships vary by `year`.
2. **Model:** Build **at least two** reasonable model specifications for `hit_distance` (e.g., a simple baseline vs a richer model), using any predictors you think are relevant (including transformations and interactions), including your Part 1 pitch deceleration metric \(\Delta v\).

Your modeling approach must support a comparison of carry **across years**, but how you do that is up to you.

If you use \(\Delta v\) from Part 1 in this model, explain *how* you incorporated it (e.g., as a per-pitch feature on the same row, or as an aggregated “year-level”/“pitch-type-by-year” feature joined back in).

Sensitivity requirement: report your “carry by year” conclusion under both model specifications. Discuss what changes and what stays the same.

Interpretation requirement: your final writeup must translate the model into a concrete effect statement about year-to-year differences (with uncertainty or a careful variability argument).

**Deliverables:**
- At least two figures that explain distance behavior (including a time comparison)
- A fitted model, diagnostics, and error reporting (e.g., RMSE/MAE on a held-out set)
- A brief justification of your predictor choices (including any transformations/interactions)
- A clear estimate of the “carry shift” by year with uncertainty or a careful variability argument

### Part 3: Home Run Probability

Distance is continuous, but the sportsbook ultimately cares about **home run rate**.

Build a model for the probability of a home run (e.g., threshold classifiers, logistic regression with optional regularization). Minimum requirements:

- Outcome: `is_home_run`
- Choose any other predictors you think are relevant (including transformations and interactions)
- Use a train/test split or cross-validation; describe your choice
- Report at least two evaluation views (examples: ROC AUC, log loss, calibration plot, confusion matrix at a chosen threshold)

Your modeling approach must support a comparison of home run probability **across years**, but how you do that is up to you.

Sensitivity requirement: report your “HR probability by year” conclusion under **at least two** reasonable model specifications (i.e., different feature sets). Discuss what changes and what stays the same.

Interpretation requirement: quantify the magnitude of any time-based shift in HR probability for a representative batted ball (e.g., EV=100 mph, LA=25°), and discuss uncertainty.

**Deliverables:**
- Model specification (features + preprocessing + training approach)
- A brief justification of your predictor choices (including any transformations/interactions)
- Performance metrics and at least one diagnostic plot
- A clear estimate of how predicted home run probability differs by year, with interpretation

### Part 4: Recommendation

Your report must end with an explicit, decision-oriented recommendation to the sportsbook:

- **Did the ball change?** (Yes / No / Inconclusive)
- **Evidence summary:** 3–6 bullets referencing your key figures/results
- **Estimated impact:** translate into something actionable (e.g., feet of carry, change in HR probability, what that implies for totals/props conceptually)
- **Risks & limitations:** what you can’t rule out (park effects, weather, selection bias, missingness, etc.) and what data you’d want next

**Deliverables:**
- A short executive summary section written for a non-technical stakeholder

## Submission Requirements

Submit a **single PDF report** that includes:

1. Your methodology, assumptions, and limitations
2. Results for Parts 0–4 (plots/tables + interpretation)
3. A final recommendation written for the sportsbook
4. Well-documented code integrated throughout (e.g., rendered notebook/report)

If working in a pair, include **both names** on the report and submit **one** combined solution.

## Questions?

If you have questions about this assignment, please reach out to your TAs.
