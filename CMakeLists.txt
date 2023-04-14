cmake_minimum_required(VERSION 3.18)

project(PhoXiAPI LANGUAGES C CXX)
add_executable(${PROJECT_NAME} main.cpp)

#Photoneo API
if (NOT PHO_API_CMAKE_CONFIG_PATH)
    set(PHO_API_CMAKE_CONFIG_PATH "$ENV{PHOXI_CONTROL_PATH}")
endif()
find_package(PhoXi REQUIRED CONFIG PATHS "${PHO_API_CMAKE_CONFIG_PATH}")

target_include_directories(${PROJECT_NAME}
        PRIVATE ${PHOXI_INCLUDE_DIRS} )





# linking
target_link_libraries(${PROJECT_NAME}
        PUBLIC
        ${PHOXI_LIBRARY}
        )