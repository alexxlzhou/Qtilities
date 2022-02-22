cmake_minimum_required(VERSION 3.5)
project(MainWindowExample) 

set(SOURCE_FILES
    main.cpp
	ExampleMode.cpp
	)

set(HEADER_FILES
	ExampleMode.h
	)

set(UI_FILES
	ExampleMode.ui 
	)
	
set(QRC_FILES rc_file.rc)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesExtensionSystem)
include_directories(${Qtilities_header_dir}/QtilitiesProjectManagement)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesProjectManagement QtilitiesExtensionSystem
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::Network
    Qt${QT_VERSION_MAJOR}::PrintSupport
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
