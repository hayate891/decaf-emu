project(pm4-replay)

include_directories(".")
include_directories("../../src/libdecaf/src")

file(GLOB_RECURSE SOURCE_FILES *.cpp)
file(GLOB_RECURSE HEADER_FILES *.h)

add_executable(pm4-replay ${SOURCE_FILES} ${HEADER_FILES})
set_target_properties(pm4-replay PROPERTIES FOLDER tools)

target_link_libraries(pm4-replay
    common
    libdecaf
    ${EXCMD_LIBRARIES}
    ${SDL2_LINK})

if(${CMAKE_SYSTEM_NAME} MATCHES "Linux")
    target_link_libraries(pm4-replay X11)
endif()

install(TARGETS pm4-replay RUNTIME DESTINATION "${CMAKE_INSTALL_PREFIX}")
