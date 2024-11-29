#set(CMAKE_AUTOMOC ON)
#set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


find_package(Qt5 COMPONENTS Widgets)

set(SRCS
    animationcontrollerdialog.cc
    areaselectordialog.cc
    arrow.cc
    canvasinspector.cc
    canvasrenderer.cc
    canvasviewer.cc
    chartgriditem.cc
    charttickdecimal.cc
    comboselectiondialog.cc
    componenthistory.cc
    compoundmoduleitem.cc
    connectionitem.cc
    displaystringaccess.cc
    displayupdatecontroller.cc
    exponentialspinbox.cc
    figurerenderers.cc
    fileeditor.cc
    findobjectsdialog.cc
    genericobjectinspector.cc
    genericobjecttreemodel.cc
    genericobjecttreenodes.cc
    graphicsitems.cc
    highlighteritemdelegate.cc
    histograminspector.cc
    histograminspectorconfigdialog.cc
    histogramview.cc
    imagecache.cc
    inspector.cc
    inspectorfactory.cc
    inspectorutil.cc
    iosgviewer.cc
    layersdialog.cc
    layouterenv.cc
    logbuffer.cc
    logfilterdialog.cc
    logfinddialog.cc
    loginspector.cc
    mainwindow.cc
    messageanimations.cc
    messageanimator.cc
    messageitem.cc
    messageprintertagsdialog.cc
    modulecanvasviewer.cc
    moduleinspector.cc
    modulelayouter.cc
    objectlistmodel.cc
    objectlistview.cc
    objecttreeinspector.cc
    osgcanvasinspector.cc
    outputvectorinspector.cc
    outputvectorinspectorconfigdialog.cc
    outputvectorview.cc
    preferencesdialog.cc
    qtenvapp.cc
    qtenvenvir.cc
    qtutil.cc
    runselectiondialog.cc
    rununtildialog.cc
    stopdialog.cc
    submoduleitem.cc
    textviewerproviders.cc
    textviewerwidget.cc
    timelinegraphicsview.cc
    timelineinspector.cc
    vectorplotitem.cc
    videorecordingdialog.cc
    watchinspector.cc
)

add_library(oppqtenv ${SRCS})
target_link_libraries(oppqtenv PRIVATE Qt5::Widgets oppnedxml)
target_compile_definitions(oppqtenv PRIVATE QT_NO_KEYWORDS)
target_include_directories(oppqtenv PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
