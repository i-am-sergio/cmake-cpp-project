add_library(myLibrary SHARED
    myLibrary.h
    myLibrary.cpp
)

target_include_directories(myLibrary PUBLIC 
    ${CMAKE_CURRENT_LIST_DIR})