cmake_minimum_required(VERSION 3.10...3.27)
# 设置Cmake的工具链文件
set(CMAKE_TOOLCHAIN_FILE $ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake)
include($ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake)
add_subdirectory(base64)
add_subdirectory(lz4)
add_subdirectory(mongoose)
add_subdirectory(spdlog)
add_subdirectory(tinyxml2)


if(USE_EXTERNAL_DETOURS)
find_path(DETOURS_INCLUDE_DIRS "detours/detours.h")
find_library(DETOURS_LIBRARY detours REQUIRED)    
else()
add_subdirectory(Detours)
endif()


if(USE_EXTERNAL_JSON)
  find_package(nlohmann_json 3.2.0 REQUIRED)
else()
  set(JSON_BuildTests OFF CACHE INTERNAL "")
  add_subdirectory(json)
endif()