PROJECT(sq)

SET(CMAKE_CXX_FLAGS "-O2 -fno-exceptions -fno-rtti")

IF("${CMAKE_SIZEOF_VOID_P}" EQUAL "8")
    SET(CMAKE_CXX_FLAGS "-m64 -D_SQ64 ${CMAKE_CXX_FLAGS}")
ELSE() # Build for 32-bit instead.
    SET(CMAKE_CXX_FLAGS "-m32 ${CMAKE_CXX_FLAGS}")
ENDIF("${CMAKE_SIZEOF_VOID_P}" EQUAL "8")

INCLUDE_DIRECTORIES(
    ${CMAKE_SOURCE_DIR}/include
)

ADD_EXECUTABLE(${PROJECT_NAME} sq.c)

TARGET_LINK_LIBRARIES(${PROJECT_NAME} squirrel sqstdlib)
