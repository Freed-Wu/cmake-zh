cmake_minimum_required(VERSION 3.10)
# cmake-format: off
set(VERSION v3.26.4 CACHE STRING "version of cmake")
# cmake-format: on
option(ZH_CN "generate simplified Chinese translation" ON)
option(ZH_TW "generate taiwan traditional Chinese translation")
option(HTML "generate html" ON)
option(MAN "generate man")

string(REPLACE v "" NEW_VERSION ${VERSION})

find_program(sphinx-build sphinx-build HINTS "/usr/bin/" REQUIRED)
find_program(sphinx-intl sphinx-intl HINTS "/usr/bin/" REQUIRED)
if(ZH_CN)
  set(LANG zh_cn)
endif()
if(ZH_TW)
  find_program(opencc opencc HINTS "/usr/bin/" REQUIRED)
  set(LANG zh_tw)
endif()

project(
  cmake-${LANG}
  VERSION ${NEW_VERSION}
  DESCRIPTION "translation of cmake documents for ${LANG}"
  HOMEPAGE_URL "https://github.com/Freed-Wu/cmake-zh"
  LANGUAGES)

include(ExternalProject)
ExternalProject_Add(
  cmake
  URL "https://github.com/Kitware/CMake/archive/refs/tags/${VERSION}.tar.gz"
  CMAKE_ARGS -DSPHINX_HTML=ON -DSPHINX_MAN=ON -DCMAKE_USE_OPENSSL=OFF
  BUILD_COMMAND ""
  INSTALL_COMMAND ""
  USES_TERMINAL_DOWNLOAD 1
  USES_TERMINAL_CONFIGURE 1
  USES_TERMINAL_BUILD 1)
add_custom_target(
  pot ALL
  COMMAND sphinx-build ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake/Help ${CMAKE_BINARY_DIR}/build/gettext -c
          ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake-build/Utilities/Sphinx -b gettext
  DEPENDS cmake
  COMMENT "generate .pot files")
add_custom_target(
  zh_CN-po ALL
  COMMAND sphinx-intl update -l zh_CN -d ${CMAKE_SOURCE_DIR}/locales
  DEPENDS pot
  COMMENT "update .po files")
if(MAN)
  set(ZH_CN_MAN ALL)
endif()
add_custom_target(
  zh_CN-man
  ${ZH_CN_MAN}
  COMMAND
    sphinx-build ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake/Help ${CMAKE_BINARY_DIR}/build/man -c
    ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake-build/Utilities/Sphinx -b man -Dlanguage=zh_CN
    -Dlocale_dirs=${CMAKE_SOURCE_DIR}/locales
  DEPENDS zh_CN-po
  COMMENT "generate man")
if(HTML)
  set(ZH_CN_HTML ALL)
endif()
add_custom_target(
  zh_CN-html
  ${ZH_CN_HTML}
  COMMAND
    sphinx-build ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake/Help ${CMAKE_BINARY_DIR}/build/html -c
    ${CMAKE_BINARY_DIR}/cmake-prefix/src/cmake-build/Utilities/Sphinx -b html -Dlanguage=zh_CN
    -Dlocale_dirs=${CMAKE_SOURCE_DIR}/locales
  DEPENDS zh_CN-po
  COMMENT "generate html")
if(ZH_TW)
  set(ZH_TW_PO ALL)
  add_dependencies(zh_TW-man zh_TW-po)
  add_dependencies(zh_TW-html zh_TW-po)
endif()
add_custom_target(
  zh_TW-po
  ${ZH_TW_PO}
  COMMAND opencc -c s2twp.json -i ${CMAKE_SOURCE_DIR}/locales/zh_CN/LC_MESSAGES/ -o
          ${CMAKE_BINARY_DIR}/locales/zh_TW/LC_MESSAGES/
  DEPENDS zh_CN-po
  COMMENT "po for zh_TW")

if(LANG STREQUAL zh_cn)
  install(DIRECTORY ${CMAKE_BINARY_DIR}/zh_CN/zh_CN TYPE MAN)
else()
  install(DIRECTORY ${CMAKE_BINARY_DIR}/zh_TW/zh_TW TYPE MAN)
endif()

set(CPACK_PACKAGE_CONTACT "https://github.com/Freed-Wu/cmake-zh/issues")
include(CPack)
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/LICENSE")
set(CPACK_RESOURCE_FILE_README "${CMAKE_CURRENT_SOURCE_DIR}/README.md")
set(CPACK_ARCHIVE_THREADS 0)
set(CPACK_THREADS 0)
