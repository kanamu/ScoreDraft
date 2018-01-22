cmake_minimum_required (VERSION 3.0)

set(SOURCES
UtauDraft.cpp
OtoMap.cpp
FrqData.cpp
)

set(HEADERS 
OtoMap.h
FrqData.h
)

set (INCLUDE_DIR
.
../ScoreDraftCore
../WavUtil
../DSPUtil
../PyScoreDraft
)

set (LINK_LIBS 
ScoreDraftCore
WavUtil
DSPUtil)

if (WIN32) 
set (DEFINES  ${DEFINES}
-D"_CRT_SECURE_NO_DEPRECATE"  
-D"_SCL_SECURE_NO_DEPRECATE" 
)
else()
add_definitions(-std=c++0x)
add_compile_options(-fPIC)
endif()

include_directories(${INCLUDE_DIR})
add_definitions(${DEFINES})
add_library (UtauDraft SHARED ${SOURCES} ${HEADERS})
target_link_libraries(UtauDraft ${LINK_LIBS})

install(TARGETS UtauDraft DESTINATION Extensions)


