cmake_minimum_required(VERSION 3.28)
project(MySFMLProject LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(MY_SOURCES
    src/aux_func.cpp
    src/aggreg.cpp
    src/pause_core.cpp
    src/autoscale.cpp
    src/colors.cpp
    src/dbg_report.cpp
    src/garbage_coll.cpp
    src/demo_func.cpp
    src/draw.cpp
    src/frames_count.cpp
    src/light.cpp
    src/logtxt.cpp
    src/cfg_toml.cpp
    src/main.cpp
    src/match_col.cpp
    src/opt_lyra.cpp
    src/progress.cpp
    src/picture.cpp
    src/recurrence.cpp
    src/real_time.cpp
    src/screen_size.cpp
    src/mut_grow.cpp
    src/text_draw.cpp
    src/transform.cpp
    src/vec2angle.cpp
    src/vec2rotate.cpp
    src/fluctuate.cpp
)

add_library(Lyra_lib INTERFACE)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 3.1.0
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

include(FetchContent)
FetchContent_Declare(
    tomlplusplus
    GIT_REPOSITORY https://github.com/marzer/tomlplusplus.git
    GIT_TAG        v3.4.0
)
FetchContent_MakeAvailable(tomlplusplus)

# Attach the include directory to the target's interface
target_include_directories(Lyra_lib INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/subprojects/Lyra/include
)

# Only for MSVC compiler
if(MSVC)
    add_compile_options(/permissive-)
endif()

# Example add library: target_link_libraries(MyApp tomlplusplus::tomlplusplus)
add_executable(cosfra ${MY_SOURCES})
target_compile_features(cosfra PRIVATE cxx_std_17)
target_link_libraries(cosfra PRIVATE SFML::Graphics tomlplusplus::tomlplusplus Lyra_lib)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT cosfra)
