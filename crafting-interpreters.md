# Crafting Interpreters - https://craftinginterpreters.com/


### A Map of the Territory

#### The Parts of  a Language
Scanner(or lexer): Break the source code into a sequence of tokens(words). Whitespace and comments are discarded by the lexer.

Parser: Takes a flat sequence of tokens and turns it into a tree.

Static analysis: The language binds names to values, and in statically typed languages, it does type checking.
