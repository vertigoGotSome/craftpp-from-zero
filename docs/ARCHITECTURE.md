# Architecture and development tools

C++ is the implementation language. Windows x64 comes first and the planned executable is `craftpp.exe`. Linux is a future platform. Keep platform dependencies at narrow boundaries when implementation begins.

The NTLVD layout reserves `src/`, `tests/`, `scripts/` and `docs/`. Keep local research and scratch files in ignored `work/`. Use the configured external NTLVD worktree root for task branches.

## IDE preparation

- **Visual Studio:** Use Desktop development with C++, x64 MSVC tools, a Windows SDK and C++ CMake tools for Windows. Open the repository folder when the CMake project exists.
- **Visual Studio Code:** Use Microsoft C/C++ and CMake Tools with the same MSVC toolchain and an accessible CMake installation. The workspace recommends these extensions.
- **Build plan:** Prefer CMake with checked-in shared presets, out-of-source builds and ignored local overrides. Validate configure, build and test entry points in both IDEs after real targets exist.

The C++ language standard, minimum tool versions, generator, Windows SDK baseline, dependency strategy and rendering backend are open. Evaluate Vulkan against credible alternatives for portability, driver support, tooling and workload needs. Record the decision with evidence before committing the implementation to a backend.
