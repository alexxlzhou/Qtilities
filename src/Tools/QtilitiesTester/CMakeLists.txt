cmake_minimum_required(VERSION 3.5)
project(QtilitiesTester) 

set(SOURCE_FILES
    main.cpp
	)

set(HEADER_FILES
	)

set(UI_FILES
	)
	
set(QRC_FILES rc_file.rc)

add_definitions(-DQTILITIES_TESTING)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesTesting)
include_directories(${Qtilities_header_dir}/QtilitiesExtensionSystem)
include_directories(${Qtilities_header_dir}/QtilitiesProjectManagement)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesTesting
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::Test
    Qt${QT_VERSION_MAJOR}::PrintSupport
)

set_target_properties(${PROJECT_NAME} PROPERTIES     
	AUTOMOC ON
    AUTORCC ON
    AUTOUIC ON
)

set_target_properties(${PROJECT_NAME} PROPERTIES FOLDER "Tools")


install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
