# Architecture and development tools

C++ is the implementation language. Windows x64 comes first and the planned executable is `craftpp.exe`. Linux is a future platform. Keep platform dependencies at narrow boundaries when implementation begins.

The NTLVD layout reserves `src/`, `tests/`, `scripts/` and `docs/`. Keep local research and scratch files in ignored `work/`. Use the configured external NTLVD worktree root for task branches.

## File layout for the first playable slice

| Location | Responsibility |
| --- | --- |
| `src/world/block_type.hpp` | Define block IDs such as `Air`, `Grass`, `RoughStone` and `WoodPlanks`. |
| `src/world/voxel_grid.hpp` and `voxel_grid.cpp` | Store block IDs in a dense 3D grid and handle coordinate bounds. |
| `tests/world/voxel_grid_tests.cpp` | Check the initial state, block changes and out-of-bounds coordinates. |
| `src/main.cpp` | Start the application and later wire the game loop together. |
| `src/rendering/` | Future mesh generation and drawing. Add the directory when rendering work begins. |
| `assets/textures/blocks/` | Runtime-ready block textures. See [Game assets](../assets/README.md). |

Start with the block IDs and a fixed-size grid initialized to air. Read and write by integer coordinates. Return air for an out-of-bounds read and report failure on an out-of-bounds write. Test that setting and removing a block preserves neighboring cells. Once there is real code to compile, add a CMake target and verify the grid tests. The first visible scene can use three solid colors while the original tiles are being drawn.

## IDE preparation

- **Visual Studio:** Use Desktop development with C++, x64 MSVC tools, a Windows SDK and C++ CMake tools for Windows. Open the repository folder when the CMake project exists.
- **Visual Studio Code:** Use Microsoft C/C++ and CMake Tools with the same MSVC toolchain and an accessible CMake installation. The workspace recommends these extensions.
- **Build plan:** Prefer CMake with checked-in shared presets, out-of-source builds and ignored local overrides. Validate configure, build and test entry points in both IDEs after real targets exist.

The C++ language standard, minimum tool versions, generator, Windows SDK baseline, dependency strategy and rendering backend are open. Evaluate Vulkan against credible alternatives for portability, driver support, tooling and workload needs. Record the decision with evidence before committing the implementation to a backend.
