add_library(engine_core STATIC)

target_sources(engine_core PRIVATE
  "Core/Game.cpp"
  "Core/Game.hpp"
)

target_link_libraries(engine_core PRIVATE
  "sfml-graphics"
  "sfml-window"
  "sfml-system"
)

set_target_properties(engine_core PROPERTIES
  CXX_STANDARD 20
  CXX_STANDARD_REQUIRED ON
  CXX_EXTENSIONS OFF
)
