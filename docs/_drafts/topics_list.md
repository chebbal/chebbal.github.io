---
created: 2025-05-11T07:46
updated: 2025-05-15T06:56
---
## Compilers/interpreters

General:
1. Pick an open source implementation of a language you like. Download the source code and poke around in it. Try to find the code that implements the scanner and parser. Are they hand-written, or generated using tools like Lex and Yacc? (.l or .y files usually imply the latter.)
3. Just-in-time compilation tends to be the fastest way to implement a dynamicallytyped language, but not all of them use it. What reasons are there to not JIT? 

4. Most Lisp implementations that compile to C also contain an interpreter that lets them execute Lisp code on the fly as well. Why?

Scanning:
1. The lexical grammars of Python and Haskell are not _regular_. What does that mean, and why aren’t they?
    
2. Aside from separating tokens—distinguishing `print foo` from `printfoo`—spaces aren’t used for much in most languages. However, in a couple of dark corners, a space _does_ affect how code is parsed in CoffeeScript, Ruby, and the C preprocessor. Where and what effect does it have in each of those languages?
    
3. Our scanner here, like most, discards comments and whitespace since those aren’t needed by the parser. Why might you want to write a scanner that does _not_ discard those? What would it be useful for?
    
4. Add support to Lox’s scanner for C-style `/* ... */` block comments. Make sure to handle newlines in them. Consider allowing them to nest. Is adding support for nesting more work than you expected? Why?

Syntax tree:

chapter 5:
1. Earlier, I said that the |, *, and + forms we added to our grammar metasyntax were just syntactic sugar. Given this grammar: lox/AstPrinter.java add after visitUnaryExpr() << lox/AstPrinter.java add after parenthesize() << expr → expr ( "(" ( expr ( "," expr )* )? ")" | "." IDENTIFIER )+ | IDENTIFIER | NUMBER Produce a grammar that matches the same language but does not use any of that notational sugar. Bonus: What kind of expression does this bit of grammar encode? 
2. The Visitor pattern lets you emulate the functional style in an object-oriented language. Devise a complementary pattern for a functional language. It should let you bundle all of the operations on one type together and let you define new types easily. (SML or Haskell would be ideal for this exercise, but Scheme or another Lisp works as well.)
3. In Reverse Polish Notation (RPN), the operands to an arithmetic operator are both placed before the operator, so 1 + 2 becomes 1 2 +. Evaluation proceeds from le! to right. Numbers are pushed onto an implicit stack. An arithmetic operator pops the top two numbers, performs the operation, and pushes the result. Thus, this: (1 + 2) * (4 - 3) in RPN becomes: 1 2 + 4 3 - * Define a visitor class for our syntax tree classes that takes an expression, converts it to RPN, and returns the resulting string
