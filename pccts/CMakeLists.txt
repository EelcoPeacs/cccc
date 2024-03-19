
# Build the antlr application

set(ANTLR_SOURCES
    antlr/antlr.c
    antlr/bits.c
    antlr/build.c
    antlr/egman.c
    antlr/err.c
    antlr/fcache.c
    antlr/fset.c
    antlr/fset2.c
    antlr/gen.c
    antlr/globals.c
    antlr/hash.c
    antlr/lex.c
    antlr/main.c
    antlr/misc.c
    antlr/mrhoist.c
    antlr/pred.c
    antlr/scan.c
    support/set/set.c
)

include_directories(antlr h support/set)

add_executable(antlr ${ANTLR_SOURCES})
set_target_properties(antlr PROPERTIES LINKER_LANGUAGE C)
set_target_properties(antlr PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
set_target_properties(antlr PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")


# Build the dlg application

set(DLG_SOURCES
    dlg/automata.c
    dlg/dlg_a.c
    dlg/dlg_p.c
    dlg/err.c
    dlg/main.c
    dlg/output.c
    dlg/relabel.c
    dlg/support.c
    support/set/set.c
)

include_directories(dlg h support/set)

add_executable(dlg ${DLG_SOURCES})
set_target_properties(dlg PROPERTIES LINKER_LANGUAGE C)
set_target_properties(dlg PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
set_target_properties(dlg PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")


# The next applications are not used by CCCC

## Build the sorcerer application

#set(SORCERER_SOURCES
#    sorcerer/cpp.c
#    sorcerer/err.c
#    sorcerer/gen.c
#    sorcerer/globals.c
#    sorcerer/hash.c
#    sorcerer/look.c
#    sorcerer/main.c
#    sorcerer/scan.c
#    sorcerer/sor.c
#    support/set/set.c
#)

#include_directories(sorcerer h support/set)

#add_executable(sorcerer ${SORCERER_SOURCES})
#set_target_properties(sorcerer PROPERTIES LINKER_LANGUAGE C)
#set_target_properties (sorcerer PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
#set_target_properties(sorcerer PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")



## Build the genmk application

#set(GENMK_SOURCES
#    support/genmk/genmk.c
#)

#include_directories(genmk h support/set)

#add_executable(genmk ${GENMK_SOURCES})
#set_target_properties(genmk PROPERTIES LINKER_LANGUAGE C)
#set_target_properties (genmk PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
#set_target_properties(genmk PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
