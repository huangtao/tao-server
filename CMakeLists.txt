# ************************************************************
# tao server application.
#
# Copyright (C) 2016 Huang Tao <huangtao117@yeah.net>
# ************************************************************

# CMake版本要求
cmake_minimum_required(VERSION 3.7)

# 项目名称
project(tserver)

if(MSVC)
    # 我们使用多线程/MT
    # /MT和/MD区别是/MT是静态链接,/MD(微软推荐)运行时需要依赖的DLL
    # 保证第三方库均使用/MT(需要修改apr项目属性)
    set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} /MT")
    set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} /MTd")
    # 这个警告信息不要
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
    # VC默认不支持无BOM中文编码,开启它
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /source-charset:utf-8")
endif()

# 头文件目录
#include_directories(${CMAKE_SOURCE_DIR}/third_party/libuv/include)
#include_directories(${CMAKE_SOURCE_DIR}/third_party/libpq/include)

# 库目录
#link_directories(${CMAKE_SOURCE_DIR}/third_party/libuv/prebuilt/win)
#link_directories(${CMAKE_SOURCE_DIR}/third_party/libpq/prebuilt/win)

# 包含子目录
add_subdirectory(source)
#add_subdirectory(tests)
