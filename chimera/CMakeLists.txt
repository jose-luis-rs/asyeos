# Create a library called  "libR3BAsyChim" which includes the source files given in
# the array.
# The extension is already found.  Any number of sources could be listed here.

file(
    GLOB
    SRCS
    ./sim/*.cxx
    ./pars/*.cxx
    ./ana/*.cxx)

change_file_extension(*.cxx *.h HEADERS "${SRCS}")

add_library_with_dictionary(
    LIBNAME
    R3BAsyChim
    LINKDEF
    R3BAsyChimLinkDef.h
    HEADERS
    ${HEADERS}
    SRCS
    ${SRCS}
    INCLUDEDIRS
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/sim
    ${CMAKE_CURRENT_SOURCE_DIR}/pars
    ${CMAKE_CURRENT_SOURCE_DIR}/ana
    DEPENDENCIES
    R3BAsyData
    R3BTracking)
