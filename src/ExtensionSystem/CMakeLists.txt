cmake_minimum_required(VERSION 2.9)
project(QtilitiesExtensionSystem)

set(SOURCE_FILES
        source/ExtensionSystemConfig.cpp 
        source/ExtensionSystemCore.cpp 
        source/PluginInfoWidget.cpp 
        source/PluginTreeModel.cpp 
	)

set(HEADER_FILES
        source/ExtensionSystemConfig.h 
        source/ExtensionSystemConstants.h 
        source/ExtensionSystemCore.h 
        source/ExtensionSystem_global.h 
        source/IPlugin.h 
        source/PluginInfoWidget.h 
        source/PluginTreeModel.h 
	)

set(UI_FILES 
        source/ExtensionSystemConfig.ui 
        source/PluginInfoWidget.ui 
	)
	
set(QRC_FILES 
	)

add_definitions(-DEXTENSION_SYSTEM_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesLogging QtilitiesCore QtilitiesCoreGui
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
)
#need xml?

set_target_properties(${PROJECT_NAME} PROPERTIES 
	AUTOMOC ON
    AUTORCC ON
    AUTOUIC ON
)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
