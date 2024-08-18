### Documentation: Why the Code Works

#### Overview
The code provided is designed to solve the puzzle from Day 3 of Advent of Code 2023. The puzzle involves processing a grid of characters to identify numbers adjacent to specific symbols, and then performing calculations based on these numbers. The solution is split into two parts: Part 1 calculates the sum of numbers adjacent to any symbol, while Part 2 calculates the sum of products of numbers adjacent to the `*` symbol.

#### Part 1: Summing Numbers Adjacent to Symbols

1. **Reading the Input:**
   - The input grid is read from a text file and split into lines to create a grid-like representation where each line corresponds to a row in the grid.

2. **Identifying Numbers and Symbols:**
   - **Numbers:** The code uses regular expressions to find all multi-digit numbers in each line of the grid. These numbers are stored along with their exact coordinates (row and column positions).
   - **Symbols:** Similarly, the code identifies all symbols that are neither digits nor periods (`.`) and records their coordinates. This includes symbols such as `*`, `#`, `+`, `$`, and others.

3. **Checking Adjacency:**
   - For each number identified in the grid, the code checks if any part of the number is adjacent to any symbol. Adjacency is defined as being horizontally, vertically, or diagonally next to a symbol.
   - This check is performed by comparing the coordinates of each digit in the number with the coordinates of each symbol.

4. **Calculating the Sum:**
   - If a number is found to be adjacent to any symbol, it is included in the sum.
   - The sum of all such adjacent numbers is calculated and output as the result for Part 1.

#### Part 2: Summing Products of Pairs of Numbers Adjacent to the `*` Symbol

1. **Identifying `*` Positions:**
   - The code specifically searches for the `*` symbol in the grid and records its position. Each `*` symbol is also associated with an empty list that will later store adjacent numbers.

2. **Checking Adjacency to `*`:**
   - The code checks each number in the grid to see if it is adjacent to any `*` symbol.
   - If a number is adjacent to a `*` symbol, it is added to the list of numbers associated with that `*`.

3. **Calculating the Product Sum:**
   - The code then checks each `*` symbol to see if exactly two numbers are adjacent to it.
   - For each `*` symbol with two adjacent numbers, the code multiplies these two numbers and adds the product to a running total.
   - The final sum of these products is calculated and output as the result for Part 2.

#### Why the Code Works

- **Effective Use of Regular Expressions:** The code utilizes regular expressions to accurately identify multi-digit numbers and symbols, ensuring that even complex cases are handled correctly.

- **Coordinate-Based Adjacency Check:** By storing and comparing the coordinates of numbers and symbols, the code effectively determines adjacency. This method is reliable and works for any grid configuration, including edge and corner cases.

- **Error Handling in Multiplication:** The code ensures that all strings representing numbers are converted to integers before performing any mathematical operations. This prevents type errors and guarantees that the calculations are performed correctly.

- **Comprehensive Coverage:** The code is designed to handle a variety of symbols and grid sizes, making it robust and adaptable to different input scenarios. It accurately solves the puzzle by considering all possible cases where numbers and symbols can interact.

This approach ensures that the code provides correct results for both Part 1 and Part 2 of the Advent of Code Day 3 puzzle, demonstrating the accuracy and efficiency of the solution.
