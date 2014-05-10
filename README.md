svelTest Language Reference Manual
==================================
Welcome! This is the documentation for svelTest. Last updated May 10, 2014.

For new programmers, our [tutorial](http://sveltest.github.io/tutorial) is a great resource to help you get started.

# Table of Contents
1. [Introduction](#introduction)
2. [Lexical Conventions](#lexical-conventions)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 2.1 [Tokens](#tokens)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 2.2 [Comments](#comments)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 2.3 [Identifiers](#identifiers)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 2.4 [Keywords](#keywords)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 2.5 [Reserved](#reserved)
3. [Types](#types)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 3.1 [Basic Types](#basic-types)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.1.1 [int](#tokens)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.1.2 [double](#double)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.1.3 [boolean](#boolean)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.1.4 [string](#string)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.1.5 [file](#file)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 3.2 [Derived Types](#derived-types)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.1 [Arrays](#arrays)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.2 [Functions](#functions)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.3 [input](#input)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.4 [output](#output)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.5 [funct](#funct)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.5.1 [assert](#assert)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.5.2 [The lang Declaration](#the-lang-declaration)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.5.3 [funct Restrictions](#funct-restrictions)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.2.5.4 [funct Helper Files](#funct-helper-files)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 3.3 [Constants](#constants)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.3.1 [char constants](#char-constants)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.3.2 [boolean constants](#boolean-constants)
4. [Input/Output](#input--output)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 4.1 [print](#print)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 4.2 [Reading from files](#reading-from-files)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 4.3 [Writing to files](#writing-to-files)
5. [Scope](#scope)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 5.1 [Lexical Scope](#lexical-scope)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 5.2 [Global Scope](#global-scope)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 5.3 [Function Scope](#function-scope)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 5.4 [Statement Block Scope](#statement-block-scope)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 5.5 [Scope of Functions](#scope-of-functions)
6. [Expressions](#expressions)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.1 [Primary Expressions](#primary-expressions)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.2 [Function Calls](#function-calls)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.3 [Multiplicative Operators](#multiplicative-operators)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.4 [Additive Operators](#additive-operators)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.5 [Relational Operators](#relational-operators)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.6 [Equality Operators](#equality-operators)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.7 [Logical AND Operator](#logical-and-operator)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.8 [Logical OR Operator](#logical-or-operator)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.9 [Assignment Expression](#assignment-expression)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.10 [Declarations and Definitions](#declarations-and-definitions)
<br>&nbsp;&nbsp;&nbsp;&nbsp; 6.11 [Statements](#statments)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.11.1 [Expression Statement](#expression-statement)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.11.2 [If-Else Statements](#if-else-statements)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.11.3 [Loop Statements](#loop-statements)
7. [Grammar](#grammar)

# Introduction

This manual describes the svelTest programming language, which provides numerous features to simplify the testing of production-level code. This manual follows the structure of Kernighan and Ritchie’s C Reference Manual, starting with a look at svelTest’s lexical conventions, its syntax, and finally its grammar.

# Lexical Conventions
## Tokens
svelTest has six classes of tokens: identifiers, keywords, constants, string literals, operators, and other separators. The compiler considers blanks, tabs, newlines, and comments “whitespace”. Any whitespace is ignored by the compiler except when separating tokens.

## Comments
svelTest uses double forward slashes (`//`) for single-line comments, which terminate at the newline character.  Block comments use the standard forward slash-asterisk combination (`/*`), and may not be nested or exist in literal types.  A comment is treated by the compiler as a whitespace character and may exist anywhere a whitespace character is allowed.  The user cannot include comments within tokens.  The compiler ignores all characters in a comment.

```
// This is an inline comment
```

```
/* This is a
block comment */
```
```
/* This is also
* a block comment
*/
```

## Identifiers
An identifier is a token which names a svelTest language entity.  A token may consist of alphanumeric sequences of any length with underscores allowed, but cannot start with a number.  An identifier can represent a primitive, object, or function.

## Keywords
The following identifiers are reserved for use as keywords, and may not be used otherwise.


Control flow | svelTest primitives | Other primitives
-------------|---------------------|-----------------
`if` 	|	`funct`		|	`int`
`else`	|	`input`	|	`boolean`
`for`	|	`output`		|	`char`
`while`	|	`file`		|	`double`
`return`	|	`__main__`	|	`string`
`break`	|	`verbose`		|	`void`
`continue`|	`lang`		|	`null`
`true`	|			|
`false`	|			|

The following function names are also reserved:

Standard | Array functions | File reading
---------|-----------------|-------------
`main`	| 	`size`	| `readlines`
`print`	| 	`append`|
`assert`| 	`insert`|
`int`	|	`remove`|
`double`|	`replace`|
`boolean`|		|
`string`|		|


Note that the following Python keywords are also reserved, as svelTest programs compile to Python code:

	|		|		|
---------|-----------------|-------------
`and`	|	`exec`	|	`lambda`
`as`	|	`finally`	|	`None`
`class`	|	`from`	|	`not`
`def`	|	`global`	|	`or`
`del`	|	`import`	|	`pass`
`elif`	|	`in`	|	`raise`
`except`	|	`is`	| 	`try`
`with`	|	`yield`	|

When the declaring a new `funct` object, the user specifies the source code parameter type with this template:

`languageAbbreviation_type` (ex: `j_byte` for a Java byte, `j_long` for a Java long, etc.).  We currently support all Java 1.6, Python 2.x, and C99 primitive data types. A full list of these primitives and their styling can be found in Appendix A.

## Reserved
The following list contains characters that are reserved for use in our grammar. They may not be used in identifiers or for any purpose other than their intended use in our language.

( ) [ ] { } ; : , .

\+ - ++ -- * / < > <= >= == = != 

&& || ! \ ' "

# Types

## Basic Types
svelTest has 5 primitive types.

### int
The `int` data type represents signed integer values. Similar to the implementation in Python 2.7.x, an `int` is a two’s complement constant, is 31 bits in size, and has a range from -2147483648 through 2147483647, inclusive.

### double
The `double` data type represents machine-level double precision floating point numbers.  Similar to Python 2.7.x, the accepted range and overflow handling is dependent on your underlying machine architecture. 

### boolean
The `boolean` type represents a logical quantity with two possible values, indicated by the reserved keywords `true` and `false`. Similar to Python 2.7.x, a `boolean` is a subtype of plain integers, and `boolean` values `true` and `false` behave like the integer values 1 and 0, respectively.

### string
A `string` is an immutable sequence of characters surrounded by double quotation marks. There is no separate character type; a character is simply a `string` of length one. Similar to Python 2.7.x, characters have a size of (at least) 8-bits.

### file
The `file` type is used to reference an ASCII file relative to the user’s working directory. The `file` type is a subtype of the `string` type. It contains a string that specifies the relative path from the .svel file. If the file does not exist in the path specified, the svelTest compiler will fail and throw an error.

```
file f = “src/Foo.java”;
```

A `file` type is used to specify the source code file (*.java, *.c, *.py) that contains the function or program to test. A file type can also be used to specify an ASCII file with the extension *.txt; this provides the option for a svelTest programmer to parse a .txt file for inputs and outputs. 

Alternatively, a file name could first be specified as a string and then used to create the file, like so:

```
String filename = “../lib/thisFile.java”;
file thisFile = filename;
```

These `int`, `double`, `boolean`, and `string` primitive types may be cast to other types with the library functions `int()`, `double()`, `boolean()`, `string()`.

## Derived Types
Besides the basic types, there is a conceptually infinite class of derived types constructed from the fundamental types in the following ways:
- arrays of objects of a given type
- functions returning objects of a given type


Along with the common array and function, svelTest has three additional derived types: `input`, `output`, and `funct`.

### Arrays
The user can initialize an array with inputs in curly brackets, or use the `append()` function to add an element to the end of an existing array. Note that if the user wishes to insert values into an empty array, the user must first initialize the array as empty with curly brackets. svelTest arrays follow zero-based numbering.

```
int[] a = {1, 2, 3}; // valid inline declaration

int[] b = {};
b.append(1);    
b.append(2);    
b.append(3); 
// b is now {1, 2, 3}

int i = a[0]; // 1
```

Other supported array functions are `remove()`, `insert()`, `size()`, and `replace()`. Examples of these functions are outlined below:

```
int[] c = {1, 2, 3};
// Prototype: a.remove(int index) 
// Removes object at the specified index and returns it
c.remove(2); // returns 3, list is now {1, 2}

int[] d = {1, 2, 3};
// Prototype: array.size()
// Takes zero arguments.
int j = d.size(); // 3

int[] e = {1, 2, 3};
// Prototype: a.insert(int index, Type t) 
// Inserts and pushes back.
e.insert(0, 4); // {4, 1, 2, 3}

int[] f = {1, 2, 3};
// Prototype: a.replace(int index, Type t);
// Replaces object at the index and returns the old object.
f.replace(0, 4); // {4, 2, 3}
```

### Functions
A function is declared by specifying a return type (or `void`), name, and any parameters. For example, we have a function prototype for an add function that takes two integers as parameters and returns an integer:
```
int add(int x, int y)
```
### input
The input data type is a wrapper for an n-sized tuple, where n represents the number of parameters of the method to test. Each value in the tuple can take the type of any data type, including those in the source code language. An input is used to specify a set of actual parameters for any method the user wants to test. Parentheses are used to denote a set of actual parameters as an input type, and commas are used to separate each parameter.

```
input empty = (); // method to test takes no parameters
input single = (3); // takes a single parameter of type int
input multiple = (“Hello World”, true); // takes two params
```

### output
The output data type is a wrapper for the expected return value of the method to test. The value of an output can take the type of any source code language data type.
```
output out = "Hello World!";
```

### funct
The funct type is a wrapper to specify the method to test. A funct has three fields: the method name denoted by a string, the set of the formal parameters of the method denoted using parentheses and commas, and the file type that specifies where the method is defined. The three fields are surrounded with brackets { } and separated by commas.

```
file f = “src/Add.java”;
funct add = {“add”, (j_int, j_int), f};
```

In the example above, the Add.java class file contains the method with the method signature that has the name “add”, and takes two Java ints as parameters. The keyword __main__ can be used to specify that the entire program should be run. (Note that the user could also specify “main” as the method name.) If the specified method does not exist in the file, the compiler will raise an error.

#### assert
An object of type funct has a reserved, built-in method called assert(). The assert() method returns a boolean and takes in two parameters: an input type and output type. 

```
boolean assert(input, output)
```

When the assert() method is called via an object of type funct, the method specified by the funct object will be tested with the given input parameters. The actual return value or contents of standard output will be validated against the expected return value or standard output contents. If the actual return value or console contents matches the expected, assert() returns true. Otherwise, it will return false.

```
input in = (1, 1);
output out = (2);
if (add.assert(in, out)) {
    print(“add passed.”);
} else {
    print(“add failed.”); 
}
```

Python’s “==” equality operator is used to test for equality between the expected output and the actual output of the function being tested. If the user wishes to test the output of a non-primitive object, that user must write their own toString() method for that object, as svelTest compares output by string representation.

The assert method also has an optional third argument, verbose. Specifying verbose as the third argument adds additional functionality to assert(): instead of just returning true or false, assert will also print test information to standard output for you.

```
fib.assert(4, 3, verbose);
// Output: fib(4)...        PASS
```

#### The lang Declaration
In order for assert() to know what kind of code you’re testing, every svelTest file must start with a lang declaration. Currently supported lang types are Java, C, Python, and None. lang declarations are of this form:

```        
lang = Java;
```

#### funct Restrictions
Depending on which language is being tested, there are some restrictions on what kinds of functions can be tested successfully with funct.

#####Java
Any public static function that takes Java primitives or void (including the main() method)

#####C
Any main() method that C primitives or void

Any method that takes C primitives or void contained in a file not also containing a main() method

#####Python:
Any “main” method i.e. the equivalent of running `python <file_to_test>.py` and testing the output

Any function contained within a class definition

Any of the above functions that do not return primitives/void can be tested as long as the returned value can be compared with a toString() method written by the user.

#### funct Helper Files
funct may create some helper files at runtime. For example, you may write addTester.svel to test the public static function add() contained in Add.java. Your code will compile to addTester.py; upon running addTester.py, the helper file Sveladd.java will be created and compiled. This allows the program to test add() individually rather than having to use the entire Add.java class. 

Note that these helper files are not removed after addTester.py finishes execution. This is for efficiency reasons: rather than creating, compiling, deleting, and repeating the entire process for every execution of assert(), the helper files are created and compiled only once. We suggest creating a Makefile with a target “clean” to remove all Svel* files after you’re done testing, or simply using a command like rm Svel*.

## Constants

### char constants

Special constants that are reserved or cannot be represented without conventional keys are represented with escape sequences.

* newline&nbsp;&nbsp;&nbsp;&nbsp;\n
* horizontal tab&nbsp;&nbsp;&nbsp;&nbsp;\t
* carriage return&nbsp;&nbsp;&nbsp;&nbsp;\r
* backslash&nbsp;&nbsp;&nbsp;&nbsp;\\ \\
* single quote&nbsp;&nbsp;&nbsp;&nbsp;\’
* double quote&nbsp;&nbsp;&nbsp;&nbsp;\”

### boolean constants
A boolean can either take the value true or false.

# Input/Output

## print
svelTest users may send values to Standard Out using the print function.  print takes in variables of any type, converting any non-string types to strings on-the fly.

```
print(“Hello World!”); // prints Hello World!

int a = 1;
print(a); // prints 1
int b = 2;
print(b); // prints 2
int c = a + b;
print(c); // prints 3

boolean bl = true;
print(bl); // prints true
```

## Reading from Files
As outlined above, the file type is used to reference an ASCII file relative to the user’s working directory. They use may use the file type to load a source code file, or a file containing streams of inputs and outputs.

```
file f = “../Foo.java”;
file g = “inputs.txt”;
file h = “outputs.txt”;
```

The file type has the reserved, built-in function readlines() that reads the entire contents of a file into a string array. The trailing newline character on each is not kept in the string.

```
// testcases.txt
// 0
// 1
// 2

file testcases = "testcases.txt";
string[] lines = testcases.readlines();
print(lines); // ['0', '1', '2']
```

## Writing to Files
The user may not create new files or write to existing files in a svelTest program. If a user wishes to write the output of a svelTest program to a file, they may use the ‘>’ character to redirect the contents of standard out to a new file of their choice in their favorite shell.

# Scope
The scope of a declaration is the region within the svel program which the entity declared by the declaration can be referred to using the name of the entity. The svelTest compiler will catch any scoping issues.

## Lexical Scope
A code block defines the scope of a variable. Variables declared in a specific scope are not visible from outside that block. Furthermore, variables declared in the same scope must have unique names.

## Global Scope
Variables declared outside of functions are considered to have a global scope.  These variables exist in all other scopes throughout the program.

## Function Scope
Variables declared inside functions exist only within the scope of that function, and die upon the termination of that function.

## Statement Block Scope
Variables declared inside statement blocks exist only within the scope of that statement, and die upon leaving the block.

## Scope of Functions
svelTest requires users to define a function before using it. For example, the following syntax is not valid:

```
main() { 
notDefined(); 
}

void notDefined() {
    print “This function is not defined correctly.”;
}
```

```
The following syntax is valid:
void defined() {
    print(“This function is defined correctly.”);
}

main() {
    defined();
}
```

# Expressions

## Primary Expressions

Primary expressions are identifiers, constants, or strings.  Constants are defined by a number (integer), decimal number, true and false boolean statements, function calls, and reference types (for accessing array elements).

```
primary_expr : 	ID
 	     | STRINGLITERAL
 	     | NUMBER
	     | DECIMAL
	     | TRUE
	     | FALSE
	     | function_call
	     | ref_type
```

## Function Calls
A function call is a postfix expression that consists of a function name and parameter list surrounded by parentheses.  Casting to the various data types is also done through Function calls.

```
function_call : ID LPAREN identifier_list RPAREN
                | STRING LPAREN logical_OR_expr RPAREN
                | INT LPAREN logical_OR_expr RPAREN
                | BOOLEAN LPAREN logical_OR_expr RPAREN
                | DOUBLE LPAREN logical_OR_expr RPAREN
                | PRINT LPAREN logical_OR_expr RPAREN
                | ID PERIOD lib_function LPAREN identifier_list RPAREN
```

## Multiplicative Operators
The multiplicative operators are * (multiplication) and / (division), and group left-to-right.

```
multiplicative_expr : secondary_expr
                    | multiplicative_expr TIMES secondary_expr
                    | multiplicative_expr DIVIDE secondary_expr
```

The modulus operation is not supported in svelTest.

## Additive Operators
The additive operators are + (addition) and - (subtraction), and group left-to-right.

```
additive_expr : multiplicative_expr
            | additive_expr PLUS multiplicative_expr
            | additive_expr MINUS multiplicative_expr
```

## Relational Operators
The relational operators are < (less), > (greater), <= (less or equal), >= (greater or equal).

```
relational_expr : additive_expr
                | relational_expr LS_OP additive_expr
                | relational_expr LE_OP additive_expr
                | relational_expr GR_OP additive_expr
                | relational_expr GE_OP additive_expr
```

## Equality Operators
The equality operators are == (equal to) and != (not equal to), and have lower precedence than the relational operators.

```
equality_expr : relational_expr
            | equality_expr EQ relational_expr
            | equality_expr NEQ relational_expr
```

## Logical AND Operator
The logical AND (&&) operator groups left-to-right.

```
logical_AND_expr : equality_expr
                | logical_AND_expr AND equality_expr
```

## Logical OR Operator
The logical OR (||) operator groups left-to-right.

```
logical_OR_expr : logical_AND_expr
                | logical_OR_expr OR logical_AND_expr
```

## Assignment Expression
Assignment expressions evaluate right-to-left.  The left operand must be an identifier. svelTest is statically typed.

```
assignment_expr : FUNCT ID ASSIGN LBRACE funct_name COMMA LPAREN reserved_languages_list RPAREN COMMA primary_expr RBRACE
                | type ID ASSIGN assignment_expr
                | ID ASSIGN assignment_expr
                | logical_OR_expr
```

## Declarations and Definitions
Declarations specify how an identifier should be interpreted and do not necessarily reserve storage.

```
external_declaration : function_def
                    | type ID SEMICOLON
                    | type ID ASSIGN assignment_expr SEMICOLON
```

Definitions also specify how an identifier should be interpreted and do reserve storage.

```
function_def : VOID ID LPAREN param_list RPAREN brack_stmt
 | type ID LPAREN param_list RPAREN brack_stmt
 | MAIN LPAREN param_list RPAREN brack_stmt
```

## Statements
Statements are executed for their effect, and do not have values.  In addition, statements are normally executed in sequence.

```
stmts : stmts stmt
    | stmt
    | brack_stmt

stmt : expression_stmt
     | ifelse_stmt
     | loop_stmt
     | jump_stmt
```

### Expression Statement
Expressions ended with a semicolon (;) are Expression Statements. The result of the expression statement evaluation is not stored unless explicitly reassigned to a new identifier.

```
expression_stmt : expression SEMICOLON

expression : assignment_expr
            | type ID
            | empty
```

### If-Else Statements
If-else statements define the if and if-else control-flow mechanisms.

```
ifelse_stmt : IF LPAREN expression RPAREN brack_stmt
            | IF LPAREN expression RPAREN brack_stmt ELSE brack_stmt
```

The expression contained within the parentheses is evaluated as a boolean or boolean equivalent. If this expression is true, the first statement is evaluated. If the expression is false the statement following the else is evaluated, or none in the case that there is no else.

The ambiguity of the dangling-else problem is handled by binding each else to the nearest if statement.

### Loop Statements
Loop statements define the the while and for looping mechanisms.

```
loop_stmt : WHILE LPAREN expression RPAREN brack_stmt
        | FOR LPAREN expression SEMICOLON expression SEMICOLON expression RPAREN brack_stmt
```

The while loop works by first evaluating the expression contained within the parentheses and executing the statement if the expression evaluates to true. The loop will continue to evaluate this expression before each iteration until it evaluates to false, at which point the loop will terminate.

The first expression of the for loop is evaluated once and is generally used for the initialization mechanism of loop. The second expression is evaluated before each iteration of the for loop and is analogous to the parenthesized expression in the while loop. Note that a missing second expression will be evaluated to true. The third and final expression is evaluated at the end of each iteration, after the statement has been executed, and is generally used to update the state of the loop (e.g. a counter).
