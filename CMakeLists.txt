cmake_minimum_required(VERSION 3.13)

file(STRINGS "${CMAKE_SOURCE_DIR}/version.txt" projectVersion)
project("docs-sintefio"
  VERSION "${projectVersion}"
  DESCRIPTION "Documentation web frontpage"
  LANGUAGES NONE
)
set(DOCS_PROJECT_NAME "docs.sintef.io")

add_subdirectory(doc)
