PROJECT(sqstdlib)

SET(CMAKE_CXX_FLAGS "-O2 -fno-exceptions -fno-rtti -Wall -fno-strict-aliasing")

IF("${CMAKE_SIZEOF_VOID_P}" EQUAL "8")
    SET(CMAKE_CXX_FLAGS "-m64 -D_SQ64 ${CMAKE_CXX_FLAGS}")
ELSE() # Build for 32-bit instead.
    SET(CMAKE_CXX_FLAGS "-m32 ${CMAKE_CXX_FLAGS}")
ENDIF("${CMAKE_SIZEOF_VOID_P}" EQUAL "8")

INCLUDE_DIRECTORIES(
    ${CMAKE_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}
)

ADD_LIBRARY(${PROJECT_NAME} STATIC
    sqstdblob.cpp
    sqstdio.cpp
    sqstdstream.cpp
    sqstdmath.cpp
    sqstdsystem.cpp
    sqstdstring.cpp
    sqstdaux.cpp
    sqstdrex.cpp
)

INSTALL(TARGETS ${PROJECT_NAME} DESTINATION lib)
