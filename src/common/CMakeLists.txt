find_package(SQLite3)

set(SRCS
    any_ptr.cc
    backward.cc
    bigdecimal.cc
    colorutil.cc
    commonutil.cc
    csvwriter.cc
    enumstr.cc
    exception.cc
    expression.cc
    exprnode.cc
    exprnodes.cc
    exprvalue.cc
    fileglobber.cc
    filelock.cc
    filereader.cc
    fileutil.cc
    fnamelisttokenizer.cc
    formattedprinter.cc
    intutil.cc
    jsonwriter.cc
    lcgrandom.cc
    linetokenizer.cc
    matchexpression.cc
    matchexpressionlexer.cc
    omnetppscalarfilewriter.cc
    omnetppvectorfilewriter.cc
    patternmatcher.cc
    pooledstring.cc
    quantityformatter.cc
    rwlock.cc
    saxparser_default.cc
    saxparser_libxml.cc
    saxparser_yxml.cc
    sqliteresultfileschema.cc
    sqlitescalarfilewriter.cc
    sqlitevectorfilewriter.cc
    statistics.cc
    stringpool.cc
    stringtokenizer.cc
    stringutil.cc
    unitconversion.cc
)

configure_file(ver.h.base ver.h)
file(APPEND ${CMAKE_CURRENT_BINARY_DIR}/ver.h
"
#define OMNETPP_PRODUCT \"${CMAKE_PROJECT_NAME}\"
#define OMNETPP_VERSION_STR \"${CMAKE_PROJECT_VERSION}\"
#define OMNETPP_BUILDID \"TODO (241008-f7568267cd)\"
#define OMNETPP_EDITION \"Academic Public License -- NOT FOR COMMERCIAL USE\"
#define OMNETPP_RELEASE \"omnetpp-${CMAKE_PROJECT_VERSION}\"
"
)

add_custom_command(
    OUTPUT matchexpression.tab.h matchexpression.tab.cc
    COMMAND  yacc -o matchexpression.tab.cc --no-lines --defines=matchexpression.tab.h -p matchexpressionyy -d ${CMAKE_CURRENT_SOURCE_DIR}/matchexpression.y
)

add_library(oppcommon ${SRCS} matchexpression.tab.cc)

target_include_directories(oppcommon PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})

target_link_libraries(oppcommon SQLite::SQLite3)
