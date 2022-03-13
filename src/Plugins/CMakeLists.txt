cmake_minimum_required(VERSION 2.9)

project(QtilitiesPlugins)

if(BUILD_TESTING)
	add_subdirectory(DebugPlugin)
endif(BUILD_TESTING)

add_subdirectory(HelpPlugin)
add_subdirectory(ProjectManagementPlugin)
add_subdirectory(PluginTemplate)
add_subdirectory(SessionLogPlugin)
