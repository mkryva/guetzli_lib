cmake_minimum_required(VERSION 3.6)
project(guetzli_lib)

set(CMAKE_CXX_STANDARD 11)

include_directories(
        ./
        ./third_party/butteraugli
)
set(guetzli_sources
        guetzli/butteraugli_comparator.cc
        guetzli/dct_double.cc
        guetzli/debug_print.cc
        guetzli/entropy_encode.cc
        guetzli/fdct.cc
        guetzli/gamma_correct.cc
        guetzli/guetzli.cc
        guetzli/idct.cc
        guetzli/jpeg_data.cc
        guetzli/jpeg_data_decoder.cc
        guetzli/jpeg_data_encoder.cc
        guetzli/jpeg_data_reader.cc
        guetzli/jpeg_data_writer.cc
        guetzli/jpeg_huffman_decode.cc
        guetzli/output_image.cc
        guetzli/preprocess_downsample.cc
        guetzli/processor.cc
        guetzli/quality.cc
        guetzli/quantize.cc
        guetzli/score.cc
        third_party/butteraugli/butteraugli/butteraugli.cc)


set(SOURCE_FILES ${guetzli_sources} libguetzli.cpp libguetzli.h guetzli/entry_point.h)
set (CMAKE_SHARED_LINKER_FLAGS  "-lpng -lgflags_nothreads -lz -lpthread")

add_library(guetzli_lib SHARED ${SOURCE_FILES})