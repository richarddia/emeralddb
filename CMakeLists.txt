cmake_minimum_required(VERSION 3.0.0)
project(EmeraldDB)
set(CMAKE_BUILD_TYPE Debug)

include_directories(src src/include boost src/bson/src)
# link_directories(${PROJECT_SOURCE_DIR}/boost/stage/lib)

message(STATUS "Search boost lib files(.a)")
file(GLOB BOOST_LIBS ${CMAKE_CURRENT_SOURCE_DIR}/boost/stage/lib/*.a)

message(STATUS "link boost libs")
link_libraries(${BOOST_LIBS} pthread)
add_executable(
    emeralddb 
    src/pmd/pmdMain.cpp
    src/pmd/pmdTcpListener.cpp
    src/pmd/pmdOptions.cpp
    src/pmd/pmd.cpp
    src/pmd/pmdEDU.cpp
    src/pmd/pmdEDUMgr.cpp
    src/pmd/pmdAgent.cpp
    src/bson/src/bsonobj.cpp 
    src/bson/src/util/json.cpp 
    src/bson/src/oid.cpp 
    src/bson/src/lib/base64.cpp 
    src/bson/src/lib/md5.cpp
    src/bson/src/lib/nonce.cpp
    src/oss/ossSocket.cpp
    src/oss/ossPrimitiveFileOp.cpp
    src/pd/pd.cpp
    src/pmd/pmdOptions.cpp
)

add_executable(
    edb
    src/client/edb.cpp
    src/client/command.cpp
    src/client/commandFactory.cpp
    src/bson/src/bsonobj.cpp 
    src/bson/src/util/json.cpp 
    src/bson/src/oid.cpp 
    src/bson/src/lib/base64.cpp 
    src/bson/src/lib/md5.cpp
    src/bson/src/lib/nonce.cpp
    src/oss/ossSocket.cpp
    src/oss/ossPrimitiveFileOp.cpp
    src/pd/pd.cpp
)