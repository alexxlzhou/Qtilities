cmake_minimum_required(VERSION 2.9)
project(QtilitiesTesting)

set(SOURCE_FILES
    source/BenchmarkTests.cpp
    source/TestAbstractTreeItem.cpp
    source/TestActivityPolicyFilter.cpp
    source/TestExporting.cpp
    source/TestNamingPolicyFilter.cpp
    source/TestObjectManager.cpp
    source/TestObserver.cpp
    source/TestObserverRelationalTable.cpp
    source/TestSubjectIterator.cpp
    source/TestSubjectTypeFilter.cpp
    source/TestTask.cpp
    source/TestTreeFileItem.cpp
    source/TestTreeIterator.cpp
    source/TestVersionNumber.cpp
)

set(HEADER_FILES
    source/BenchmarkTests.h
    source/TestAbstractTreeItem.h
    source/TestActivityPolicyFilter.h
    source/TestExporting.h
    source/TestingConstants.h
    source/Testing_global.h
    source/TestNamingPolicyFilter.h
    source/TestObjectManager.h
    source/TestObserver.h
    source/TestObserverRelationalTable.h
    source/TestSubjectIterator.h
    source/TestSubjectTypeFilter.h
    source/TestTask.h
    source/TestTreeFileItem.h
    source/TestTreeIterator.h
    source/TestVersionNumber.h
)

# --------------------------
# Extension Library Files
# --------------------------
set(SOURCE_FILES ${SOURCE_FILES}
    source/DebugWidget.cpp
    source/DropableListWidget.cpp
    source/FunctionCallAnalyzer.cpp
    source/TestFileSetInfo.cpp
    source/TestFrontend.cpp
)

set(HEADER_FILES ${HEADER_FILES}
    source/DebugWidget.h
    source/DropableListWidget.h
    source/FunctionCallAnalyzer.h
    source/ITestable.h
    source/TestFileSetInfo.h
    source/TestFrontend.h
    source/TestingConstants.h
    source/Testing_global.h
)
		
set(UI_FILES 
	source/TestFrontend.ui
	source/DebugWidget.ui
	)
	
set(QRC_FILES 
	)

add_definitions(-DTESTING_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)
include_directories(${Qtilities_header_dir}/QtilitiesExtensionSystem)
include_directories(${Qtilities_header_dir}/QtilitiesProjectManagement)
include_directories(${Qtilities_header_dir}/QtilitiesTesting)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesExtensionSystem QtilitiesProjectManagement
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

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
