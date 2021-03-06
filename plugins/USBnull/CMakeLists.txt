# Check that people use the good file
if(NOT TOP_CMAKE_WAS_SOURCED)
    message(FATAL_ERROR "
    You did not 'cmake' the good CMakeLists.txt file. Use the one in the top dir.
    It is advice to delete all wrongly generated cmake stuff => CMakeFiles & CMakeCache.txt")
endif()


# plugin name
set(Output USBnull-0.7.0)

set(OptimizationFlags
    -O2
    )

if(CMAKE_BUILD_TYPE STREQUAL Debug)
	set(USBnullFinalFlags "")

elseif(CMAKE_BUILD_TYPE STREQUAL Devel)
	set(USBnullFinalFlags ${OptimizationFlags})

elseif(CMAKE_BUILD_TYPE STREQUAL Release)
	set(USBnullFinalFlags ${OptimizationFlags})

endif()

# USBnull sources
set(USBnullSources
	Config.cpp
	USB.cpp)

# USBnull headers
set(USBnullHeaders
	Config.h
	USB.h)

# USBnull Linux sources
set(USBnullLinuxSources
)

# USBnull Linux headers
set(USBnullLinuxHeaders
)

# USBnull Windows sources
set(USBnullWindowsSources
	Windows/Config.cpp
	Windows/USBnull.def
	Windows/USBnull.rc
	Windows/Win32.cpp)

# USBnull Windows headers
set(USBnullWindowsHeaders
	Windows/resource.h)

set(USBnullFinalSources
	${USBnullSources}
	${USBnullHeaders}
	${USBnullLinuxSources}
	${USBnullLinuxHeaders}
)

set(USBnullFinalLibs
	${GTK2_LIBRARIES}
)

add_pcsx2_plugin(${Output} "${USBnullFinalSources}" "${USBnullFinalLibs}" "${USBnullFinalFlags}")
