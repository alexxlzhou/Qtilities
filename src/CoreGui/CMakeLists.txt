cmake_minimum_required(VERSION 2.9)
project(QtilitiesCoreGui)

set(SOURCE_FILES
    source/AboutWindow.cpp 
    source/AbstractObserverItemModel.cpp 
    source/AbstractTreeItem.cpp 
    source/ActionContainer.cpp 
    source/ActionManager.cpp 
    source/ActionProvider.cpp 
    source/AddDynamicPropertyWizard.cpp 
    source/ClipboardManager.cpp 
    source/CodeEditor.cpp 
    source/CodeEditorWidgetConfig.cpp 
    source/CodeEditorWidget.cpp 
    source/Command.cpp 
    source/CommandEditor.cpp 
    source/CommandTreeModel.cpp 
    source/ConfigurationWidget.cpp 
    source/DynamicSideWidgetViewer.cpp 
    source/DynamicSideWidgetWrapper.cpp 
    source/GenericPropertyBrowser.cpp 
    source/GenericPropertyPathEditor.cpp 
    source/GenericPropertyPathEditorListWrapper.cpp 
    source/GenericPropertyTypeManagers.cpp 
    source/GroupedConfigPage.cpp 
    source/LoggerConfigWidget.cpp 
    source/LoggerEnginesTableModel.cpp 
    source/ModeListWidget.cpp 
    source/ModeManager.cpp 
    source/NamingPolicyFilter.cpp 
    source/NamingPolicyInputDialog.cpp 
    source/ObjectHierarchyNavigator.cpp 
    source/ObjectScopeWidget.cpp 
    source/ObserverTableModel.cpp 
    source/ObserverTableModelProxyFilter.cpp 
    source/ObserverTreeItem.cpp 
    source/ObserverTreeModelBuilder.cpp 
    source/ObserverTreeModel.cpp 
    source/ObserverTreeModelProxyFilter.cpp 
    source/ObserverWidget.cpp 
    source/QtilitiesApplication.cpp 
    source/QtilitiesApplication_p.cpp 
    source/QtilitiesMainWindow.cpp 
    source/SearchBoxWidget.cpp 
    source/SideViewerWidgetFactory.cpp 
    source/SideWidgetFileSystem.cpp 
    source/SingleTaskWidget.cpp 
    source/StringListWidget.cpp 
    source/TaskManagerGui.cpp 
    source/TaskSummaryWidget.cpp 
    source/TreeFileItem.cpp 
    source/TreeItemBase.cpp 
    source/TreeItem.cpp 
    source/TreeNode.cpp 
    source/WidgetLoggerEngine.cpp 
    source/WidgetLoggerEngineFrontend.cpp 
	)

set(HEADER_FILES
    source/AboutWindow.h 
    source/AbstractObserverItemModel.h 
    source/AbstractTreeItem.h 
    source/ActionContainer.h 
    source/ActionManager.h 
    source/ActionProvider.h 
    source/AddDynamicPropertyWizard.h 
    source/ClipboardManager.h 
    source/CodeEditor.h 
    source/CodeEditorWidgetConfig.h 
    source/CodeEditorWidget.h 
    source/CommandEditor.h 
    source/Command.h 
    source/CommandTreeModel.h 
    source/ConfigurationWidget.h 
    source/DynamicSideWidgetViewer.h 
    source/DynamicSideWidgetWrapper.h 
    source/GenericPropertyBrowser.h 
    source/GenericPropertyPathEditor.h 
    source/GenericPropertyPathEditorListWrapper.h 
    source/GenericPropertyTypeManagers.h 
    source/GroupedConfigPage.h 
    source/IActionManager.h 
    source/IActionProvider.h 
    source/IClipboard.h 
    source/IConfigPage.h 
    source/IGroupedConfigPageInfoProvider.h 
    source/IMode.h 
    source/INamingPolicyDialog.h 
    source/ISideViewerWidget.h 
    source/LoggerConfigWidget.h 
    source/LoggerEnginesTableModel.h 
    source/LoggerGui.h 
    source/ModeListWidget.h 
    source/ModeManager.h 
    source/NamingPolicyFilter.h 
    source/NamingPolicyInputDialog.h 
    source/ObjectHierarchyNavigator.h 
    source/ObjectScopeWidget.h 
    source/ObserverTableModel.h 
    source/ObserverTableModelProxyFilter.h 
    source/ObserverTreeItem.h 
    source/ObserverTreeModelBuilder.h 
    source/ObserverTreeModel.h 
    source/ObserverTreeModelProxyFilter.h 
    source/ObserverWidget.h 
    source/QtilitiesApplication.h 
    source/QtilitiesApplication_p.h 
    source/QtilitiesCoreGuiConstants.h 
    source/QtilitiesCoreGui_global.h 
    source/QtilitiesMainWindow.h 
    source/SearchBoxWidget.h 
    source/SideViewerWidgetFactory.h 
    source/SideWidgetFileSystem.h 
    source/SingleTaskWidget.h 
    source/StringListWidget.h 
    source/TaskManagerGui.h 
    source/TaskSummaryWidget.h 
    source/TreeFileItem.h 
    source/TreeItemBase.h 
    source/TreeItem.h 
    source/TreeNode.h 
    source/WidgetLoggerEngineFrontend.h 
    source/WidgetLoggerEngine.h 
	)

