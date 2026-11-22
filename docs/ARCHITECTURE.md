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

Start with the block IDs and a fixed-size grid initialized to air. Read and write by integer coordinates. Return air for an out-of-bounds read and report failure on an out-of-bounds write. Test that setting and removing a block preserves neighboring cells. Once the grid is implemented, add an executable test project to the solution and verify the grid tests. The first visible scene can use three solid colors while the original tiles are being drawn.

## Windows development

Install Visual Studio 2026 with Desktop development with C++, the x64 MSVC v145 toolset and a Windows 10 or 11 SDK. Open [CraftPP.sln](../CraftPP.sln) as a solution. Select Debug and x64 to develop, then choose Build Solution (Ctrl+Shift+B). The World filter contains the three starter files. Use the C++ project property pages to inspect the configured compiler settings.

The static library uses C++17, Unicode, UTF-8 source, MSVC conformance mode and warning level 4. Debug emits compiler debug information. Release enables speed optimization. From a Visual Studio Developer PowerShell at the repository root, build with:

```powershell
msbuild CraftPP.sln /t:Build /p:Configuration=Debug /p:Platform=x64
msbuild CraftPP.sln /t:Build /p:Configuration=Release /p:Platform=x64
```

The output is `out/x64/<configuration>/CraftPPWorld.lib`. Add an executable project when there is an entry point to run. Visual Studio Code can edit the same files and run MSBuild from the developer shell. Keep the world code portable for later Linux support.

The dependency strategy and rendering backend are open. Evaluate Vulkan and alternatives for portability, driver support, tooling and workload needs.
