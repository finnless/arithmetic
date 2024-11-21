# Arithmetic Expression Parser and Transformer ![](https://github.com/finnless/arithmetic/workflows/tests/badge.svg)

A simple python library for manipulating arithmetic expressions.

This project implements a flexible arithmetic expression parser and transformer that demonstrates various ways to work with Abstract Syntax Trees (ASTs) using the Lark parsing library.

## Overview

Features:
1. Parsing arithmetic expressions with operator precedence
2. Expression evaluation
3. Expression minification
4. Conversion to Reverse Polish Notation (RPN)

## Key Components

### Grammar
The project uses a context-free grammar that supports:
- Basic arithmetic operations (+, -, *, /, %)
- Exponentiation (**)
- Parentheses for grouping
- Implicit multiplication (e.g., "2(3)" = "2*3")

### Interpreters and Transformers

1. **Interpreter**: Evaluates expressions using a top-down approach
   - Handles all arithmetic operations
   - Supports negative numbers and integer division
   - Processes the AST recursively from root to leaves

2. **Simplifier**: Alternative implementation using bottom-up transformation
   - Demonstrates how the same computation can be done with different traversal strategies
   - Generally simpler implementation due to Lark's Transformer class handling recursion

3. **RemoveUnnecessaryParentheses**: Optimizes expressions by removing redundant parentheses
   - Preserves operator precedence
   - Handles cases like `((1))` → `1` and `(1+2)+3` → `1+2+3`
   - Keeps necessary parentheses like in `(1+2)*3`

4. **InfixToRPN**: Converts standard arithmetic notation to Reverse Polish Notation
   - Transforms `1+2*3` → `1 2 3 * +`
   - Useful for calculator implementations and expression evaluation

## How It Works

1. **Parsing**: Expressions are first parsed into an AST using Lark
2. **Transformation**: The AST is processed using either:
   - Interpreter class (top-down)
   - Transformer class (bottom-up)
3. **Output**: Results can be:
   - Evaluated to a number
   - Minified to a shorter string
   - Converted to RPN

## Example Usage

```python
# Evaluate an expression
interpreter = Interpreter()
result = interpreter.visit(parser.parse("(1+2)*3"))  # Returns 9

# Minify an expression
minified = minify("1 + ((2)) * 3")  # Returns "1+2*3"

# Convert to RPN
rpn = infix_to_rpn("1+2*3")  # Returns "1 2 3 * +"
```

## Educational Value

This project demonstrates several important concepts in compiler design and language processing:
- Parsing and grammar design
- AST manipulation
- Different tree traversal strategies
- Expression optimization
- Notation conversion

It's particularly useful for understanding how calculators and simple programming language implementations work under the hood.