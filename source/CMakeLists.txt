# 版本号
set(tserver_VERSION_MAJOR 1)
set(tserver_VERSION_MINOR 0)

# 目录下的源文件保存到变量
aux_source_directory(. MY_SRCS)

#libqipai.a for release
#libqipai-d.a for debug
#set(CMAKE_DEBUG_POSTFIX -d)

add_executable(tserver ${MY_SRCS})

# 链接库
#target_link_libraries(qipaid debug libuv_d)
#target_link_libraries(qipaid debug apr-1_d)

#target_link_libraries(qipaid optimized libuv)
#target_link_libraries(qipaid optimized apr-1)

if(MSVC)
# 忽略LIBCMTD.lib
#target_link_libraries(qipaid ws2_32 Iphlpapi Psapi Userenv Rpcrt4)
endif()
    
if(CMAKE_SYSTEM_NAME MATCHES "Linux")
#target_link_libraries(qipaid m)
endif(CMAKE_SYSTEM_NAME MATCHES "Linux")
