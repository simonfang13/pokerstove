cmake_minimum_required(VERSION 2.6)

project(programs)

# set up boost
if (UNIX)
    message(status "building for unix")
    set(BOOST_LIBRARYDIR "/usr/local/lib/")
else()
    message(status ": building for non-unix -> windows")
    set(BOOST_ROOT "E:/code/ext/boost_1_53_0/")
    set(BOOST_LIBRARYDIR "E:/code/ext/boost_1_53_0/lib32-msvc-10.0/")
endif()
find_package(Boost COMPONENTS program_options REQUIRED)

message(status "** Boost Include: ${Boost_INCLUDE_DIR}")
message(status "** Boost Libraries: ${Boost_LIBRARY_DIRS}")
message(status "** Boost Libraries: ${Boost_LIBRARIES}")

include_directories(${Boost_INCLUDE_DIR})
link_directories(${Boost_LIBRARY_DIRS})

include_directories(../libs)

add_subdirectory(../libs libs)
add_subdirectory (pseval)
