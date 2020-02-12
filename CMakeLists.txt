cmake_minimum_required( VERSION 2.6 )

if(NOT WIN32)
  string(ASCII 27 ESC)
  set( NORM "${ESC}[39m" )
  set( RED  "${ESC}[31m" ) 
  set( GRN  "${ESC}[32m" )
  set( CYN  "${ESC}[36m" )
  set( MAG  "${ESC}[35m" )
  set( YEL  "${ESC}[33m" )
  set( BLU  "${ESC}[34m" )
endif()

### Add this options before PROJECT keyword
set( CMAKE_DISABLE_IN_SOURCE_BUILD ON )
set( CMAKE_DISABLE_SOURCE_CHANGES  ON )

if( "${CMAKE_SOURCE_DIR}" STREQUAL "${CMAKE_BINARY_DIR}" )
  message( SEND_ERROR "In-source builds are not allowed." )
endif ()

project( Tools LANGUAGES C CXX )

# The version number.
set( ${CMAKE_PROJECT_NAME}_VERSION_MAJOR 1 )
set( ${CMAKE_PROJECT_NAME}_VERSION_MINOR 0 )

set( CMAKE_VERBOSE_MAKEFILE ON )
set( CMAKE_COLOR_MAKEFILE ON )

###########
### Library
###########
message( "${CYN}Configuring library : ${PROJECT_NAME}${NORM}" )
add_library( ${PROJECT_NAME} INTERFACE )
target_include_directories(
    ${PROJECT_NAME}
INTERFACE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)
