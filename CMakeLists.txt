cmake_minimum_required(VERSION 2.8)

if(!WIN32)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -pedantic -Wextra")
else()
	set(XINPUT "Xinput9_1_0")
	if ( ${CMAKE_SYSTEM_VERSION} LESS 6.1 )
		set(XINPUT, "xinput")
	endif()
endif()

if(ANDROID)
	include(extern/cmake/AndroidNdkModules.cmake)
	android_ndk_import_module_native_app_glue()
endif()


add_subdirectory(lib)
if(!no_samples)
	add_subdirectory(samples)
endif()

if(!no_test)
	add_subdirectory(test)
endif()



