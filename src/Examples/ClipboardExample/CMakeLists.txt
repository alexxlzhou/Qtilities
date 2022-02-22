cmake_minimum_required(VERSION 3.5)
project(ClipboardExample) 

set(SOURCE_FILES
    main.cpp
    ObserverWidgetConfig.cpp 
    ExtendedObserverTreeModel.cpp 
    ExtendedObserverTableModel.cpp
	)

set(HEADER_FILES
	ObserverWidgetConfig.h 
    ExtendedObserverTreeModel.h 
    ExtendedObserverTableModel.h
	)

set(UI_FILES 
	ObserverWidgetConfig.ui
	)
	
set(QRC_FILES rc_file.rc)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesTesting)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesCoreGui
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
	Qt${QT_VERSION_MAJOR}::Help 
)

set_target_properties(${PROJECT_NAME} PROPERTIES     
	AUTOMOC ON
    AUTORCC ON
    AUTOUIC ON
)

set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER "Examples")

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
