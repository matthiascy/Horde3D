set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Qt5 COMPONENTS Widgets Gui Core Xml OpenGL)
if( Qt5_FOUND )
    SET(QT_LIBRARIES "Qt5::Widgets;Qt5::Gui;Qt5::Core;Qt5::Xml;Qt5::OpenGL")
    FUNCTION(QT4_ADD_RESOURCES)
    ENDFUNCTION(QT4_ADD_RESOURCES)
else()
    find_package(Qt4 REQUIRED QtGui QtXml QtOpenGL QtCore)
    SET(QT_LIBRARIES "Qt4::QtGui;Qt4::QtXml;Qt4::QtCore;Qt4::QtOpenGL")
endif()

FIND_PACKAGE(Lua REQUIRED)

add_subdirectory(src/EditorLib)
add_subdirectory(src/QPropertyEditor)
add_subdirectory(src/QXmlTree)
add_subdirectory(src/tgaPlugIn)
add_subdirectory(src/psdPlugIn)
add_subdirectory(src/HordeSceneEditorCore)
add_subdirectory(src/HordeSceneEditor)

if(HORDE3D_BUILD_TERRAIN)
    add_subdirectory(src/QTerrainNodeExtension)
    add_subdirectory(src/TerrainToolPlugIn)
endif(HORDE3D_BUILD_TERRAIN)
