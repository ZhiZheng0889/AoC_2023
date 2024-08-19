# Advent of Code 2023 - Day 3: Gear Ratios

This repository contains a Python script that solves the Advent of Code 2023 Day 3 puzzle. The puzzle involves analyzing a grid of numbers and symbols to calculate specific sums related to "part numbers" and "gears" in an engine schematic.

## Problem Summary

The puzzle consists of two parts:

1. **Part 1:** Identify and sum all numbers in the grid that are adjacent to any symbol (other than a period `.`). Numbers can be adjacent horizontally, vertically, or diagonally.

2. **Part 2:** Calculate the sum of products of pairs of numbers that are adjacent to a specific symbol (`*`). A gear (denoted by `*`) is defined as being adjacent to exactly two numbers. The gear ratio is the product of these two numbers.

## Code Explanation

### Part 1: Sum of Numbers Adjacent to Any Symbol

1. **Reading the Input:**
   - The input grid is read from a file named `AoC_2023_Day3.txt` and stored as a list of strings, where each string represents a line in the grid.

2. **Extracting Numbers and Symbols:**
   - The script identifies all numbers in the grid along with their coordinates using regular expressions.
   - Similarly, it identifies all symbols (any character that is not a digit or a period) and stores their coordinates.

3. **Calculating the Sum:**
   - The script checks if any part of a number is adjacent to any symbol. If so, it adds the number to the total sum.
   - The adjacency is determined by checking if the coordinates of a number and a symbol differ by no more than 1 in either direction (horizontally, vertically, or diagonally).

### Part 2: Sum of Gear Ratios

1. **Identifying Gears:**
   - The script first locates all `*` symbols in the grid and prepares to store the numbers adjacent to each `*`.

2. **Associating Numbers with Gears:**
   - For each number, the script checks if it is adjacent to any `*`. If a number is adjacent to a `*`, it is added to that `*`'s list of adjacent numbers.

3. **Calculating the Gear Ratios:**
   - For each `*`, if exactly two numbers are adjacent to it, their product is calculated and added to the total sum of gear ratios.
