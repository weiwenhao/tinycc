cmake_minimum_required(VERSION 3.2)

project(tcc
        LANGUAGES C CXX)

set(CMAKE_C_FLAGS         "-pthread -Wall -Wextra -DTCC_TARGET_X86_64 -DONE_SOURCE=0 -Wdeclaration-after-statement -fno-strict-aliasing -Wno-pointer-sign -Wno-sign-compare -Wno-unused-result")
set(CMAKE_C_FLAGS_DEBUG   "-g")
set(CMAKE_C_FLAGS_RELEASE "-O2 -DNDEBUG")

include_directories(.)

set(X864_64_FILES
        tcc.h
        config.h
        elf.h
        i386-asm.c
        i386-asm.h
        i386-tok.h
#        i386-gen.c
#        i386-link.c
        libtcc.c
        stab.h
        tccelf.c
        tccasm.c
        tccgen.c
        tccdbg.c
        tccpp.c
        tccrun.c
        tcctok.h
        x86_64-asm.h
        x86_64-link.c
        x86_64-gen.c)

add_executable(tcc tcc.c ${X864_64_FILES})
target_link_libraries(tcc m dl)