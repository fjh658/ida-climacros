cmake_minimum_required(VERSION 3.1)
project(ida-climacros)

include("ida-cmake/cmake/IDA.cmake")

set(CMAKE_CXX_STANDARD 17)

set(sources 
      "utils_impl.hpp"
			"climacros.cpp")

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "AppleClang")
	# using AppleClang
	set(CMAKE_C_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")
	set(CMAKE_CXX_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")

elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
  # using Clang
  set(CMAKE_C_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")
  set(CMAKE_CXX_FLAGS "-DUSE_DANGEROUS_FUNCTIONS=1 -DUSE_STANDARD_FILE_FUNCTIONS=1")

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  	# using GCC
  	# TODO

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Intel")
  # using Intel C++
  # TODO

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
  # using Visual Studio C++
  # TODO
endif()

add_ida_plugin(${CMAKE_PROJECT_NAME} ${sources})
