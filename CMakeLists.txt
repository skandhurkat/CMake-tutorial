cmake_minimum_required(VERSION 2.8)
project("CMake tutorial")

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
if(WIN32)
	set(CMAKE_INSTALL_RPATH ${EXECUTABLE_OUTPUT_PATH})
else()
	set(CMAKE_INSTALL_RPATH ${PROJECT_BINARY_DIR}/lib)
endif()

if(${CMAKE_CXX_COMPILER_ID} STREQUAL "GNU")
	if(CMAKE_CXX_COMPILER_VERSION GREATER 4.7 OR
	   CMAKE_CXX_COMPILER_VERSION EQUAL 4.7)
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pedantic -Wall -Wextra")
		set(CMAKE_CXX_FLAGS_DEBUG "-O0 -g")
		set(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O3 -g")
		set(CMAKE_CXX_FLAGS_RELEASE "-O3")
	else()
		message(FATAL_ERROR
			"This project requires g++ 4.7 or higher")
	endif()
elseif(${CMAKE_CXX_COMPILER_ID} STREQUAL "Clang")
	if(CMAKE_CXX_COMPILER_VERSION GREATER 3.3 OR
	   CMAKE_CXX_COMPILER_VERSION EQUAL 3.3)
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pedantic -Wall -Wextra")
		set(CMAKE_CXX_FLAGS_DEBUG "-O0 -g")
		set(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O3 -g")
		set(CMAKE_CXX_FLAGS_RELEASE "-O3")

	else()
		message(FATAL_ERROR
			"This project requires clang 3.3 or higher")
	endif()
elseif(${MSVC})
	if(CMAKE_CXX_COMPILER_VERSION GREATER 14 OR
			CMAKE_CXX_COMPILER_VERSION EQUAL 14)
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /Za")
		set(CMAKE_CXX_FLAGS_DEBUG "/DEBUG /Od")
		set(CMAKE_CXX_FLAGS_RELWITHDEBINFO "/DEBUG /O2")
		set(CMAKE_CXX_FLAGS_RELEASE "/O2")
	else()
		message(FATAL_ERROR
			"This project requires Visual Studio 14 or higher")
	endif()
else()
	message(FATAL_ERROR
		"Unsupported compiler, please add configuration here")
endif()

subdirs(src)
