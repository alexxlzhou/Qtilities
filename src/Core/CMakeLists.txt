cmake_minimum_required(VERSION 2.9)
project(QtilitiesCore)

set(SOURCE_FILES
    source/ActivityPolicyFilter.cpp 
    source/ContextManager.cpp 
    source/FileLocker.cpp 
    source/FileSetInfo.cpp 
    source/FileUtils.cpp 
    source/GenericProperty.cpp 
    source/GenericPropertyManager.cpp 
    source/IExportable.cpp 
    source/InstanceFactoryInfo.cpp 
    source/ITaskContainer.cpp 
    source/ObjectManager.cpp 
    source/Observer.cpp 
    source/ObserverData.cpp 
    source/ObserverDotWriter.cpp 
    source/ObserverHints.cpp 
    source/ObserverRelationalTable.cpp 
    source/PointerList.cpp 
    source/QtilitiesCategory.cpp 
    source/QtilitiesCoreApplication.cpp 
    source/QtilitiesCoreApplication_p.cpp 
    source/QtilitiesFileInfo.cpp 
    source/QtilitiesProcess.cpp 
    source/QtilitiesPropertyChangeEvent.cpp 
    source/QtilitiesProperty.cpp 
    source/SubjectFilterTemplate.cpp 
    source/SubjectTypeFilter.cpp 
    source/Task.cpp 
    source/TaskManager.cpp 
    source/VersionInformation.cpp 
    source/Zipper.cpp 
	)

set(HEADER_FILES
    ../Common/Qtilities.h 
    source/AbstractSubjectFilter.h 
    source/ActivityPolicyFilter.h 
    source/ContextManager.h 
    source/Factory.h 
    source/FileLocker.h 
    source/FileSetInfo.h 
    source/FileUtils.h 
    source/GenericProperty.h 
    source/GenericPropertyManager.h 
    source/IAvailablePropertyProvider.h 
    source/IContext.h 
    source/IContextManager.h 
    source/IExportableFormatting.h 
    source/IExportable.h 
    source/IExportableObserver.h 
    source/IFactoryProvider.h 
    source/IIterator.h 
    source/IModificationNotifier.h 
    source/InstanceFactoryInfo.h 
    source/IObjectBase.h 
    source/IObjectManager.h 
    source/ITaskContainer.h 
    source/ITask.h 
    source/ObjectManager.h 
    source/ObserverData.h 
    source/ObserverDotWriter.h 
    source/Observer.h 
    source/ObserverHints.h 
    source/ObserverMimeData.h 
    source/ObserverRelationalTable.h 
    source/PointerList.h 
    source/QtilitiesCategory.h 
    source/QtilitiesCoreApplication.h 
    source/QtilitiesCoreApplication_p.h 
    source/QtilitiesCoreConstants.h 
    source/QtilitiesCore_global.h 
    source/QtilitiesFileInfo.h 
    source/QtilitiesProcess.h 
    source/QtilitiesPropertyChangeEvent.h 
    source/QtilitiesProperty.h 
    source/SubjectFilterTemplate.h 
    source/SubjectIterator.h 
    source/SubjectTypeFilter.h 
    source/Task.h 
    source/TaskManager.h 
    source/TreeIterator.h 
    source/VersionInformation.h 
    source/Zipper.h 
	)


add_definitions(-DQTILITIESCORE_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesLogging
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
)

set_target_properties(${PROJECT_NAME} PROPERTIES AUTOMOC TRUE)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
