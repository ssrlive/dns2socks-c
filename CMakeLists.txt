cmake_minimum_required(VERSION 3.5)
project(dns2socks)

add_executable(dns2socks dns2socks/dns2socks.c dns2socks/stdafx.c)
target_include_directories(dns2socks PRIVATE dns2socks)

if(WIN32)
    target_link_libraries(dns2socks PRIVATE ws2_32)
elseif(UNIX)
    target_link_libraries(dns2socks PRIVATE pthread)
    target_compile_options(dns2socks PRIVATE -Wall -O2)
endif()
