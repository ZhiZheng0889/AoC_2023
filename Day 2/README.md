# Advent of Code 2023 - Day 2: Cube Conundrum

This repository contains a Python script that solves the Advent of Code 2023 Day 2 puzzle. The puzzle involves analyzing several games where cubes of different colors (red, green, and blue) are drawn from a bag. The goal is to determine which games are possible given a specific bag configuration and to calculate the "power" of the minimum set of cubes required for each game.

## Problem Summary

The puzzle consists of two parts:

1. **Part 1:** Determine which games would have been possible if the bag contained only 12 red cubes, 13 green cubes, and 14 blue cubes. The task is to sum the IDs of all such possible games.

2. **Part 2:** For each game, find the minimum number of cubes of each color that must have been in the bag to make the game possible. The power of a set of cubes is defined as the product of the number of red, green, and blue cubes. The task is to sum the power of these minimum sets across all games.

## Code Explanation

### `parse_game(game)`

- **Purpose:** This function parses the input data for a single game and extracts:
  - The game ID.
  - The maximum number of red, green, and blue cubes required to satisfy the game's conditions.
  
- **Input:** A string representing a game (e.g., `"Game 1: 3 blue, 4 red; 1 red, 2 green, 6 blue; 2 green"`).

- **Output:** A tuple `(game_id, max_red, max_green, max_blue)`, where:
  - `game_id` is the numeric ID of the game.
  - `max_red`, `max_green`, `max_blue` are the maximum counts of red, green, and blue cubes shown in any round of the game.

- **Process:**
  1. The game string is split into the game ID and the list of rounds.
  2. Regular expressions are used to identify and extract number-color pairs.
  3. The function tracks the maximum count for each color across all rounds.
  4. It returns the game ID and the maximum required cubes for each color.

### `solve_part1(file_path)`

- **Purpose:** This function identifies all possible games that can be played with a bag containing exactly 12 red, 13 green, and 14 blue cubes, and sums their IDs.

- **Input:** The path to the input file containing the game data.

- **Output:** An integer representing the sum of the IDs of all possible games.

- **Process:**
  1. The input file is read line by line.
  2. Each game is parsed using `parse_game()` to determine the maximum number of cubes required for each color.
  3. If a game can be played within the specified limits (12 red, 13 green, 14 blue), its ID is added to the total sum.
  4. The total sum is returned.

### `solve_part2(file_path)`

- **Purpose:** This function calculates the sum of the "power" of the minimum set of cubes required for each game.

- **Input:** The path to the input file containing the game data.

- **Output:** An integer representing the sum of the power of the minimum sets of cubes for all games.

- **Process:**
  1. The input file is read line by line.
  2. Each game is parsed using `parse_game()` to determine the maximum number of cubes required for each color.
  3. The "power" is calculated as the product of the maximum number of red, green, and blue cubes.
  4. The power for each game is added to the total power sum.
  5. The total power sum is returned.
