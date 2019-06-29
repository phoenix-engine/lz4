if(WIN32)
  set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS true)
endif(WIN32)

set(LZ4_LIB_SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR})

set(LZ4_SOURCES
  "${LZ4_LIB_SOURCE_DIR}/lz4.c"
  "${LZ4_LIB_SOURCE_DIR}/xxhash.c")

add_library(LZ4 SHARED ${LZ4_SOURCES})
target_include_directories(LZ4 PUBLIC ${LZ4_LIB_SOURCE_DIR})

set(LZ4F_SOURCES
  "${LZ4_LIB_SOURCE_DIR}/lz4frame.c"
  "${LZ4_LIB_SOURCE_DIR}/lz4hc.c"
  "${LZ4_LIB_SOURCE_DIR}/xxhash.c")

add_library(LZ4F STATIC ${LZ4F_SOURCES})
target_link_libraries(LZ4F LZ4)
target_include_directories(LZ4F PUBLIC ${LZ4_LIB_SOURCE_DIR})
