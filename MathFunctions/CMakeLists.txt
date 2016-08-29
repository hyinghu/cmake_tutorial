# first we add the executable that generates the table
add_executable(MakeTable MakeTable.cpp)

# add the command to generate the source code
add_custom_command(
	OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/Table.h
	DEPENDS MakeTable
	COMMAND MakeTable
	ARGS ${CMAKE_CURRENT_BINARY_DIR}/Table.h
)

set_source_files_properties(
	mysqrt.cpp PROPERTIES
	OBJECT_DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/Table.h
)

# add the binary tree directory to the search path for incilude files
include_directories(${CMAKE_CURRENT_BINARY_DIR})

# add the main library
add_library(MathFunctions SHARED mysqrt.cpp)

install(TARGETS MathFunctions DESTINATION lib)
install(FILES MathFunctions.h DESTINATION include)
