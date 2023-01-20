cmake_minimum_required(VERSION 3.5)

#project(cccc LANGUAGES C)
project(cccc)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Make sure to not link debug libs
# against release libs and vice versa
if(WIN32)
  SET(CMAKE_DEBUG_POSTFIX "d" CACHE STRING "Add postfix to debug build")
endif(WIN32)

#if(WIN32)
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /D_CONSOLE")
#    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SUBSYSTEM:CONSOLE")

#    MESSAGE(STATUS "     CMAKE_EXE_LINKER_FLAGS ............. : ${CMAKE_EXE_LINKER_FLAGS}")
#endif(WIN32)


SET(CCCC_SUPPORT_CPP ON CACHE BOOL "Support C++ analysis.")
SET(CCCC_SUPPORT_JAVA ON CACHE BOOL "Support Java analysis.")
SET(CCCC_SUPPORT_ADA OFF CACHE BOOL "Support Ada analysis (still need checking and testing).")
mark_as_advanced(CCCC_SUPPORT_ADA)

# Make these ones internal so it won't be displayed default to the user as an option
SET(PCCTS_USER_ZZSYN ON CACHE BOOL
    "Do not use standard error reporting function (default ON, preferred).")
mark_as_advanced(PCCTS_USER_ZZSYN)
if (PCCTS_USER_ZZSYN)
    add_compile_definitions(USER_ZZSYN)
endif(PCCTS_USER_ZZSYN)

# Let the user have the option to define a different buffer size
SET(PCCTS_LEXER_BUFFER_SIZE "65536" CACHE STRING
    "The size (in bytes) of the buffer used by antlr and dlg to generate the lexers.")
add_compile_definitions(ZZLEXBUFSIZE=${PCCTS_LEXER_BUFFER_SIZE})

#SET(PCCTS_LONG_FILENAMES ON CACHE BOOL
#    "Do use long file names (default ON, preferred).")
#mark_as_advanced(PCCTS_LONG_FILENAMES)
#if (PCCTS_LONG_FILENAMES)
    add_compile_definitions(PC)
    add_compile_definitions(LONGFILENAMES)
#endif(PCCTS_LONG_FILENAMES)

add_compile_definitions(__STDC__)


# Add the pccts required untility applications build. These are required by CCCC to create
# the files used for the code parser
add_subdirectory(pccts)


# Add the final cccc application
add_subdirectory(cccc)



#add_executable(cccc main.cpp)

#install(TARGETS cccc
#    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
