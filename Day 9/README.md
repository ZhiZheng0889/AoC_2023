# Sequence Extrapolation Script

## Overview

This script extrapolates the next and previous values in a sequence of numbers using a mathematical technique called Lagrange interpolation. It calculates the sum of these extrapolated values for a given list of sequences.

## How It Works

### 1. **Input:**

- **Concept:** The script begins by processing a series of number sequences. These sequences are provided as lines of space-separated integers. For example, each line might represent a progression like `1 2 3 4` or `10 20 30 40`.
  
- **Purpose:** Each sequence represents a set of numbers from which the script will extrapolate additional values—either predicting the next number in the sequence (as if the series continues) or the previous number (as if we're looking back before the sequence started).

- **Process:** The script reads each line, treats it as a distinct sequence of numbers, and prepares to calculate the extrapolated values for both the next and previous terms.

### 2. **Lagrange Interpolation:**

- **Mathematical Foundation:** The script uses Lagrange interpolation, a method that allows you to construct a polynomial passing through a given set of points. In this case, the points are the numbers in the sequence.

- **Extrapolation:**
  - **Next Value Prediction:** The script uses Lagrange interpolation to extend the sequence by predicting the next number that logically follows the sequence provided. This is useful when you want to know what comes next based on the existing trend.
  
  - **Previous Value Estimation:** Conversely, the script can also estimate what the sequence might have been before the first number you know. This involves calculating the value that would logically precede the first number in the sequence.

- **Calculation Process:** The script systematically computes the contributions of each number in the sequence to build the interpolation polynomial. This polynomial is then evaluated to predict the next or previous number. The interpolation involves adjusting the sign of certain terms and using combinations of the sequence length and index positions to determine the weight of each contribution.

### 3. **Output:**

- **Summing the Extrapolated Values:**
  - After calculating the next and previous values for each sequence, the script sums these extrapolated values across all sequences.
  - **Part 1:** The script outputs the total sum of all predicted "next" values. This gives a cumulative figure representing all the extrapolated future numbers based on the sequences provided.
  - **Part 2:** Similarly, the script calculates and outputs the total sum of all estimated "previous" values, representing the cumulative figure of all numbers that would logically precede the given sequences.

### Summary:

In essence, the script takes a list of numerical sequences and, using the mathematical technique of Lagrange interpolation, predicts both the next and previous numbers in these sequences. It then sums these predictions to provide a total for both future (next) and past (previous) extrapolations. This approach can be particularly useful in scenarios where you want to extend a series of numbers or fill in missing values before the known sequence begins.



