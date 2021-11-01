set(PELIB_SOURCES
	conversion.cpp
	ord_lookup.cpp
	string.cpp
)

add_library(pelib STATIC ${PELIB_SOURCES})

target_compile_features(pelib PUBLIC cxx_std_17)

target_include_directories(pelib
	PUBLIC ${PROJECT_SOURCE_DIR}/include/)

# Disable all warnings from this library.
if(MSVC)
	target_compile_options(pelib PUBLIC "/w")
else()
	target_compile_options(pelib PUBLIC "-w")
endif()
