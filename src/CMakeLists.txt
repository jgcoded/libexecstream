set(TARGET execstream)

if(LIBEXECSTREAM_SHARED)
    set(libtype SHARED)
else()
    set(libtype)
endif()

find_package(Threads REQUIRED)

add_library(${TARGET} ${libtype} exec-stream.cpp)
target_include_directories(${TARGET} PUBLIC "../include")
target_link_libraries(${TARGET} PUBLIC ${CMAKE_THREAD_LIBS_INIT})

if(NOT MSVC)
    target_compile_options(${TARGET} PRIVATE -fPIC)
endif()
