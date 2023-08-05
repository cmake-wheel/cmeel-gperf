cmake_minimum_required(VERSION 3.20)

set(GPERF_VERSION 3.1)

project(cmeel-gperf VERSION ${GPERF_VERSION})

include(ExternalProject)
ExternalProject_Add(
  gperf
  URL "https://ftpmirror.gnu.org/gnu/gperf/gperf-${GPERF_VERSION}.tar.gz"
      DOWNLOAD_EXTRACT_TIMESTAMP OFF
  BUILD_IN_SOURCE ON
  CONFIGURE_COMMAND "./configure" "--prefix=${CMAKE_INSTALL_PREFIX}"
  # "--with-bugurl=https://github.com/cmake-wheel/cmeel-gperf/issues"
  BUILD_COMMAND "make"
  TEST_COMMAND "make" "check"
  INSTALL_COMMAND "make" "install")

# dummy file for install target
install(FILES README.md DESTINATION share/cmeel-gperf/)
