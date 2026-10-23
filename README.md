![Halo's Gate banner](banner.jpeg)

# Dynamic SSN Resolution — Halo's Gate

This project is a Windows x64 research proof of concept exploring dynamic system service number (SSN) resolution. It is provided for educational and defensive study, not as a supported library, a general-purpose syscall interface, or production-ready software.

## Repository scope

The published repository intentionally omits **`halo.asm`** and **`native.h`**. These files contain supporting assembly and native declarations that would make the syscall-dispatch implementation more complete and straightforward to reuse. They are withheld to avoid making the technique easier to operationalize or weaponize.

As a result, the files in this repository are **incomplete and are not expected to build or run as provided**. This README does not provide replacement implementations or instructions for recreating the omitted components.

## Security notice

The remaining C source includes an opaque, hard-coded byte array. The program's demonstration logic uses that data in an executable-memory and thread-creation flow. Its purpose and provenance have not been documented or independently verified. Treat it as untrusted code.

Do not build or execute this sample on a normal workstation. For defensive review, inspect the source statically. Any authorized dynamic analysis should be performed by qualified analysts in an isolated, disposable environment.

## High-level overview

The C source explores locating `ntdll.dll` in the current process, searching its exports, and attempting to derive an SSN from a native API stub. The omitted assembly component was intended to provide the syscall-dispatch routine. The sample references native memory-management and thread-creation operations.

These techniques rely on undocumented Windows internals and may vary across Windows versions. This description is intended to explain the subject of the research, not to recommend or enable its use.

## Demo

![Project demo](demo.gif)

## Included files

| File | Description |
| --- | --- |
| `halo.c` | Research code for module/export lookup and SSN-resolution logic. It also contains the unverified byte array described above. |
| `banner.jpeg` | Project banner displayed at the top of this README. |
| `demo.gif` | Animated project demonstration. |

## Limitations

- The implementation depends on undocumented structures, export layouts, and syscall-stub byte patterns that may change between Windows builds.
- It has not been validated as a reliable or complete resolver across Windows versions.
- The source has incomplete bounds checking and error handling and should be treated as experimental.
- The published source is intentionally incomplete because supporting files are omitted.
- No supported Windows-version matrix, automated tests, or verified benign payload is provided.
- No license file is included; reuse and redistribution terms are unspecified.

## Disclaimer

This material is provided for educational and defensive research. Use and analysis must comply with applicable laws, policies, and authorization requirements. The authors provide no warranty and accept no liability for use or misuse.
