

SET(project_name test_main)
PROJECT(${project_name})

SET(Cpp_File_Pattern "*.hpp" "*.cpp" "*.h" "*.c")
FileGlobRecurse(${PROJECT_SOURCE_DIR} "${Cpp_File_Pattern}" dir_files)
SET(all_files ${all_files} ${dir_files})
FileGroupByDir(${PROJECT_SOURCE_DIR} "${all_files}" "")

LINK_LIBRARIES(glad)
LINK_LIBRARIES(glfw3)
LINK_LIBRARIES(learn_opengl)
ADD_EXECUTABLE(${project_name} ${all_files})

IF (WIN32)

ELSE()
	LINK_LIBRARIES(${project_name} m)
ENDIF (WIN32)




