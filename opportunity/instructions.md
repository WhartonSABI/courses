# Assignment: World Hockey League Analytics

## Background
The World Hockey League (WHL) is a 32-team international league. The regular season has ended, and the league is preparing for a single-elimination tournament. Your task is to use regular season data to evaluate team strength, estimate matchup probabilities, and explain which factors appear to matter most.

## Files to Use
- `season_box.csv`: team-level game box scores, including power-play opportunities, minutes, goals, and `xG`
- `league_table.csv`: the final regular-season standings
- `first_round_matchups.csv`: the seeded first-round playoff bracket

## Reading the Data
To help you interpret the box score and standings:
- `goals` are the number of times a team scored.
- `assists` are credited to players who helped create a goal.
- `penalties` last for 2 or 4 minutes and give the other team a power play.
- `power plays` are man-advantage situations created by penalties. In `season_box.csv`, power-play fields track opportunities, minutes, goals, and `xG`.
- `went_ot` indicates that a game went to overtime.
- `points` in `league_table.csv` are standings points: `2` for a win, `1` for an overtime loss, and `0` for a regulation loss.

# Your Tasks

## 1. Build a Team Power Rating
Create a power rating for all 32 teams using the season data. Your rating should be data-driven and should capture overall team strength.

Your method should consider useful inputs, such as:
- goal differential or `xG` differential
- strength of schedule
- goalie quality
- shot quality and shot volume
- home-ice advantage

Your final output should include:
- a ranking of all 32 teams from strongest to weakest
- one clear power rating for each team
- a visualization of your power rankings, included in your report or slide deck

## 2. Explain Your Method
Write a short explanation of what you did and why.

Be sure to address:
- which variables or features you used
- how you combined them into a single rating or model
- why your method makes sense for hockey
- what assumptions or simplifications you made

Your explanation should be clear enough for someone with an introductory background in statistics to understand.

## 3. Predict the First Round of the Tournament
Use the provided file `opportunity/first_round_matchups.csv`, which lists the first-round bracket based on the final league table.

For each of the 16 matchups, estimate the probability that the home team wins. Additionally, report how much this estimate would shift if the away team hosted instead.

Your final output should include the completed matchup table. You may use your power rating to estimate these probabilities.

## 4. Goaltending
Next, use the regular season data to rank goalkeepers. Include a visualization of goaltending skill in your report or slide deck, and briefly explain how you produced that ranking.

# Deliverables
Submit the following:
- a short report (`1-3` pages) or a slide deck summarizing your method and findings, including your power ranking and goaltending visuals
- your code or notebook
- a final table of team power ratings
- a completed `first_round_matchups.csv`
- a ranking of goalkeepers with a brief explanation of your method

# Evaluation
Entries will be judged on:
- clarity of method
- quality of reasoning
- effective use of data
- communication of results
- practical usefulness of the final predictions

The strongest submissions will combine thoughtful analysis with clear communication.
