cmake_minimum_required(VERSION 3.20)
project(eokas_dotnet)

set(CMAKE_CXX_STANDARD 11)

if(CMAKE_HOST_WIN32)
    add_definitions(-D _OS_WINDOWS 1)
    set(PACK_APPHOST C:\\Program Files\\dotnet\\packs\\Microsoft.NETCore.App.Host.win-x64\\6.0.3\\runtimes\\win-x64\\native)
elseif(CMAKE_HOST_APPLE)
    add_definitions(-D _OS_MACOS 1)
    set(PACK_APPHOST /usr/local/share/dotnet/packs/Microsoft.NETCore.App.Host.osx-x64/6.0.3/runtimes/osx-x64/native)
elseif(CMAKE_HOST_UNIX)
    add_definitions(_OS_LINUX 1)
endif()

include_directories(.)
link_directories(${PACK_APPHOST})

aux_source_directory(. SRC)
add_executable(eokas_dotnet ${SRC})
target_link_libraries(eokas_dotnet nethost)
