xbox-swizzle
---

nv2a texture swizzling routines extracted from [xemu](https://xemu.app).


## Including in CMake-based projects

This project is expected to be used as a dependency of other projects.

You can include it via `FetchContent`. In your `CMakeLists.txt` file:

```cmake
include(FetchContent)

FetchContent_Declare(
        xbox-swizzle
        GIT_REPOSITORY https://github.com/abaire/xbox-swizzle.git
        GIT_TAG        main
)

FetchContent_MakeAvailable(xbox-swizzle)
```