set(UI_FILES 
    source/AboutWindow.ui 
    source/CodeEditorWidgetConfig.ui 
    source/CodeEditorWidget.ui 
    source/CommandEditor.ui 
    source/ConfigurationWidget.ui 
    source/DynamicSideWidgetViewer.ui 
    source/DynamicSideWidgetWrapper.ui 
    source/GenericPropertyPathEditorListWrapper.ui 
    source/GenericPropertyPathEditor.ui 
    source/GroupedConfigPage.ui 
    source/LoggerConfigWidget.ui 
    source/NamingPolicyInputDialog.ui 
    source/ObjectHierarchyNavigator.ui 
    source/ObjectScopeWidget.ui 
    source/ObserverWidget.ui 
    source/QtilitiesMainWindow.ui 
    source/SearchBoxWidget.ui 
    source/SideWidgetFileSystem.ui 
    source/SingleTaskWidget.ui 
    source/StringListWidget.ui 
    source/TaskSummaryWidget.ui 
	)
	
set(QRC_FILES resources/CoreGui.qrc)

IF(QTPROPERTYBROWSER)
	SET(HEADER_FILES ${HEADER_FILES} source/ObjectPropertyBrowser.h source/ObjectDynamicPropertyBrowser.h)
	SET(SOURCE_FILES ${SOURCE_FILES} source/ObjectPropertyBrowser.cpp source/ObjectDynamicPropertyBrowser.cpp)
ENDIF(QTPROPERTYBROWSER)

set(QTILITIES_NO_HELP OFF)
IF(NOT QTILITIES_NO_HELP)
	SET(HEADER_FILES ${HEADER_FILES} source/HelpManager.h)
	SET(SOURCE_FILES ${SOURCE_FILES} source/HelpManager.cpp)
ENDIF(NOT QTILITIES_NO_HELP)

add_definitions(-DQTILITIES_CORE_GUI_LIBRARY)

include_directories(${Qtilities_header_dir}/QtilitiesLogging)
include_directories(${Qtilities_header_dir}/QtilitiesCore)
include_directories(${Qtilities_header_dir}/QtilitiesCoreGui)

#set(CMAKE_INCLUDE_CURRENT_DIR ON)
add_library(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES} ${UI_FILES} ${QRC_FILES})

target_link_libraries(${PROJECT_NAME} PUBLIC QtilitiesLogging QtilitiesCore
    Qt${QT_VERSION_MAJOR}::Core 
    Qt${QT_VERSION_MAJOR}::Gui 
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Xml
    Qt${QT_VERSION_MAJOR}::PrintSupport
	Qt${QT_VERSION_MAJOR}::Help 
)

IF(QTPROPERTYBROWSER)
	target_link_libraries(${PROJECT_NAME} PUBLIC ${QTPROPERTYBROWSER_LIBRARY})
ENDIF(QTPROPERTYBROWSER)

set_target_properties(${PROJECT_NAME} PROPERTIES AUTOMOC TRUE)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)
