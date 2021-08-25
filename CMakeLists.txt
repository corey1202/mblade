cmake_minimum_required(VERSION 3.10)

project(mblade)

include(cmake/BuildOptions.cmake)
include(cmake/PackageConfig.cmake)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/libs)

set(BASE_PROJECT_PATH ${PROJECT_SOURCE_DIR})

set(DEPENDS_ROOT_PATH ${PROJECT_SOURCE_DIR}/depends)

set(DEPENDS_SOURCE_PATH ${PROJECT_SOURCE_DIR}/depends/lib)

if(OS_TYPE_DARWIN)
    set(DEPENDS_LIBRARY_PATH ${PROJECT_SOURCE_DIR}/depends/darwin)
elseif(OS_TYPE_WINDOWS)
    set(DEPENDS_LIBRARY_PATH ${PROJECT_SOURCE_DIR}/depends/windows)
else()
    set(DEPENDS_LIBRARY_PATH ${PROJECT_SOURCE_DIR}/depends/linux)
endif()

add_subdirectory("src")

if(BUILD_COSMOS_FLAG)
    add_subdirectory("cosmos")
endif()
