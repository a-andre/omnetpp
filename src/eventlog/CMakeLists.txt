set(SRCS
    event.cc
    eventlog.cc
    eventlogentrycache.cc
    eventlogentry.cc
    eventlogindex.cc
    filteredevent.cc
    filteredeventlog.cc
    ichunk.cc
    ievent.cc
    ieventlog.cc
    index.cc
    messagedependency.cc
    opp_eventlogtool.cc
    snapshot.cc
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_SOURCE_DIR}/eventlogentries.h ${CMAKE_CURRENT_SOURCE_DIR}/eventlogentries.cc
        ${CMAKE_CURRENT_SOURCE_DIR}/eventlogentryfactory.cc
    COMMAND  perl eventlogentries.pl
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

add_library(oppeventlog ${SRCS} eventlogentries.cc eventlogentryfactory.cc)

target_include_directories(oppeventlog PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
