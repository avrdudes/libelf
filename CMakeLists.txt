#
# CMakeLists.txt
# Copyright (C) 2021 Marius Greuel
#

cmake_minimum_required(VERSION 3.12)
project(libelf)

add_library(libelf STATIC
    src/32.fsize.c
    src/32.getehdr.c
    src/32.getphdr.c
    src/32.getshdr.c
    src/32.newehdr.c
    src/32.newphdr.c
    src/32.xlatetof.c
    src/64.xlatetof.c
    src/assert.c
    src/begin.c
    src/checksum.c
    src/cntl.c
    src/cook.c
    src/data.c
    src/end.c
    src/errmsg.c
    src/errno.c
    src/fill.c
    src/flag.c
    src/gelfehdr.c
    src/gelfphdr.c
    src/gelfshdr.c
    src/gelftrans.c
    src/getarhdr.c
    src/getaroff.c
    src/getarsym.c
    src/getbase.c
    src/getdata.c
    src/getident.c
    src/getscn.c
    src/hash.c
    src/input.c
    src/kind.c
    src/memset.c
    src/ndxscn.c
    src/newdata.c
    src/newscn.c
    src/next.c
    src/nextscn.c
    src/nlist.c
    src/opt.delscn.c
    src/rand.c
    src/rawdata.c
    src/rawfile.c
    src/strptr.c
    src/swap64.c
    src/update.c
    src/verdef_32_tof.c
    src/verdef_32_tom.c
    src/verdef_64_tof.c
    src/verdef_64_tom.c
    src/version.c
    src/x.elfext.c
    src/x.movscn.c
    src/x.remscn.c
    )

target_include_directories(libelf
    PUBLIC
    include
    PRIVATE
    src
    include/libelf
    )

target_compile_definitions(libelf PRIVATE HAVE_CONFIG_H=1)

if(MSVC)
    target_compile_definitions(libelf PRIVATE _CRT_SECURE_NO_WARNINGS=1)
    target_compile_definitions(libelf PRIVATE _CRT_NONSTDC_NO_WARNINGS=1)
    target_compile_options(libelf PRIVATE /wd4244) # warning C4244: '=': conversion from 'xxx' to 'xxx', possible loss of data
    target_compile_options(libelf PRIVATE /wd4267) # warning C4267: 'function': conversion from 'xxx' to 'xxx', possible loss of data
    target_compile_options(libelf PRIVATE /wd4311) # warning C4311: 'type cast': pointer truncation from 'xxx' to 'xxx'
endif()
