cmake_minimum_required(VERSION 2.9)
project(QtilitiesLogging)

set(SOURCE_FILES
    source/AbstractLoggerEngine.cpp 
    source/FormattingEngines.cpp 
    source/Logger.cpp 
    source/LoggerEngines.cpp 
	)

set(HEADER_FILES
    source/AbstractFormattingEngine.h 
    source/AbstractLoggerEngine.h 
    source/FormattingEngines.h 
    source/ILoggerExportable.h 
    source/LoggerEngines.h 
    source/LoggerFactory.h 
    source/Logger.h 
    source/LoggingConstants.h 
    source/Logging_global.h 
	)

set(UI_FILES 
	)
	
set(QRC_FILES 
	)

add_definitions(-DLOGGING_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
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
