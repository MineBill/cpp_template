include_directories(include)

set(SOURCE_FILES main.cpp)
set(HEADER_FILES)

add_executable({{exe_name}} ${SOURCE_FILES} ${HEADER_FILES})
target_link_libraries( 
    {{exe_name}}
    PRIVATE 
    project_options 
    project_warnings)