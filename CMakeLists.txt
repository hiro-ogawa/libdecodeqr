cmake_minimum_required(VERSION 2.8)
project(decodeqr C CXX)

find_package(OpenCV REQUIRED)
set(CMAKE_CXX_FLAGS "-fpermissive")

set(lib_sources
  libdecodeqr/bitstream.cpp
  libdecodeqr/formatinfo.cpp
  libdecodeqr/codedata.cpp
  libdecodeqr/galois.cpp
  libdecodeqr/container.cpp
  libdecodeqr/imagereader.cpp
  libdecodeqr/ecidecoder.cpp
  libdecodeqr/libdecodeqr.cpp
)

include_directories(libdecodeqr)
# add_library(decodeqr ${lib_sources})
# target_include_directories(decodeqr libdecodeqr)

add_executable(simpletest examples/simple/simpletest.cpp ${lib_sources})
target_link_libraries(simpletest ${OpenCV_LIBS})
# add_executable(simpletest examples/simple/simpletest.cpp)
# target_link_libraries(simpletest decodeqr ${OpenCV_LIBS})

add_executable(webcam examples/webcam/webcam.cpp ${lib_sources})
target_link_libraries(webcam ${OpenCV_LIBS})

