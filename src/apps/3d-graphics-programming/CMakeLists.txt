set(APP_NAME 3DGraphicsProgramming)
set(APP_FOLDER_NAME 3d-graphics-programming)

set(APP_NAME_TEST ${LIB_NAME}Test)

file(GLOB_RECURSE SOURCES "src/*.cpp")

add_executable(${APP_NAME} ${SOURCES})

# Copy assets
file(COPY assets DESTINATION ${CMAKE_BINARY_DIR}/src/apps/${APP_FOLDER_NAME})

# Load upng
add_library(upng ${CMAKE_SOURCE_DIR}/externals/upng/upng.c ${CMAKE_SOURCE_DIR}/externals/upng/upng.h)
include_directories(${CMAKE_SOURCE_DIR}/externals/upng)
target_link_libraries(${APP_NAME} upng)

target_link_libraries(${APP_NAME} Core)
target_link_libraries(${APP_NAME} CoreImgui)
target_link_libraries(${APP_NAME} Logger)
