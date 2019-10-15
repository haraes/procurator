set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR}/CMakeModules)

add_executable(procurator
	main.cpp
	mainwindow.cpp
	mainwindow.h
)

# Compile as a WIN32
target_link_libraries(procurator PRIVATE Qt5::WinMain)
if(MSVC)
	set_target_properties(procurator PROPERTIES LINK_FLAGS_RELEASE "/SUBSYSTEM:WINDOWS")
elseif(MINGW)
	set_target_properties(procurator PROPERTIES LINK_FLAGS_RELEASE "-mwindows")
endif()

target_link_libraries(procurator PRIVATE common)
target_link_libraries(procurator PRIVATE Qt5::Widgets)

target_compile_definitions(procurator PRIVATE
    -DQT_USE_QSTRINGBUILDER
    -DQT_NO_CAST_FROM_ASCII
    -DQT_NO_CAST_TO_ASCII
    -DQT_NO_NARROWING_CONVERSIONS_IN_CONNECT
    -DQT_NO_PROCESS_COMBINED_ARGUMENT_START
    -DQT_NO_URL_CAST_FROM_STRING
)
