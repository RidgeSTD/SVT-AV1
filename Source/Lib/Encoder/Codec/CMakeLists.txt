#
# Copyright(c) 2019 Intel Corporation
# SPDX - License - Identifier: BSD - 2 - Clause - Patent
#

# C_DEFAULT Directory CMakeLists.txt
if (CMAKE_SYSTEM_PROCESSOR MATCHES "(x86)|(X86)|(amd64)|(AMD64)")
    set (X86 TRUE)
else ()
    set (X86 FALSE)
endif ()
if(X86)
# Include Encoder Subdirectories
include_directories(../../../API
        ../../Encoder/Codec
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/C_DEFAULT/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/ASM_SSE2/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/ASM_SSSE3/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/ASM_SSE4_1/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/ASM_AVX2/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/ASM_AVX512/
        ${PROJECT_SOURCE_DIR}/third_party/fastfeat/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/Globals/
        )
else ()
# Include Encoder Subdirectories
include_directories(../../../API
        ../../Encoder/Codec
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/C_DEFAULT/
        ${PROJECT_SOURCE_DIR}/third_party/fastfeat/
        ${PROJECT_SOURCE_DIR}/Source/Lib/Encoder/Globals/
        )
endif ()
file(GLOB all_files
    "*.h"
    "*.c")

add_library(ENCODER_CODEC OBJECT ${all_files})



