# sdl-deps

My SDL2 / Game Programming Dependencies. 

---
#### Steps:

Clone this into your repo using: `git submodule add git@github.com:conner-calhoun/sdl-deps.git deps` 

**OR** 

`git clone git@github.com:conner-calhoun/sdl-deps.git deps` if you are not using a git repo.

...

Then make sure your `CMakeLists.txt` matches what is below.

---
#### CMakeLists.txt


```CMake
cmake_minimum_required(VERSION 3.10)
project(ProjectName VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(SDL2_DIR ${CMAKE_CURRENT_LIST_DIR}/deps/SDL2-2.0.16)
find_package(SDL2 REQUIRED)

set(SRCS
    src/main.cpp)

add_executable(${PROJECT_NAME} ${SRCS})

target_include_directories(${PROJECT_NAME}
PUBLIC
    src/

    # Deps
    deps/
    deps/stb/
    deps/nlohman/
    ${SDL2_INCLUDE_DIRS}
)

target_link_libraries(${PROJECT_NAME}
    ${SDL2_LIBRARIES}
)
```

---
#### In a single cpp file, you will need to initialize stb:

```c++
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
```
