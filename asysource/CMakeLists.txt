# Create a library called "libR3BAsysource" which includes the source files given in
# the array. The extension is already found. Any number of sources could be listed here.



set(INCLUDE_DIRECTORIES
    #cmake-format: sortable
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${R3BROOT_SOURCE_DIR}/r3bsource
    ${R3BROOT_SOURCE_DIR}/r3bsource/base
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils
    ${R3BROOT_SOURCE_DIR}/r3bbase
    ${R3BROOT_SOURCE_DIR}/r3bdata/wrData
    ${R3BASY_SOURCE_DIR}/asydata
    ${R3BASY_SOURCE_DIR}/asydata/chimeraData
    ${R3BASY_SOURCE_DIR}/asydata/krabData
    ${R3BASY_SOURCE_DIR}/asysource
    ${R3BASY_SOURCE_DIR}/asysource/ext    
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr
   )

    set(SRCS
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbLauncher.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbStructInfo.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BUcesbSource.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BUcesbSource2.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BReader.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BUnpackReader.cxx
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr/R3BWhiterabbitMasterReader.cxx
    R3BAsyChimeraReader.cxx
    R3BAsyKrabReader.cxx
    )
    
    set(STRUCT_HEADERS
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/ext_h101_unpack.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr/ext_h101_whiterabbit.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr/ext_h101_wrmaster.h
    ext/ext_h101_chimera.h
    ext/ext_h101_krab.h
    )

    set(HEADERS
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BUcesbSource.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BReader.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/R3BUnpackReader.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbDecl.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbLauncher.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbMappingFlag.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/base/utils/R3BUcesbStructInfo.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr/R3BWhiterabbitMasterReader.h
    ${R3BROOT_SOURCE_DIR}/r3bsource/wr/R3BTimestampMasterReader.h
    R3BAsyChimeraReader.h
    R3BAsyKrabReader.h
    )

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
    ${INCLUDE_DIRECTORIES}
    DEPENDENCIES
    R3BBase 
    R3BData 
    Ucesb 
    R3BAsyData)

