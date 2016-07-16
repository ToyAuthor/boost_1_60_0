project(boost)
cmake_minimum_required(VERSION 2.8)

set( BOOST_ROOT_SOURCE_DIR     ${PROJECT_SOURCE_DIR} )
set( BOOST_ROOT_BINARY_DIR     ${PROJECT_BINARY_DIR} )
set( BOOST_LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR} )

# Choose a path of your boost header files.
# For example:
# set(BOOST_INCLUDE_DIR "D:/sdk/boost" )
# set(BOOST_INCLUDE_DIR "~/sdk/boost" )

if( NOT DEFINED BOOST_INCLUDE_DIR)
	message("You have to define BOOST_INCLUDE_DIR to choose a path of your boost header files.")
endif()

option(BOOST_BUILD_SHARED_LIBS "Build shared library" OFF)

link_directories(${BOOST_LIBRARY_OUTPUT_PATH})

if(BOOST_BUILD_SHARED_LIBS)
	set(BOOST_LIBRARY_TYPE SHARED)
else()
	set(BOOST_LIBRARY_TYPE STATIC)
endif()

# Disable auto link.
add_definitions(-DBOOST_ALL_NO_LIB)

add_subdirectory(libs)
