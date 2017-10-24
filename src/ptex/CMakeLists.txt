add_library(ptex
  PtexCache.cpp
  PtexFilters.cpp
  PtexHalf.cpp
  PtexReader.cpp
  PtexSeparableFilter.cpp
  PtexSeparableKernel.cpp
  PtexTriangleFilter.cpp
  PtexTriangleKernel.cpp
  PtexUtils.cpp
  PtexWriter.cpp
)

include(GenerateExportHeader)
generate_export_header(ptex
  EXPORT_FILE_NAME PtexExport.h
  EXPORT_MACRO_NAME PTEXAPI
  STATIC_DEFINE PTEX_STATIC
)

target_include_directories(ptex
  PUBLIC
    ${CMAKE_CURRENT_BINARY_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_link_libraries(ptex 
  Threads::Threads
  ZLIB::ZLIB
)

install(
  TARGETS
    ptex
  DESTINATION
    ${CMAKE_INSTALL_LIBDIR}
)
install(
  FILES
    ${CMAKE_CURRENT_BINARY_DIR}/PtexExport.h
    PtexHalf.h
    PtexInt.h
    Ptexture.h
    PtexUtils.h
    PtexVersion.h
  DESTINATION
    ${CMAKE_INSTALL_INCLUDEDIR}
)
