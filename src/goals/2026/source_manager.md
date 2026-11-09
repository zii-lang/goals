# SourceManager

- Feature Name: `source_manager`
- Project: `zirsakht`
- Status: Planned

## Overview

`SourceManager` is a core component of Zirsakht responsible for managing source files and their associated data throughout the Z toolchain.

Since multiple components of the Z toolchain need to access and process source code, we need a centralized and consistent way to represent, store, retrieve, and manage source files.

Instead of allowing each project to implement its own source management logic, Zirsakht should provide a shared `SourceManager` implementation.

## Goals

The primary goals of `SourceManager` are:

- Provide a centralized source file management system.
- Assign unique identifiers to source files.
- Store and manage source file contents.
- Provide efficient access to source contents.
- Track source file paths and metadata.
- Support source locations and ranges.
- Provide a foundation for diagnostics and error reporting.
- Allow other Z toolchain components to share source information.

## Responsibilities

### 1. Source Registration

`SourceManager` should provide an API for registering source files.

Each registered source should receive a unique identifier (`SourceId`) that can be used by other components to reference it.

Registration should support:
- Source file paths.
- Source contents.
- Optional source metadata.

### 2. Source Retrieval

Other components should be able to retrieve registered sources using their `SourceId`.

The API should provide access to:
- Source contents.
- Source paths.
- Source metadata.

### 3. Source Locations

SourceManager should provide the infrastructure required to represent locations within source files.

This includes:
- Byte offsets.
- Source positions.
- Source ranges (spans).

These representations should make it possible for the lexer, parser, compiler, and diagnostic system to refer to precise locations in source code.

### 4. Source Metadata

The system should be able to maintain metadata associated with each source file.

Potential metadata includes:
- File path.
- File name.
- Source length.
- Source type (if needed).

## Integration

`SourceManager` should be designed as shared infrastructure for the entire Z toolchain.

Expected consumers include:

- **Zaban:** Uses source identifiers and source locations when tokenizing and parsing source code.
- **Zolal:** Uses source management when parsing manifests and reporting errors.
- **Z Compiler:** Uses source information throughout compilation and diagnostics.
- **Other Toolchain Components:** Can access source information without implementing their own storage mechanisms.

## Implementation Milestones

- [ ] Design the `SourceManager` API.
- [ ] Implement `SourceId`.
- [ ] Implement source registration and storage.
- [ ] Implement source retrieval.
- [ ] Implement source locations and ranges.
- [ ] Add source metadata support.
- [ ] Integrate `SourceManager` with Zaban.
- [ ] Add unit tests and documentation.

## Expected Outcome

After implementation, Zirsakht should provide a reusable and centralized source management system.

All Z toolchain components should be able to share source files and reference precise locations within them, establishing a common foundation for parsing, compilation, and diagnostics.
