# NHL Shot Prediction - Data Sources

This directory contains the data used for NHL shot prediction analysis. Due to size limitations on GitHub, this repository contains only sample datasets. Full datasets are available via the links below.

## Data Overview

The project utilizes three primary datasets collected from the NHL API for the 2024-2025 season:

1. **Play-by-Play Data** (`nhl_play_by_play_full_season.csv`)
   - Contains detailed event-level data for every completed game
   - Includes shot attempts, goals, penalties, faceoffs, and other in-game events
   - Each event is timestamped and contains contextual information

2. **Player Box Scores** (`nhl_player_box_scores_full_season.csv`)
   - Contains individual player statistics for each game
   - Includes metrics like TOI (time on ice), shots, goals, assists, etc.
   - Each record is linked to both player and game IDs

3. **Team Box Scores** (`nhl_team_box_scores_full_season.csv`)
   - Contains team-level performance metrics for each game
   - Includes shots, goals, powerplay performance, etc.
   - Each record is identified by unique game and team IDs

## Data Collection Process

All data is collected directly from the NHL API using custom Python scripts:

- **Initial Collection**: A comprehensive script pulled all available data from the start of the 2024-2025 season through the project initialization date.
- **Daily Updates**: An automated script runs each morning to gather data from the previous day's games and append it to the existing datasets.

This approach ensures that the analysis is always working with the most current data available, allowing for real-time insights into ongoing season trends.

## Data Consistency and Relationships

All three datasets share consistent identifiers:
- Game IDs are uniform across all datasets
- Player IDs in the box score data correspond to player references in the play-by-play data
- Team IDs are consistent throughout all datasets

This schema allows for seamless joining of data across different granularity levels, enabling both micro (event-level) and macro (game-level) analysis.

## Accessing Complete Datasets

The complete datasets are available at this [Google Drive link](INSERT_YOUR_LINK_HERE). To use these datasets with the repository code:

1. Download all three CSV files
2. Place them in the `data/raw/` directory of your local repository clone
3. Run the notebooks or analysis scripts as directed in the main README

## Data Update Instructions

If you wish to update the data with the latest games:

1. Ensure you have the required dependencies installed (`pip install -r requirements.txt`)
2. Run the daily update script: `python scripts/data_collection/daily_update.py`
3. The script will automatically detect the most recent data in your files and update accordingly

## Sample Data

This repository contains the first 200 rows of each dataset to demonstrate their structure. These samples are located in the `data/raw/samples/` directory.

## Additional Notes

- The NHL API occasionally changes structure. The collection scripts have been designed to handle common inconsistencies, but significant API changes may require script updates.
- All timestamps are in UTC. Game times are converted to local time zones when necessary in the analysis.
- Missing values are denoted by `NaN` in the datasets and are handled appropriately in the analysis code.