project( cmakeVersionExample )
cmake_minimum_required( VERSION 3.0 )
include (cmake/git_version.cmake)

git_version()

message( STATUS "\tGit version string: ${GIT_VERSION_STRING}")


file( GLOB_RECURSE cmakeVersionExample_sources ${CMAKE_CURRENT_SOURCE_DIR}/src/*.[ch]pp )

add_executable( ${PROJECT_NAME} ${cmakeVersionExample_sources} )

target_compile_definitions( ${PROJECT_NAME} PUBLIC GIT_VERSION_STRING=${GIT_VERSION_STRING} )

set_target_properties( ${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES )
