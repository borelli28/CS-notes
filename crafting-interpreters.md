# Crafting Interpreters - https://craftinginterpreters.com/


### A Map of the Territory

#### The Parts of  a Language
Scanner(or lexer): Break the source code into a sequence of tokens(words). Whitespace and comments are discarded by the lexer.

Parser: Takes a flat sequence of tokens and turns it into a tree.

Static analysis: The language binds names to values, and in statically typed languages, it does type checking.

Intermediate representation: Created by the compiler or interpreter as an abstract and simplified version of the source code, which facilitates the compilation process. Its not the source code nor the compiled machine code, is something in the middle.

Optimization: Swap out user code with a code that has the same semantics, but is more efficient.

Code generation: Translate the optimized intermediate representation into machine code or bytecode.

Virtual machine: A program that emulates a CPU and executes the bytecode.

Runtime: Things like garbage collection that are part of the language may get compiled with the program and ran at runtime.

### Shortcuts and Alternates Routes

#### Single-pass Compilers
Some simple compilers interleave parsing and code generation, so they don't need to build a full syntax tree. Pascal and C were designed around this limitation. At the time, memory was so precious that a compiler might not even be able to hold an entire source file in memory, much less the whole program

#### Tree-walk Interpreters
Some languages begin executing code right after parsing it into an AST. The interpreter walks the tree, executing the code as it goes. This implementation style is common for student projects and little languages, but is not widely used for general-purpose languages since it tends to be slow.

#### Transpilers
Instead of writing a backend that generates machine code, you can write a backend that generates code in another language, like C, then teh C compiler handles the rest.

#### Just-in-time Compilation
On the end-user machine, the program source code is loaded, then the program is compiled to native(machine) code for the architecture their computer supports. The program can be loaded from source, in the case of Javascript, or from platform independent bytecode, like Java(JVM) and C#(CLR).

### Compilers and Interpreters
Compiling: Translating a source language into another source language, usually a lower-level one, without executing it.

Interpreting: Reading source code and execute it immediately.
