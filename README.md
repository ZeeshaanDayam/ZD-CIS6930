# Delphi Interpreter

This project implements a Delphi-like interpreter using ANTLR4 and Java. It supports object-oriented extensions, user-defined procedures, functions, and comprehensive control flow constructs including loops, BREAK, and CONTINUE statements. All new features and test cases have been updated and now work flawlessly.

## New Features

- **Loop Control Enhancements:**  
  BREAK and CONTINUE statements are fully supported in all loop constructs (WHILE, FOR, and REPEAT). The interpreter uses custom exceptions to gracefully exit or continue iterations.

- **Procedure and Function Handling:**  
  Procedures (and functions, if applicable) are now handled in a case-insensitive manner. This improvement ensures that user-defined routines work as expected regardless of the identifier case used in the source.

- **Error Handling and Scope Management:**  
  Enhanced error messaging for undefined variables and procedures. Local and global scopes are properly managed to simulate Delphi’s static scoping rules.

- **Enhanced Grammar:**  
  The grammar file (`Delphi.g4`) has been updated to reflect new language constructs including class definitions, object instantiation, and a custom terminator (`STOP`) for class blocks.

## Test Cases

The project comes with a suite of test cases to verify interpreter functionality:

- **TestRepeat.pas**  
  Validates REPEAT UNTILL loop iteration.

- **TestIO.pas**  
  Validates I/O operations using built-in procedures such as `READ` and `PRINT`.

- **TestObjCreation.pas**  
  Checks correct object instantiation and usage.

- **TestPROC.pas**  
  Tests user-defined procedure declarations and calls along with proper scope management.

- **TestFunc.pas**  
  (If functions are implemented) Verifies that function calls, return values, and expressions evaluate correctly.

- **TESTBREAK.pas**  
  Ensures the BREAK statement exits loops (WHILE, FOR, REPEAT) immediately when invoked.

- **TESTCONTINUE.pas**  
  Ensures the CONTINUE statement properly skips to the next loop iteration without executing remaining statements in the current cycle.

- **TestWhile.pas**  
  Tests the correct evaluation and execution of WHILE loops, including proper handling of BREAK and CONTINUE.

- **TestFor.pas**  
  Validates FOR loop iteration in both increasing and decreasing order, along with in-loop control features.

## Setup and Run Instructions

Follow these steps to generate the parser/lexer, compile the code, and run the interpreter on the test cases.

### 1. Generate the Parser/Lexer

Create a folder for the generated files and run the ANTLR4 tool:

```bash
mkdir gen
antlr4 Delphi.g4 -o gen -listener -visitor
```
2. Compile the Generated Files
Change to the gen directory and compile all generated Java files:

```bash
cd gen
javac -cp ".;C:\antlr4\antlr-4.13.2-complete.jar" *.java
cd ..
```
3. Compile the Interpreter
Compile the interpreter using the generated classes:

```bash
javac -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter.java
```
4. Run the Interpreter
Run the interpreter on any of the test case files. Examples:

Repeat Test:

```bash
java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestRepeat.pas
```

I/O Test:

```bash
java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestIO.pas
```
Object Creation Test:

```bash
java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestObjCreation.pas
```
Procedure Test:

```bash

java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestPROC.pas
```
Function Test (if implemented):

```bash

java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestFunc.pas
```
Break Statement Test:

```bash

java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TESTBREAK.pas
```
Continue Statement Test:

```bash

java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TESTCONTINUE.pas
```
While Loop Test:

```bash
java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestWhile.pas
```
For Loop Test:

```bash

java -cp ".;gen;C:\antlr4\antlr-4.13.2-complete.jar" DelphiInterpreter TestFor.pas
```
