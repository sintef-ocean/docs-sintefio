include(SfhDocHelpers.cmake)
sfh_doc_python_requirements(${CMAKE_CURRENT_SOURCE_DIR}/requirements.txt)

# Sphinx html generation =============================================

set(SPHINX_BUILD_DIR ${CMAKE_CURRENT_BINARY_DIR}/sphinx)

# Variables used in sphinx's conf.py
set(SPHINX_PROJECT_VENDOR "SINTEF Ocean")
set(SPHINX_PROJECT_AUTHOR "")
string(TIMESTAMP THE_YEAR %Y)

set(SPHINX_SOURCE ${SPHINX_BUILD_DIR}/source) # Location of doc source

configure_file(conf.py.in ${SPHINX_SOURCE}/conf.py @ONLY)

# Prepare sphinx root source directory
# Copy static resources
# Copy markdown and rst files
# This assumes that files and directories to be copied do exist
macro(sfh_add_doc_sources_target _target _source_path _build_path)

   add_custom_target(${_target}
      COMMENT "DELETE generated docs and COPY doc sources to sphinx root directory"
      COMMAND ${CMAKE_COMMAND} -E remove_directory ${_build_path}
      COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_SOURCE_DIR}/doc/index.rst ${_source_path}/index.rst
      COMMAND ${CMAKE_COMMAND} -E copy_directory static ${_source_path}/static
      COMMAND ${CMAKE_COMMAND} -E copy_directory _templates ${_source_path}/_templates
      WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
      )
   #      COMMAND ${CMAKE_COMMAND} -E copy_directory markup ${_source_path}/markup

   set(_index_file ${_build_path}/index.html)

   add_custom_command(
      OUTPUT ${_index_file} always.outdated
      COMMAND ${SPHINX_EXECUTABLE} -b html
      ${_source_path} ${_build_path}
      WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
      MAIN_DEPENDENCY ${_source_path}/conf.py
      COMMENT "Generate docs with Sphinx"
      VERBATIM
      )

endmacro()

sfh_add_doc_sources_target(doc-sources ${SPHINX_SOURCE} ${SPHINX_BUILD_DIR}/html)
add_custom_target(doc-html DEPENDS ${SPHINX_BUILD_DIR}/html/index.html)
add_dependencies(doc-html doc-sources)
add_custom_target(doc ALL)
add_dependencies(doc doc-html)

install(
   DIRECTORY "${CMAKE_BINARY_DIR}/doc/sphinx/html"
   DESTINATION "doc"
   OPTIONAL
   PATTERN ".doctrees*" EXCLUDE
   PATTERN "_sources*" EXCLUDE
   PATTERN ".buildinfo" EXCLUDE
   )

install(
   FILES ${CMAKE_CURRENT_SOURCE_DIR}/static/favicon.ico
   DESTINATION "doc/html")
