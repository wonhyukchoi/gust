# Gust
This is the repository for the standard, interpreter, compiler, and the standard library for the `Gust` language.

`Gust` is designed to be an safe and fast application-building language with many benefits:
* _Safe_: immutable by default, and garbage collection avoids most segmentation faults.
* _Prototypable_: `Gust` can be interpreted, making it easy to prototype.
* _Fast_: When needed, `Gust` can be compiled 
* _Expressive_: Use functional idioms of `map`, `filter`, and `fold`, abstract data types, and higher order functions. Use `trait`s for polymorphism.
* _Easy_: Garbage collection: you don't need to worry about memory management. Syntax: familiar syntax you've been using all your software career.

## Syntax
GPC syntax is largely influenced by `Rust`.
### Example 1
```
import Vector from vector;
import fold from functional;

int add(int x, int y) {
  x + y;
}

int sum(Vector<int> input) {
  fold(add, 0, input);
} 
```

### Example 2
```
enum Boolean {
  Boolean bool,
  Not Boolean,
  And Boolean Boolean,
  Or Boolean Boolean
}

bool evalBoolean(Boolean boolean) {
  case boolean of {
    Boolean b => b,
    Not b => !evalBoolean(b),
    And b1 b2 => evalBoolean(b1) && evalBoolean(b2),
    Or b1 b2 => evalBoolean(b1) || evalBoolean(b2),
  };
}

```

## Runtime
`GPC` is a garbage-collected language.
This means that there are no pointers in the language; except for primitives, all values in `GPC` follow reference semantics.

This means that `GPC` requires a runtime; the runtime is implemented in `Rust`.

## Compiler
The compiler frontend is written in `Haskell`, which emits `LLVM` code.

## Implementation Milestones
- [ ] Sanity Test: basic programs with just primitives
    - [x] Parser
    - [ ] Type Checker
    - [ ] `--i` (`--intepreter`) flag
- [ ] Conditionals
    - [ ] `if`
    - [ ] `else`
    - [ ] `elif`
- [ ] Debug flags `--debug`, `--ast`
- [ ] Compile to LLVM
- [ ] Traits
- [ ] Abstract Data Types
- [ ] Garbage Collection
- [ ] Standard Library
    - [ ] String
    - [ ] Vector
    - [ ] I/O
    - [ ] Functional idioms
        - [ ] Map
        - [ ] Filter
        - [ ] Fold
- [ ] Developer Tools
    - [ ] Syntax Highlighting
    - [ ] Language Server Protocol
- [ ] Bootstrapping
    - [ ] Lexer
    - [ ] Parser
    - [ ] Type Checker
    - [ ] Interpreter
