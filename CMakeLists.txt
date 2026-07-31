cmake_minimum_required(VERSION 3.26)

add_library(matlib INTERFACE)

include(FetchContent)

FetchContent_Declare(
	veclib
	GIT_REPOSITORY https://github.com/ms1d/veclib
	GIT_TAG main
)

FetchContent_Declare(
    commonlib
    GIT_REPOSITORY https://github.com/ms1d/commonlib
    GIT_TAG        main
)

FetchContent_MakeAvailable(veclib commonlib)

target_include_directories(matlib INTERFACE include)
target_link_libraries(matlib INTERFACE commonlib veclib)

if (BUILD_TESTS)
    add_subdirectory(test)
endif()
