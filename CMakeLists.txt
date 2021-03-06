CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

OPTION(USE_STATIC_RUNTIME "Use the static MSVC runtime." OFF)

IF("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC" AND USE_STATIC_RUNTIME)
    SET(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} /MTd")
    SET(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")

    SET(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} /MT")
    SET(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
ELSEIF("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC" AND USE_STATIC_RUNTIM)
    SET(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} /MDd")
    SET(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MDd")

    SET(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} /MD")
    SET(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MD")
ENDIF("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC" AND USE_STATIC_RUNTIME)

if( "${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC" )
  set( CMAKE_C_FLAGS_RELWITHDEBINFO "${CMAKE_C_FLAGS_RELWITHDEBINFO} /Z7" )
  set( CMAKE_CXX_FLAGS_RELWITHDEBINFO "${CMAKE_CXX_FLAGS_RELWITHDEBINFO} /Z7" )
endif()

ADD_SUBDIRECTORY(squirrel)
ADD_SUBDIRECTORY(sqstdlib)
ADD_SUBDIRECTORY(sq)
ADD_SUBDIRECTORY(include)
