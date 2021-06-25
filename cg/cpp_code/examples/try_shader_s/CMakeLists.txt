

SET(project_name try_shader_s)
PROJECT(${project_name})


SET(Cpp_File_Pattern "*.hpp" "*.cpp" "*.h" "*.c")
FileGlobRecurse(${PROJECT_SOURCE_DIR} "${Cpp_File_Pattern}" dir_files)
SET(all_files ${all_files} ${dir_files})
FileGroupByDir(${PROJECT_SOURCE_DIR} "${all_files}" "")

LINK_LIBRARIES(glad)
LINK_LIBRARIES(glfw3)
LINK_LIBRARIES(learn_opengl)
ADD_EXECUTABLE(${project_name} ${all_files})

IF (group_folder)
	set_target_properties(${project_name} PROPERTIES FOLDER ${group_folder})
ENDIF(group_folder)

IF (WIN32)

ELSE()
	LINK_LIBRARIES(${project_name} m)
ENDIF (WIN32)




