
add_library(engine_core STATIC)

target_sources(engine_core PRIVATE
  "src/Game.cpp"
  "include/Game.hpp"
)

target_include_directories(engine_core PUBLIC
  "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

target_link_libraries(engine_core PUBLIC
  "sfml-graphics"
  "sfml-window"
  "sfml-system"
)

set_target_properties(engine_core PROPERTIES
  CXX_STANDARD 20
  CXX_STANDARD_REQUIRED ON
  CXX_EXTENSIONS OFF
)
