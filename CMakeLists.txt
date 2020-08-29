cmake_minimum_required(VERSION 3.15)
project({{project_name}})

include(cmake/StandardProjectSettings.cmake)

add_library(project_options INTERFACE )
target_compile_features(project_options INTERFACE cxx_std_17) 

add_library(project_warnings INTERFACE)

set(WARNINGS_AS_ERRORS OFF)
include(cmake/CompilerWarnings.cmake)
set_project_warnings(project_warnings)

include(cmake/Sanitizers.cmake)
enable_sanitizers(project_options)

option(BUILD_SHARED_LIBS "Enable compilation of shared libraries" OFF)

option(ENABLE_PCH "Enable precompiled headers" OFF)
if(ENABLE_PCH)
    target_precompile_headers(
        project_options
        INTERFACE
        <vector>
        <map>
        <string>
        <utility>
    )
endif()

add_subdirectory(src)