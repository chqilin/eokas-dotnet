cmake_minimum_required(VERSION 3.20)
project(eokas_dotnet)

set(CMAKE_CXX_STANDARD 11)

if(CMAKE_HOST_WIN32)
    add_definitions(-D _OS_WINDOWS)
    set(PKG_APPHOST deps/apphost/Windows-x86)
elseif(CMAKE_HOST_APPLE)
    add_definitions(-D _OS_MACOS)
    set(PKG_APPHOST /usr/local/share/dotnet/packs/Microsoft.NETCore.App.Host.osx-x64/6.0.3/runtimes/osx-x64/native)
elseif(CMAKE_HOST_UNIX)
    add_definitions(_OS_LINUX)
endif()
message("PKG_APPHOST: " ${PKG_APPHOST})

include_directories(${PKG_APPHOST})
include_directories(src)
link_directories(${PKG_APPHOST})

aux_source_directory(src SRC)

add_executable(eokas_dotnet ${SRC})
target_link_libraries(eokas_dotnet nethost)
