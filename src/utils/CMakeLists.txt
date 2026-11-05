# Sources of the RetDec utilities PeLib uses, the target is defined in 'src/CMakeLists.txt'.
set(PELIB_UTILS_SOURCES
	${CMAKE_CURRENT_SOURCE_DIR}/conversion.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/ord_lookup.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/string.cpp
	PARENT_SCOPE
)