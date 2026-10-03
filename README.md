# Simple Calculator

A small command-line calculator written in Python. It asks for two numbers and an operator, then prints the result of the operation.

## Features

- Supports addition (`+`), subtraction (`-`), multiplication (`*`) and division (`/`)
- Works with whole numbers and decimals
- Handles division by zero without crashing
- Reports invalid operators

## Requirements

- Python 3.x (no external libraries needed)

## How to Run

1. Save the code in a file named `calculator.py`.
2. Open a terminal in the folder containing the file.
3. Run:

   ```bash
   python calculator.py
   ```

## Example Usage

```
Enter first number: 12
Enter operator (+, -, *, /): *
Enter second number: 4
Result: 48.0
```

```
Enter first number: 10
Enter operator (+, -, *, /): /
Enter second number: 0
Error! Division by zero.
```

```
Enter first number: 5
Enter operator (+, -, *, /): %
Enter second number: 2
Invalid operator
```

## Step-by-Step Explanation

### 1. Defining the function

```python
def calculator():
```

`def` creates a function named `calculator`. Everything indented below it is the body of the function. Wrapping the logic in a function keeps the code organized and lets you call it again whenever you need it.

### 2. Taking the first number

```python
num1 = float(input("Enter first number: "))
```

- `input("Enter first number: ")` shows the prompt and waits for the user to type something. It always returns a **string**.
- `float(...)` converts that string into a decimal number, so `"5"` becomes `5.0` and `"2.5"` stays `2.5`.
- The result is stored in the variable `num1`.

### 3. Taking the operator

```python
op = input("Enter operator (+, -, *, /): ")
```

The user types one of the symbols `+`, `-`, `*` or `/`. It is kept as a string in `op`, since it is a symbol and not a number.

### 4. Taking the second number

```python
num2 = float(input("Enter second number: "))
```

Works exactly like step 2, and stores the second value in `num2`.

### 5. Choosing the operation with `if / elif / else`

The program checks the value of `op` from top to bottom and runs only the first matching block.

**Addition**
```python
if op == "+":
    print("Result:", num1 + num2)
```
If `op` is `"+"`, it prints the sum. Note that `==` *compares* values, while a single `=` *assigns* them.

**Subtraction**
```python
elif op == "-":
    print("Result:", num1 - num2)
```
Runs only if the first check failed and `op` is `"-"`.

**Multiplication**
```python
elif op == "*":
    print("Result:", num1 * num2)
```
Prints the product of the two numbers.

**Division (with a safety check)**
```python
elif op == "/":
    if num2 == 0:
        print("Error! Division by zero.")
    else:
        print("Result:", num1 / num2)
```
Dividing by zero is mathematically undefined and would crash Python with a `ZeroDivisionError`. So there is a nested `if`:
- If `num2` is `0`, print an error message.
- Otherwise, perform the division and print the result.

**Invalid operator**
```python
else:
    print("Invalid operator")
```
If `op` matched none of the four symbols above, this fallback message is shown.

### 6. Calling the function

```python
calculator()
```

Defining a function does not run it. This last line actually executes `calculator()`, starting the whole process.

## Known Limitations

- **Non-numeric input crashes the program.** Typing `abc` instead of a number raises a `ValueError` because `float()` cannot convert it.
- **Runs only once.** After one calculation the program exits.
- **Results are always floats.** `2 + 2` prints `4.0`, not `4`.

## Possible Improvements

- Wrap the inputs in `try / except ValueError` to handle bad input gracefully.
- Use a `while True` loop so the user can do multiple calculations, with an option to quit.
- Add more operators such as `%` (modulus), `**` (power) or `//` (floor division).
- Format output to drop the trailing `.0` for whole numbers.

