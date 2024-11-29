set(SRCS
    cmdenvapp.cc
    cmdenvenvir.cc
    cmdenvnarrator.cc
    cmdenvsimulationrunner.cc
    fakegui.cc
)

add_library(oppcmdenv ${SRCS})
target_link_libraries(oppcmdenv oppnedxml)
