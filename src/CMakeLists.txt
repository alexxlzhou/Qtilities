cmake_minimum_required(VERSION 2.9)

add_subdirectory(Logging)
add_subdirectory(Core)
add_subdirectory(CoreGui)
add_subdirectory(ExtensionSystem)
add_subdirectory(ProjectManagement)

if(BUILD_EXAMPLES)
	add_subdirectory(Examples)
endif(BUILD_EXAMPLES)

if(BUILD_PLUGINS)
	add_subdirectory(Plugins)
endif(BUILD_PLUGINS)

if(BUILD_TOOLS)
	add_subdirectory(Tools)
endif(BUILD_TOOLS)

if(BUILD_TESTING)
	add_subdirectory(Testing)
endif(BUILD_TESTING)

