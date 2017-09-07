cmake_minimum_required(VERSION 3.6)
cmake_policy(SET CMP0042 NEW)
project(MBEDECP VERSION 1.0.0)

set (SRC_MBEDECP
        src/aes.c
        src/aesni.c
        src/bignum.c
        src/ctr_drbg.c
        src/ecp.c
        src/ecp_curves.c
        src/entropy.c
        src/entropy_poll.c
        src/padlock.c
        src/platform.c
        src/sha256.c
        #src/timing.c
        )
add_library(mbedecp STATIC ${SRC_MBEDECP})
target_include_directories(mbedecp PUBLIC inc)


install(TARGETS mbedecp EXPORT mbedecp
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin
        INCLUDES DESTINATION inc
        )
export(EXPORT mbedecp
        FILE "${CMAKE_CURRENT_BINARY_DIR}/cmake/ext/mbedecp.cmake"
        )