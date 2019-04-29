cmake_minimum_required(VERSION 2.8.3)
project(post_build_example)

set( POST_BUILD_EXAMPLE post_build_example )

set( CMAKE_BINARY_DIR ${CMAKE_CURRENT_SOURCE_DIR}/bin )
set( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR} )

add_executable(
    ${POST_BUILD_EXAMPLE}
    src/main.cpp
)


# Important points for run custom command:
# 1. TARGET must be build in current project. Easiest way is set it by builded lib or bin file;
# 2. POST_BUILD flag says that that step must be performed after build;
# 3. COMMAND with required command. In example we just execute just builded bin file
# 4. COMMENT is optional, shows additional info in build log

add_custom_command(
    TARGET ${POST_BUILD_EXAMPLE}
    POST_BUILD
    COMMAND ${CMAKE_BINARY_DIR}/${POST_BUILD_EXAMPLE}
    COMMENT "Pefroming post_build step"
)