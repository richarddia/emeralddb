cmake_minimum_required(VERSION 3.0.0)
project(EmeraldDB)
include_directories(src/include boost src/bson/src)
# link_directories(${PROJECT_SOURCE_DIR}/boost/stage/lib)

message(STATUS "Search boost lib files(.a)")
file(GLOB BOOST_LIBS ${CMAKE_CURRENT_SOURCE_DIR}/boost/stage/lib/*.a)

message(STATUS "link boost libs")
link_libraries(${BOOST_LIBS})
add_executable(
    emeralddb 
    src/pmd/pmdMain.cpp
    src/pmd/pmdTest.cpp
    src/bson/src/bsonobj.cpp 
    src/bson/src/util/json.cpp 
    src/bson/src/oid.cpp 
    src/bson/src/lib/base64.cpp 
    src/bson/src/lib/md5.cpp
    src/bson/src/lib/nonce.cpp
    src/oss/ossSocket.cpp
)