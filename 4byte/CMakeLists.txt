cmake_minimum_required(VERSION 2.6)
set(LIBNAME ${CMAKE_PROJECT_NAME}_${VERSION}_4)
file(GLOB LIB_4_SRC ${CMAKE_CURRENT_SOURCE_DIR}/../src/*.f ${CMAKE_CURRENT_SOURCE_DIR}/../src/*.F)
add_definitions( ${CMAKE_Fortran_4_FLAGS} )
add_library(${LIBNAME} STATIC ${LIB_4_SRC} )

set(CMAKE_INCLUDE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/include_4")
set_target_properties(${LIBNAME} PROPERTIES Fortran_MODULE_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/include_4")
target_include_directories(${LIBNAME} PUBLIC "${CMAKE_CURRENT_BINARY_DIR}/include_4")

install(TARGETS ${LIBNAME}
        RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
        LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
        ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib) 
install(DIRECTORY ${CMAKE_INCLUDE_OUTPUT_DIRECTORY}/ DESTINATION include_4 )

