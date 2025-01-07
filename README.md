# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common JavaScript closure issue that arises when using `setTimeout` within a loop.  The problem stems from how closures capture variables in their surrounding scope.  The expected behavior would be to print numbers from 0 to 9. However, due to the asynchronous nature of `setTimeout` and the way closures work, it actually prints the number 10 ten times.

## Setup

1. Clone the repository.
2. Open `bug.js` to see the buggy code.
3. Open `bugSolution.js` to see the corrected code.

## Explanation

The problem is that the `setTimeout` callbacks don't capture the value of `i` at the time they're created, but rather capture a reference to the variable `i`. By the time the `setTimeout` callbacks finally execute, the loop has already completed, and `i` is equal to 10.

## Solution

The solution involves using an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop, ensuring that each callback captures its own copy of `i`. This is the most common and recommended way to solve this.