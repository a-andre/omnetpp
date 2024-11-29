set(SRCS
    akaroarng.cc
    akoutvectormgr.cc
    appbase.cc
    appreg.cc
    args.cc
    configuration.cc
    debuggersupport.cc
    envirutils.cc
    eventlogfilemgr.cc
    evmain.cc
    filesnapshotmgr.cc
    fsutils.cc
    genericenvir.cc
    genericeventlooprunner.cc
    ifakegui.cc
    inifilecontents.cc
    inifilereader.cc
    intervals.cc
    logformatter.cc
    matchablefield.cc
    matchableobject.cc
    objectprinter.cc
    omnetppoutscalarmgr.cc
    omnetppoutvectormgr.cc
    resultfileutils.cc
    scenario.cc
    speedometer.cc
    sqliteoutscalarmgr.cc
    sqliteoutvectormgr.cc
    startup.cc
    valueiterator.cc
    visitor.cc
    xmldoccache.cc
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_SOURCE_DIR}/eventlogwriter.h ${CMAKE_CURRENT_SOURCE_DIR}/eventlogwriter.cc
    COMMAND  perl eventlogwriter.pl
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

add_library(oppenvir ${SRCS} eventlogwriter.cc)

target_compile_definitions(oppenvir PRIVATE
    LIBSUFFIX=""
    OMNETPP_IMAGE_PATH="${CMAKE_SOURCE_DIRECTORY}/images"
) # FIXME

target_link_libraries(oppenvir PRIVATE oppsim)

if(BUILD_SHARED_LIBS)
    add_executable(opp_run main.cc)
    target_link_libraries(opp_run PRIVATE oppenvir)
else()
    add_library(oppmain main.cc)
    target_link_libraries(oppmain PRIVATE oppenvir)
endif()

