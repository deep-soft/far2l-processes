project(processes)

set(SOURCES
src/procplugin.cpp 
)

add_library (processes MODULE ${SOURCES})

target_link_libraries(processes utils far2l)

target_compile_definitions(processes PRIVATE -DWINPORT_DIRECT -DUNICODE -DFAR_DONT_USE_INTERNALS)

target_include_directories(processes PRIVATE .)
target_include_directories(processes PRIVATE ${CMAKE_SOURCE_DIR}/WinPort)
target_include_directories(processes PRIVATE ${CMAKE_SOURCE_DIR}/far2l/far2sdk)

set_target_properties(processes
    PROPERTIES
        LIBRARY_OUTPUT_DIRECTORY "${INSTALL_DIR}/Plugins/processes/plug"
        PREFIX ""
        SUFFIX ".far-plug-wide")
