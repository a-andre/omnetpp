set(SRCS
    basicspringembedderlayout.cc
    concentrictreeembedding.cc
    forcedirectedembedding.cc
    forcedirectedgraphlayouter.cc
    forcedirectedparametersbase.cc
    forcedirectedparameters.cc
    geometry.cc
    graphcomponent.cc
    graphlayouter.cc
    heapembedding.cc
    startreeembedding.cc
)

add_library(opplayout ${SRCS})
target_link_libraries(oppcommon)
