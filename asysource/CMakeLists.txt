# Create a library called "libR3BAsysource" which includes the source files given in
# the array. The extension is already found. Any number of sources could be listed here.

set(SRCS R3BAsyChimeraReader.cxx R3BAsyKrabReader.cxx)

set(STRUCT_HEADERS ext/ext_h101_chimera.h ext/ext_h101_krab.h)

# fill list of header files from list of source files
# by exchanging the file extension
change_file_extension(*.cxx *.h HEADERS "${SRCS}")
set(HEADERS ${STRUCT_HEADERS} ${HEADERS})

add_library_with_dictionary(
    LIBNAME
    R3BAsySource
    LINKDEF
    R3BAsySourceLinkDef.h
    HEADERS
    ${HEADERS}
    SRCS
    ${SRCS}
    INCLUDEDIRS
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/ext
    DEPENDENCIES
    R3BAsyData
    R3BSource)
