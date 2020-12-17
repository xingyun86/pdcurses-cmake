# CMakeList.txt : CMake project for FreeGlutUI, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

set(project_name "pdcurses")
project(${project_name})

#include(CheckIncludeFile)
#check_include_file(string.h HAVE_STRING_H)

#configure_file (
#  "${CMAKE_CURRENT_SOURCE_DIR}/config.h.in"
#  "${CMAKE_CURRENT_BINARY_DIR}/config.h"
#)
if(MSVC)
set(EXT_LIB ws2_32 iphlpapi)
else(MSVC)
endif(MSVC)
include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}
	${CMAKE_CURRENT_SOURCE_DIR}/common
)
link_directories(
	${CMAKE_CURRENT_BINARY_DIR}
)

file(GLOB SRCS "pdcurses/*.c")

if (MSVC)
include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/wincon
)
file(GLOB EXT_SRCS "wincon/*.c")
else(MSVC)
include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/x11
)
file(GLOB EXT_SRCS "x11/*.c")
endif(MSVC)
# Add source to this project's executable.
add_library (${project_name}_static ${SRCS} ${EXT_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_static PRIVATE _CRT_SECURE_NO_WARNINGS)
# firework
file(GLOB FIREWORK_SRCS "demos/firework.c")
add_executable (${project_name}_firework ${FIREWORK_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_firework PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_firework PRIVATE ${project_name}_static)

# firework
file(GLOB OZDEMO_SRCS "demos/ozdemo.c")
add_executable (${project_name}_ozdemo ${OZDEMO_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_ozdemo PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_ozdemo PRIVATE ${project_name}_static)

# rain
file(GLOB RAIN_SRCS "demos/rain.c")
add_executable (${project_name}_rain ${RAIN_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_rain PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_rain PRIVATE ${project_name}_static)

# testcurs
file(GLOB TESTCURS_SRCS "demos/testcurs.c")
add_executable (${project_name}_testcurs ${TESTCURS_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_testcurs PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_testcurs PRIVATE ${project_name}_static)

# worm
file(GLOB WORM_SRCS "demos/worm.c")
add_executable (${project_name}_worm ${WORM_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_worm PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_worm PRIVATE ${project_name}_static)

# xmas
file(GLOB XMAS_SRCS "demos/xmas.c")
add_executable (${project_name}_xmas ${XMAS_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_xmas PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_xmas PRIVATE ${project_name}_static)

# ptest
file(GLOB PTEST_SRCS "demos/ptest.c")
add_executable (${project_name}_ptest ${PTEST_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_ptest PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_ptest PRIVATE ${project_name}_static)

# tuidemo
file(GLOB TUIDEMO_SRCS "demos/tuidemo.c" "demos/tui.c")
add_executable (${project_name}_tuidemo ${TUIDEMO_SRCS})

if (MSVC)
	MESSAGE(STATUS "CMAKE_BUILD_TYPE=" ${CMAKE_BUILD_TYPE})

	set(CompilerFlags
		CMAKE_CXX_FLAGS
		CMAKE_CXX_FLAGS_DEBUG
		CMAKE_CXX_FLAGS_RELEASE
		CMAKE_C_FLAGS
		CMAKE_C_FLAGS_DEBUG
		CMAKE_C_FLAGS_RELEASE
		)
	foreach(CompilerFlag ${CompilerFlags})
		string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
	endforeach()
endif(MSVC)
target_compile_definitions(${project_name}_tuidemo PRIVATE _CRT_SECURE_NO_WARNINGS)
target_link_libraries(${project_name}_tuidemo PRIVATE ${project_name}_static)

if(MSVC)
#SET_TARGET_PROPERTIES(${project_name} PROPERTIES LINK_FLAGS ${ADMIN_LEVEL})
endif(MSVC)