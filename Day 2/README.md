import re

def parse_game(game):
    """
    Parse a game's data and return the game ID and the maximum number of red, green, and blue cubes required.

    Parameters:
    - game (str): A string representing the game data (e.g., "Game 1: 3 blue, 4 red; 1 red, 2 green, 6 blue; 2 green").

    Returns:
    - tuple: (game_id, max_red, max_green, max_blue), where:
      - game_id is the ID of the game.
      - max_red, max_green, max_blue are the maximum number of red, green, and blue cubes required in any subset of the game.
    """
    # Split the game string into the ID and the rounds
    game_id, rounds = game.split(": ")
    game_id = int(game_id.split()[1])  # Extract the game ID as an integer

    # Initialize maximum required cubes for each color
    max_red = 0
    max_green = 0
    max_blue = 0

    # Extract all the number-color pairs from the rounds
    rounds = re.findall(r'(\d+) (\w+)', rounds)

    # Iterate through each number-color pair and update the max values
    for count, color in rounds:
        count = int(count)
        if color == "red":
            max_red = max(max_red, count)  # Update max_red if the current count is higher
        elif color == "green":
            max_green = max(max_green, count)  # Update max_green if the current count is higher
        elif color == "blue":
            max_blue = max(max_blue, count)  # Update max_blue if the current count is higher

    return game_id, max_red, max_green, max_blue

def solve_part1(file_path):
    """
    Solves Part 1: Finds the sum of the IDs of all possible games.

    Parameters:
    - file_path (str): The path to the input file containing the game data.

    Returns:
    - int: The sum of the IDs of games that are possible with the given cube limits.
    """
    # Define the cube limits for Part 1
    red_limit = 12
    green_limit = 13
    blue_limit = 14

    total_sum = 0  # Initialize the total sum of valid game IDs

    with open(file_path, 'r') as file:
        # Process each line (game) in the input file
        for line in file:
            # Parse the game to get the ID and the max required cubes for each color
            game_id, max_red, max_green, max_blue = parse_game(line.strip())

            # Check if the game is possible under the given limits
            if max_red <= red_limit and max_green <= green_limit and max_blue <= blue_limit:
                total_sum += game_id  # Add the game ID to the total sum if valid

    return total_sum

def solve_part2(file_path):
    """
    Solves Part 2: Finds the sum of the power of the minimum sets of cubes required for each game.

    Parameters:
    - file_path (str): The path to the input file containing the game data.

    Returns:
    - int: The sum of the power of the minimum sets of cubes for all games.
    """
    total_power_sum = 0  # Initialize the total sum of the power of cube sets

    with open(file_path, 'r') as file:
        # Process each line (game) in the input file
        for line in file:
            # Parse the game to get the ID and the max required cubes for each color
            game_id, max_red, max_green, max_blue = parse_game(line.strip())

            # Calculate the power of the cube set (product of the min cubes required)
            power = max_red * max_green * max_blue

            # Add the power to the total power sum
            total_power_sum += power

    return total_power_sum

# File path to the input
file_path = '/content/AoC_2023_Day2.txt'

# Solve Part 1
part1_result = solve_part1(file_path)
print("Part 1: The sum of the IDs of possible games is:", part1_result)

# Solve Part 2
part2_result = solve_part2(file_path)
print("Part 2: The sum of the power of these sets is:", part2_result)

