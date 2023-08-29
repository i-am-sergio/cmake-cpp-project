cmake_minimum_required(VERSION 3.27.3)

project("First CMake Project")

add_subdirectory(myLibrary)

add_executable(executable main.cpp)

target_link_libraries(executable 
    myLibrary)

add_custom_command(
    TARGET executable POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy
    ${CMAKE_CURRENT_LIST_DIR}/config/config.json
    ${CMAKE_CURRENT_BINARY_DIR} 
)

install(
    TARGETS executable 
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib    
)

install(
    FILES ${CMAKE_CURRENT_LIST_DIR}/config/config.json
    DESTINATION bin/config
)

install(
    PROGRAMS ${CMAKE_CURRENT_LIST_DIR}/scripts/launcher.sh
    DESTINATION bin
)
