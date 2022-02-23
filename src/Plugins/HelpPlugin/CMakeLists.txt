cmake_minimum_required(VERSION 2.9)
project(QtilitiesHelpPlugin)


IF(QTILITIES_NO_HELP)
#do nothing for now
set(SOURCE_FILES
	)

set(HEADER_FILES
	)

set(UI_FILES  
	)
	
set(QRC_FILES 
	)
ELSEIF(QTILITIES_NO_HELP)
set(SOURCE_FILES
    source/Browser.cpp    
    source/ContentWidgetFactory.cpp    
    source/HelpMode.cpp    
    source/HelpPluginConfig.cpp    
    source/HelpPlugin.cpp    
    source/IndexWidgetFactory.cpp    
    source/SearchWidgetFactory.cpp    
	)

set(HEADER_FILES
    source/Browser.h    
    source/ContentWidgetFactory.h    
    source/HelpMode.h    
    source/HelpPluginConfig.h    
    source/HelpPluginConstants.h    
    source/HelpPlugin_global.h    
    source/HelpPlugin.h    
    source/IndexWidgetFactory.h    
    source/SearchWidgetFactory.h    
	)

set(UI_FILES  
    source/HelpPluginConfig.ui    
	)
	
set(QRC_FILES 
    resources/resources.qrc    
	)
ENDIF(QTILITIES_NO_HELP)

add_definitions(-DHELP_PLUGIN_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesTesting)
include_directories(${Qtilities_header_dir}/QtilitiesExtensionSystem)
include_directories(${Qtilities_header_dir}/QtilitiesProjectManagement)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesExtensionSystem
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::Network
    Qt${QT_VERSION_MAJOR}::Help	   
)

set_target_properties(${PROJECT_NAME} PROPERTIES 	
	AUTOMOC ON
    AUTORCC ON
    AUTOUIC ON)
	
set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER "Plugins")

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
