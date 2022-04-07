cmake_minimum_required(VERSION 3.23)
project(dotnethost)

set(CMAKE_CXX_STANDARD 11)

include_directories(.)
link_directories(/usr/local/share/dotnet/packs/Microsoft.NETCore.App.Host.osx-x64/6.0.3/runtimes/osx-x64/native)

aux_source_directory(. SRC)
add_executable(dotnethost ${SRC})
target_link_libraries(dotnethost nethost)
