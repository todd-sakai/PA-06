# PA-06

Expression Tree
Problem Context

In class, we discussed Binary Search Trees, which are a special form of Binary Trees. In this programming assignment, you will implement another form, Binary Expression Trees.

Binary Expression Trees are a way to represent algebraic expressions and allow for computational analysis of such expressions. In this type of tree, operators (e.g., +, *, /) are internal nodes and operands (e.g., numbers) are leaf nodes.

Examples

Here is an example expression and corresponding binary expression tree:

(5 + 7) * (9 – 2) 


Notice how the tree is organized in order of operations:

5 and 7 are leaves under parent node + (addition)

9 and 2 are leaves under parent node - (subtraction)

The result of the + (addition) and - (subtraction) are child nodes under root node * (multiplication)

Your program will support a specific subset of expressions, with the following characteristics:

The expressions are algebraic, with operators in the set [+, -, *, /, //, %, **]. Note that there are no unary operators. That is, all operators take exactly two arguments: one on the left and one on the right.

There will be no negative numbers as operands since they use the - operator as a unary operator.

Each operator and its two operands are surrounded by parenthesis. 

The operators and operands will be separated by a space so the string is easier to parse. 

Valid examples:

( 2 + 3 )
( ( 4 / 2 ) / 3 )
( ( 4 ** 2 ) + ( 2 % 3 ) )
Invalid examples:

2 + 3
( 4 + 2 * 7 ) / ( 3 + 1 )
( -2 + 3 )
Your program can assume that the input files only include expressions that meet all requirements above.

Requirement - Analyze the Expression Tree

After the expression tree is created, evaluate the expression by traversing the tree. 

Then, evaluate the prefix and postfix notation for the expression:

A prefix expression has each operator come before the two operands that they work on. A simple example is (4 + 3 * 8) is + 4 * 3 8 in prefix notation. Note that there are no parentheses in prefix notation. Another example:

Infix: ( ( 4 / 2 ) + ( 2 % 3 ) )
Prefix : + / 4 2 % 2 3

Breaking it down:

The plus sign’s 2 operands are (4 / 2) and (2 % 3): + ( 4 / 2 ) ( 2 % 3 ) 

Evaluate the first operand. Its operator is division, with operands 4 and 2: + / 4 2 ( 2 % 3 ) 

Evaluate the second operand. Its operator is modulus, with operands 2 and 3: + / 4 2 % 2 3 

A postfix expression has each operator come after the two operands that they work on. A simple example is (4 + 3 * 8) is 3 8 * 4 + in postfix notation. Note that there are no parentheses in postfix notation. Another example:

Infix: ( ( 4 / 2 ) + ( 2 % 3 ) )

Postfix: 4 2 / 2 3 % +

Breaking it down:

The plus sign’s 2 operands are (4 / 2) and (2 % 3):  ( 4 / 2 ) ( 2 % 3 ) +

Evaluate the first operand. Its operator is division, with operands 4 and 2: 4 2 / ( 2 % 3 ) +

Evaluate the second operand. Its operator is modulus, with operands 2 and 3: 4 2 / 2 3 % + 

Input

Input files will contain one line that is a single algebraic expression. The provided input file contains: 

( ( 8 + 3 ) * ( 7 - 2 ) )
No input validation is required. 

Output

The output should include:

line 1 - the original expression, an equals sign, and the results of evaluating the expression

line 2 - a label and the prefix version of the expression

line 3 - a label and the postfix version of the expression

The output produced by the provided input file is:

( ( 8 + 3 ) * ( 7 - 2 ) ) = 55
Prefix Expression: * + 8 3 - 7 2
Postfix Expression: 8 3 + 7 2 - *
Starter Code

The starter code includes a main() method and a Stack implementation that you do not need to modify. All of your edits should take place in ExpressionTree.py. Do not change the name of these methods. This will break the grading scripts and result in 0 correctness points.

Notice how the main method includes a debug flag. When set to True, notice how your program will use the expression.in file as the input, which you can use to write custom test cases. When set to False, the program will use stdin. Make sure to set debug to False when submitting as the grading scripts will pass inputs through stdin.

Take note of the code style used in the starter file. We will apply a similar rubric (see below) when manually assessing code style.

Approach

Try working out the provided expression in expression.in on pen and paper. As humans, it's easy for us to see the entire expression and quickly build out the tree. We strongly recommend you act like a computer, and try parsing the expression one character at a time, from left to right.

Consider the following questions to help guide your implementation:

What should the resulting tree look like?

If I see a parenthesis/operator/operand, do I need to update my parent/child node and/or myself?

Try tracing the pattern of generating the tree. Is there a last in first out pattern that a stack could help with?

How does a stack help you create an expression tree?

Make sure to read through main.py to understand how each expression is transferred from input file to ExpressionTree object. Read through Stack.py to re-familiarize yourself with stack operations.

In ExpressionTree.py note that operators list of valid operators has been defined for you. Also note that the helper function operation() has been implemented for your use.

We recommend implementing the methods in the following order:

Complete create_tree(). The purpose of this method is to build the expression tree based on a given input. Test it using simple expressions such as ( 8 + 3 ). When formatting test cases, remember to include a space between each parenthesis, operand, and operator. Don't forget to test each kind of operator.

Complete evaluate(). The purpose of this method is to evaluate the expression based on an input node. For example, calling evaluate() on the left subtree in the example should return 11. With more complicated expressions, how might recursion help evaluate smaller expressions? What kind of traversal will help you get the arguments to call operation()? Start with simple expressions such as ( 8 + 3 ) then work up to more complex expressions. Compare your output with the provided output.

Complete pre_order() and post_order() and compare your output with the provided output. See In-Class Activity 14 and zyBooks Chapter 21 for inspiration.

Grading

Grading scripts (automated): 70/100 points. The first test case is based on the sample expression.in, and additional test cases are based on data that more fully tests different operators and more complex expressions.

Code review: 30/100 points. TAs will complete a manual code review for each assignment, similar to how a Team Lead would complete a code review in a professional setting. TAs will also complete a technical requirements review in addition to a code style review.

Please refer to the following code style guidelines for this assignment: 15/100 points

Readability: Descriptive variable and method names, no unused code, no commented out code, and proper indentation.

Documentation: One comment per added/modified method describing the input, output, and purpose of the function. Optional additional comments describing high level purpose of each step within a method.

Organization: Lines of code are less than 100 characters long, methods have one primary purpose, logical structure to approach.

Please refer to the following technical requirements for this assignment: 15/100 points

ExpressionTree is built based on character-by-character parsing.

Evaluation of expression is based on recursively traversing ExpressionTree (e.g., no hardcoding).
