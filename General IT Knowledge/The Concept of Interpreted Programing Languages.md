Interpreted and compiled programming languages differ primarily in how they are executed by a computer. Here’s a detailed explanation of both types and their differences:

### Interpreted Programming Languages

**Definition**: Interpreted programming languages are those in which most of the instructions are executed directly by an interpreter, rather than being compiled into machine code.

**Characteristics**:

1. **Execution**:
    
    - Code is executed line-by-line or statement-by-statement by an interpreter.
    - The interpreter reads the source code, translates it into an intermediate form (if necessary), and executes it directly.
2. **Development Cycle**:
    
    - Typically, interpreted languages have a shorter development cycle because there is no separate compilation step.
    - Changes can be tested immediately without recompiling the entire program.
3. **Portability**:
    
    - Interpreted languages are often more portable because the interpreter abstracts away the underlying hardware and operating system differences.
    - The same source code can run on different platforms as long as the appropriate interpreter is available.
4. **Performance**:
    
    - Generally, interpreted languages are slower than compiled languages because the translation and execution happen at runtime.
    - Some modern interpreters use Just-In-Time (JIT) compilation to improve performance by compiling code on-the-fly.

**Examples**:

- Python
- [[JavaScript as a Single-Threaded Programming Language|JavaScript]]
- Ruby
- PHP
- Perl

### Compiled Programming Languages

**Definition**: Compiled programming languages are those in which the source code is translated into machine code by a compiler before execution.

**Characteristics**:

1. **Execution**:
    
    - The source code is translated into machine code (binary code) by a compiler.
    - The resulting machine code is executed directly by the computer’s CPU.
2. **Development Cycle**:
    
    - Typically, compiled languages have a longer development cycle because the code must be compiled before it can be executed.
    - Any changes to the code require recompilation before testing.
3. **Performance**:
    
    - Compiled languages generally offer better performance because the machine code is optimized for the target hardware.
    - The CPU executes the pre-compiled machine code directly, without the overhead of interpretation.
4. **Portability**:
    
    - Compiled code is usually less portable because it is specific to the target hardware and operating system.
    - To run the same program on different platforms, the source code must be recompiled for each platform.

**Examples**:

- C
- C++
- Rust
- Go
- Swift

### Key Differences Between Interpreted and Compiled Languages

| Feature           | Interpreted Languages                                      | Compiled Languages                                |
| ----------------- | ---------------------------------------------------------- | ------------------------------------------------- |
| Execution         | Line-by-line by an interpreter                             | Entirely translated to machine code by a compiler |
| Development Cycle | Shorter (no separate compilation step)                     | Longer (requires compilation before execution)    |
| Performance       | Generally slower (runtime interpretation)                  | Generally faster (pre-compiled machine code)      |
| Portability       | More portable (interpreter abstracts hardware differences) | Less portable (machine code specific to hardware) |
| Error Detection   | Errors detected at runtime                                 | Errors detected at compile-time                   |
| Debugging         | Easier to debug (runtime feedback)                         | Can be harder to debug (requires recompilation)   |

### Hybrid Approaches

Some languages use a combination of both interpretation and compilation to leverage the benefits of both approaches. For example:

- **Java**: Java source code is compiled into bytecode by the Java compiler. The bytecode is then executed by the Java Virtual Machine (JVM), which interprets or JIT-compiles the bytecode into machine code.
- **Python**: Python source code is compiled into bytecode (.pyc files) by the Python interpreter. The bytecode is then executed by the Python virtual machine.

### Summary

- **Interpreted Languages**: Execute code line-by-line using an interpreter, offering shorter development cycles and better portability but generally slower performance.
- **Compiled Languages**: Translate source code into machine code using a compiler, resulting in faster execution and better performance but requiring a longer development cycle and less portability.

Understanding the differences between interpreted and compiled languages helps developers choose the right tool for their specific needs, balancing factors like development speed, performance, and portability.