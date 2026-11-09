# Lexeme
- Feature Name: `lexeme`
- Project: `zaban`
- Status: Planned

## Overview

Zaban needs a `Lexeme` abstraction to represent textual units recognized during lexical analysis.

A lexeme is simply a string originating from the source code. It does not contain token kinds, source spans, offsets, or other metadata.

## Goals

- Provide a common abstraction for textual lexemes.
- Represent text originating from source code.
- Avoid unnecessary string allocations and copying.
- Keep the abstraction independent of any particular lexer or language.

## Design

A `Lexeme` should contain nothing more than a reference or view of a string in the original source.

Conceptually:

```cpp
struct Lexeme {
    std::string_view* text;
};
```

The actual implementation should follow Zaban's existing string and memory-management conventions.

## Design Considerations

### Source Ownership

A lexeme should not own or duplicate its source text unnecessarily.

Its lifetime must be tied to the lifetime of the underlying source, ensuring that the referenced text remains valid.

### Separation of Responsibilities

Lexeme should not be responsible for:

- Identifying token kinds.
- Tracking source locations.
- Tracking offsets or spans.
- Storing lexer-specific metadata.

These responsibilities belong to other components of the lexical analysis infrastructure.

## Expected Outcome

All Zaban lexers should use a consistent, lightweight representation for textual lexemes without coupling the abstraction to token classification or source management.
