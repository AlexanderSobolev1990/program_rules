CMAKE_MINIMUM_REQUIRED(VERSION 3.7)
PROJECT(program_rules)
FIND_PACKAGE(LATEX)
SET(PDFLATEX_COMPILER xelatex)
SET(LATEX_DEFAULT_BUILD pdf)
#SET(LATEX_OUTPUT_PATH build)
INCLUDE(../../UseLATEX.cmake)

# Основной документ:
SET(parts
    ../espd.cls
    ../preamble.tex
    ../abbreviations.tex
    src/аббревиатуры.tex
    src/аннотация.tex
    src/введение.tex
    src/общие_сведения.tex
    src/элементы_языка.tex
    src/стиль_программирования.tex
)
ADD_LATEX_DOCUMENT(
    program_rules.tex
    BIBFILES ../bibliography.bib ../bibliography_gost19.bib
    IMAGE_DIRS ../images
    INPUTS ${parts}
)

add_custom_command(
        TARGET program_rules
        COMMAND ${CMAKE_COMMAND} -E copy
                ${CMAKE_SOURCE_DIR}/build/documents/program_rules/program_rules.pdf
                ${CMAKE_SOURCE_DIR}/output/Руководство_программиста_C++.pdf)