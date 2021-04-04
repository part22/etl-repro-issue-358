cmake_minimum_required(VERSION 3.18)

set(CMAKE_SYSTEM_NAME Arduino)
set(CMAKE_SYSTEM_PROCESSOR avr)

set(CMAKE_C_EXTENSIONS OFF)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_COMPILER_TARGET avr)
set(CMAKE_CXX_FLAGS "-mmcu=atmega328p -nostdlib")

project(etl-repro VERSION 0.1 LANGUAGES C CXX)

add_subdirectory("third-party/etl")

add_executable(etl-repro main.cpp)
target_include_directories(etl-repro PRIVATE include)
target_compile_options(etl-repro PRIVATE 
    -fno-lto 
    -fdata-sections 
    -fno-exceptions 
    -ffunction-sections 
    -fno-threadsafe-statics)
target_compile_features(etl-repro PRIVATE c_std_11)
target_compile_features(etl-repro PRIVATE cxx_std_17)
target_compile_definitions(etl-repro PRIVATE
    F_CPU=16000000L
    ARDUINO=10813
    ARDUINO_AVR_UNO
    ARDUINO_ARCH_AVR)
target_link_options(etl-repro PRIVATE -emain) 
target_link_libraries(etl-repro etl)