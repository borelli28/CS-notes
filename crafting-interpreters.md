# Crafting Interpreters - https://craftinginterpreters.com/


### A Map of the Territory

#### The Parts of  a Language
Scanner(or lexer): Break the source code into a sequence of tokens(words). Whitespace and comments are discarded by the lexer.

Parser: Takes a flat sequence of tokens and turns it into a tree.

Static analysis: The language binds names to values, and in statically typed languages, it does type checking.

Intermediate representation: Created by the compiler or interpreter as an abstract and simplified version of the source code, which facilitates the compilation process. Its not the source code nor the compiled machine code, is something in the middle.
