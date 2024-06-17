# Create a library called "libR3BasyData" which includes the source files given in
# the array .
# The extension is already found.  Any number of sources could be listed here.

set(SRCS
    chimeraData/R3BAsyChimeraPoint.cxx
    chimeraData/R3BAsyChimeraHitData.cxx
    chimeraData/R3BAsyChimeraMappedData.cxx
    chimeraData/R3BAsyChimeraArrayData.cxx
    krabData/R3BAsyKrabPoint.cxx
    krabData/R3BAsyKrabHitData.cxx
    krabData/R3BAsyKrabMappedData.cxx
    krabData/R3BAsyKrabArrayData.cxx)

# fill list of header files from list of source files
# by exchanging the file extension
change_file_extension(*.cxx *.h HEADERS "${SRCS}")

add_library_with_dictionary(
    LIBNAME
    R3BAsyData
    LINKDEF
    R3BAsyDataLinkDef.h
    HEADERS
    ${HEADERS}
    SRCS
    ${SRCS}
    INCLUDEDIRS
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/chimeraData
    ${CMAKE_CURRENT_SOURCE_DIR}/krabData
    DEPENDENCIES
    R3BData)
