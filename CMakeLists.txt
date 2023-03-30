CMAKE_MINIMUM_REQUIRED(VERSION 3.7)
PROJECT(program_documentation)
#
# Поддиректории с соответствующими документами:
#
add_subdirectory(documents/program_rules)

# Архивирование документации
add_custom_target(
    custom_target
    COMMAND ${CMAKE_COMMAND} -E tar cfvz "Руководство_программиста_C++.tgz"
    "${CMAKE_CURRENT_SOURCE_DIR}/output/*.pdf"
    WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/output"
)
install(CODE "execute_process(COMMAND make custom_target)")
install(SCRIPT "${CMAKE_CURRENT_SOURCE_DIR}/script.cmake")
