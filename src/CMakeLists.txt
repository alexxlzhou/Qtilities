cmake_minimum_required(VERSION 2.9)

add_subdirectory(Logging)
add_subdirectory(Core)
add_subdirectory(CoreGui)
add_subdirectory(ExtensionSystem)
add_subdirectory(ProjectManagement)

if(BUILD_EXAMPLES)
	add_subdirectory(Examples)
endif(BUILD_EXAMPLES)

#add_subdirectory(Plugins)
#add_subdirectory(Testing)
#add_subdirectory(Tool)
