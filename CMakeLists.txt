cmake_minimum_required(VERSION 3.16..3.16) # TODO find proper version

project(OMNeT++ VERSION 6.1)

option(BUILD_SHARED_LIBS "Build using shared libraries" ON)

include_directories(include src/ ${CMAKE_CURRENT_BINARY_DIR}/include ${CMAKE_CURRENT_BINARY_DIR}/src)

configure_file(include/omnetpp/platdep/config.h.in include/omnetpp/platdep/config.h)

add_subdirectory(src/cmdenv)
add_subdirectory(src/common)
add_subdirectory(src/envir)
add_subdirectory(src/eventlog)
add_subdirectory(src/layout)
add_subdirectory(src/nedxml)
add_subdirectory(src/scave)
add_subdirectory(src/sim)

#if WITH_QTENV
add_subdirectory(src/qtenv)
#endif

#add_subdirectory(src/utils)
