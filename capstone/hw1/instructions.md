# Homework 1: NHL Expansion Draft Scouting

## Overview

You are an analyst for an NHL expansion team that is joining the league next season. Your General Manager has tasked you with scouting goalkeepers across the league to prepare for the upcoming expansion draft. You need to identify which goalies are performing well and which ones might be good targets for your team.

You have access to performance data from the first half of the current season. Your job is to:
1. Evaluate goalies based on their first half performance
2. Predict how they will perform in the second half of the season
3. Refine your evaluation by accounting for additional context

Your GM wants a full PDF report containing your findings and an explanation of the choices you made, with code included.

## Assignment Parts

### Part 1a: Initial Ranking Based on First Half Performance

Your first task is to create a ranking of goalie performance. Using the data in `1h_v1.csv`, rank all goalies based on their performance in the first half of the season.

**Key consideration:** Goalies have different sample sizes (games played). You must develop a ranking methodology that appropriately accounts for these differences.

**Deliverables:**
- A ranked list of all goalies from best to worst
- A clear explanation of your ranking methodology
- Discussion of how you handled the varying sample sizes

### Part 1b: Predicting Second Half Performance

Your second task is to predict the performance of each goalie in the second half of the season. Using the data in `1h_v1.csv`, make a forecast for each goalie's performance in the second half of the season. You may use any method you choose.

**Key considerations:** Your predictions should account for uncertainty and sample size differences. Consider how to handle goalies with different amounts of playing time.

**Deliverables:**
- Predicted goals per game for each goalie in the second half of the season
- A brief explanation of your prediction methodology
- Uncertainty estimates for your predictions (if applicable to your method)

### Part 2: Refining Rankings with Expected Goals

After a request to the league office, you've obtained additional data on the expected goals (xG) faced by each goalkeeper. Using this data, refine your ranking of goalkeepers from Part 1a. How does incorporating this additional context change your evaluation?

**Deliverables:**
- A refined ranking of goalies from best to worst
- Discussion of how these rankings differ from your previous rankings
- Analysis of which goalies are helped (or hurt) most by accounting for xG faced
- Interpretation of what these differences tell us about how we should be evaluating goalkeepers
- A recommendation: How does this change your scouting priorities? Which goalkeepers should our team consider drafting? Which goalkeepers might be undervalued by other teams?

## Submission Requirements

A written report (PDF) that includes:
1. Description of methodologies and any assumptions or limitations
2. Your results (rankings, predictions, comparisons)
3. Discussion and interpretation of results
4. Your final scouting recommendations for the expansion draft
5. Well-documented code integrated throughout the report (like in a markdown document)

## Questions?

If you have questions about this assignment, please reach out to your TAs.