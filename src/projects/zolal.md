# Zolal

[zolal](https://github.com/zii-lang/zolal) is the official project and toolchain management utility for the Z Programming Language.

Its purpose is to provide a unified interface for managing Z development environments, toolchains, projects, and dependencies.
## Responsibilities
Zolal is responsible for:

- Downloading and installing Z toolchains.
- Managing installed toolchain versions.
- Managing Z project dependencies and libraries.
- Parsing and validating Z project manifests.
- Resolving project configuration.
- Preparing and invoking the Z compiler.

## Goals
### ZOLAL-001: Project Manifest
Provide a manifest system for describing Z projects and their configuration.
**Objectives:**
- [ ] Define the Z project manifest format.
- [ ] Parse manifests using `zaban`.
- [ ] Validate manifest structure and fields.
- [ ] Support project metadata.
- [ ] Support compiler and build configuration.
- [ ] Support dependency declarations.

### ZOLAL-002: Dependency Management
Provide a mechanism for managing external libraries and project dependencies.
**Objectives:**
- [ ] Download libraries from configured sources.
- [ ] Resolve project dependencies.
- [ ] Support dependency version constraints.
- [ ] Cache downloaded dependencies.
- [ ] Avoid unnecessary repeated downloads.
- [ ] Detect dependency resolution conflicts.

### ZOLAL-003: Toolchain Management
Provide a reliable mechanism for downloading, installing, and managing Z toolchains.
**Objectives:**
- [ ] External library pinning and switching.
- [ ] Download Z toolchains from configured distribution sources.
- [ ] Install toolchains locally.
- [ ] Support multiple installed toolchain versions.
- [ ] Select the toolchain used by a project.
- [ ] Verify downloaded toolchain integrity.
- [ ] Provide commands to inspect installed toolchains.
- [ ] Support toolchain updates and removal.

### ZOLAL-004: Compiler Integration
Integrate Zolal with the Z compiler to provide a unified project compilation workflow.
**Objectives:**
- [ ] Locate the appropriate compiler installation.
- [ ] Read project configuration.
- [ ] Resolve project dependencies before compilation.
- [ ] Pass the appropriate configuration to the compiler.
- [ ] Forward compiler output and diagnostics.
- [ ] Return the compiler's exit status.

### ZOLAL-005: Command-Line Interface
Provide a consistent command-line interface for Z development workflows.
**Objectives:**
- [ ] Provide a unified `zolal` command.
- [ ] Implement toolchain management commands.
- [ ] Implement project management commands.
- [ ] Implement dependency management commands.
- [ ] Provide useful command help and error messages.
- [ ] Support non-interactive execution.

## Dependencies

- **zaban:** Manifest parsing and syntax infrastructure.
- **zirsakht:** Shared infrastructure, logging, and source management.
- **Z Compiler:** Compilation and code generation.

## Expected Outcome

Zolal should become the primary entry point for developers working with Z projects.

A developer should be able to install a toolchain, initialize a project, manage its dependencies, and compile it through a unified workflow without manually managing the underlying compiler infrastructure.
