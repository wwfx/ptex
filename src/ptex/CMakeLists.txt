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

if (WIN32)
  target_compile_definitions(ptex
    PRIVATE
      PTEX_EXPORTS
  )
endif (WIN32)

if (NOT BUILD_SHARED_LIBS)
  target_compile_definitions(ptex
    PUBLIC
      PTEX_STATIC
  )
endif()

target_link_libraries(ptex ${CMAKE_THREAD_LIBS_INIT} ${ZLIB_LIBRARIES})

install(
  TARGETS
    ptex
  DESTINATION
    ${CMAKE_INSTALL_LIBDIR}
)
install(
  FILES
    PtexHalf.h
    PtexInt.h
    Ptexture.h
    PtexUtils.h
    PtexVersion.h
  DESTINATION
    ${CMAKE_INSTALL_INCLUDEDIR}
)
