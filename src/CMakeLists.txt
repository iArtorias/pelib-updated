# One static library from both source folders. The folders only list their files, the old layout defined the target
# 'pelib' twice, so the project could not be added with 'add_subdirectory' or 'FetchContent'.
add_subdirectory(pelib)
add_subdirectory(utils)

add_library(pelib STATIC ${PELIB_PELIB_SOURCES} ${PELIB_UTILS_SOURCES})
add_library(pelib::pelib ALIAS pelib)

target_compile_features(pelib PUBLIC cxx_std_17)

target_include_directories(pelib
	PUBLIC
		$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
		$<INSTALL_INTERFACE:include>)

if(MSVC)
	target_compile_options(pelib PRIVATE /w /EHsc /utf-8)
else()
	target_compile_options(pelib PRIVATE -w)
endif()

if(PELIB_INSTALL)
	include(GNUInstallDirs)
	install(TARGETS pelib EXPORT pelib-targets ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR})
	install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/retdec DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
	install(EXPORT pelib-targets NAMESPACE pelib:: DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/pelib FILE pelib-config.cmake)
endif()