cmake_minimum_required(VERSION 3.10...3.27)
project(app VERSION 1.0.0)
# 设置Cmake的工具链文件
set(CMAKE_TOOLCHAIN_FILE $ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake)
include($ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake)

# 创建一个宏来打印环境变量
macro(print_environment_variables)
    # 获取环境变量列表的键值对
    get_cmake_property(variableNames VARIABLES)
    foreach(var ${variableNames})
        # 检查是否为环境变量
        message(STATUS "Environment Variable: ${var}=${${var}}")
    endforeach()
endmacro()

# 调用宏来打印所有环境变量
print_environment_variables()

add_subdirectory(app)

