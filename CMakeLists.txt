IF(BIICODE)

    ADD_BII_TARGETS()

    target_link_libraries(${BII_BLOCK_TARGET} INTERFACE archive)

    if(MSVC)
        set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SAFESEH:NO")
    else()
        target_compile_options(${BII_BLOCK_TARGET} INTERFACE -std=c++11)
    endif()

ELSE()

    cmake_minimum_required (VERSION 2.6)

    project(Moor CXX)

    add_subdirectory(moor)
    add_subdirectory(test)

ENDIF()
