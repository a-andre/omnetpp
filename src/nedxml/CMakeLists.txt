set(SRCS
    astbuilder.cc
    astnode.cc
    dtdvalidationutils.cc
    errorstore.cc
    exception.cc
    msganalyzer.cc
    msgcodegenerator.cc
    msgcompiler.cc
    msggenerator.cc
    msgparser.cc
    msgtypetable.cc
    msgyyutil.cc
    nedcrossvalidator.cc
    nedgenerator.cc
    nedparser.cc
    nedresourcecache.cc
    nedsyntaxvalidator.cc
    nedtools.cc
    nedtypeinfo.cc
    nedutil.cc
    nedyyutil.cc
    opp_msgtool.cc
    opp_nedtool.cc
    sourcedocument.cc
    xmlastparser.cc
    xmlgenerator.cc
    yyutil.cc
)

add_custom_command(
    OUTPUT nedelements.h nedelements.cc
    COMMAND perl ${CMAKE_CURRENT_SOURCE_DIR}/dtdclassgen.pl ${CMAKE_SOURCE_DIR}/doc/etc/ned2.dtd ned
)

add_custom_command(
    OUTPUT msgelements.h msgelements.cc
    COMMAND perl ${CMAKE_CURRENT_SOURCE_DIR}/dtdclassgen.pl ${CMAKE_SOURCE_DIR}/doc/etc/msg2.dtd msg
)

add_library(oppnedxml ${SRCS} nedelements.cc msgelements.cc)

target_include_directories(oppnedxml PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})
