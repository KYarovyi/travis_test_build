cmake_minimum_required(VERSION 2.8) # Проверка версии CMake.
project(hello_world)


##########################################################
FIND_PACKAGE( Boost 1.40 COMPONENTS program_options REQUIRED )
if(NOT Boost_FOUND)
	message(SEND_ERROR "Failed to find boost::thread-mt.+++++++++++++++++++++++++")
	return()
else()
	include_directories(${Boost_INCLUDE_DIRS})
endif()
##########################################################



set(SOURCE_EXE test.cpp)

#set(SOURCES_LIB foo.cpp) 
#add_library(foo STATIC ${SOURCES_LIB})
include_directories(foo)                # Расположение заголовочных файлов
add_subdirectory(foo)                   # Добавление подпроекта, указывается имя дирректории


#include_directories(${BOOST_LIB})
#add_subdirectory(${BOOST_LIB})

add_executable(main ${SOURCE_EXE})
target_link_libraries(main foo)