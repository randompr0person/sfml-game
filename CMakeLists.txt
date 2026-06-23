
cmake_minimum_required(VERSION 3.16)
project(game LANGUAGES CXX)

if(CMAKE_VERSION VERSION_GREATER_EQUAL 4)
    set(CMAKE_POLICY_VERSION_MINIMUM 3.5)
endif()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")

# ----- dependencies -----
add_subdirectory(external "${CMAKE_BINARY_DIR}/intermediate/external")
add_subdirectory(libs "${CMAKE_BINARY_DIR}/intermediate/libs")
# add_subdirectory(tools "${CMAKE_BINARY_DIR}/intermediate/tools")
# ------------------------

# ----- game -----
add_executable(game
    src/main.cpp
)

file(MAKE_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_link_directories(game PRIVATE
    "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

target_link_libraries(game PRIVATE
    "sfml-graphics"
    "sfml-window"
    "sfml-system"

    "engine_core"
)
# ----------------

# ----- assets -----
file(MAKE_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/assets")
add_custom_command(OUTPUT ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/assets
    COMMAND ${CMAKE_COMMAND} -E create_symlink 
    ${CMAKE_CURRENT_SOURCE_DIR}/assets 
    ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/assets
)
# ------------------
