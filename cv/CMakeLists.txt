
set(CMAKE_CUDA_COMPILER  /usr/local/cuda-9.2/bin/nvcc)

include(FindCUDA)

set(CMAKE_CXX_STANDARD 14)
find_package(CUDA REQUIRED)
set(CUDA_NVCC_FLAGS ${CUDA_NVCC_FLAGS} -gencode arch=compute_30,code=sm_30)

#add_library(ygz-cv
#        src/ORBExtractor.cpp
#        src/ORBMatcher.cpp
#        src/Tracker.cpp
#        src/Align.cpp
#        src/LKFlow.cpp
#        src/TrackerLK.cpp
#        )

cuda_add_library(ygz-cv
        src/ORBExtractor.cpp
        src/ORBMatcher.cpp
        src/Tracker.cpp
        src/Align.cpp
        src/LKFlow.cpp
        src/TrackerLK.cpp
        )

target_link_libraries(ygz-cv ygz-common ${THIRD_PARTY_LIBS})