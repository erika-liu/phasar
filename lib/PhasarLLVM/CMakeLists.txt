add_subdirectory(DB)
add_subdirectory(ControlFlow)
add_subdirectory(DataFlow)
add_subdirectory(Passes)
add_subdirectory(Pointer)
add_subdirectory(TaintConfig)
add_subdirectory(TypeHierarchy)
add_subdirectory(Utils)

file(GLOB PHASAR_LLVM_SRC *.h *.cpp)

set(PHASAR_LINK_LIBS
    phasar_llvm_pointer
    phasar_llvm_db
    phasar_llvm_controlflow
    phasar_llvm_typehierarchy
)

set(LLVM_LINK_COMPONENTS
  Core
  Support
)

if(BUILD_SHARED_LIBS)
  add_phasar_library(phasar_llvm
    SHARED
    ${PHASAR_LLVM_SRC}
  )
else()
  add_phasar_library(phasar_llvm
    STATIC
    ${PHASAR_LLVM_SRC}
  )
endif()
