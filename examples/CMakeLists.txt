file(GLOB BENCHMARK_FILES ./*.cpp)

foreach(file ${BENCHMARK_FILES})

  message(STATUS " Getting ${file} ")

  get_filename_component(SOURCE_NAME ${file} NAME_WE)
  message(STATUS " Adding ${SOURCE_NAME} ")

  include_directories(${COMPUTECPP_INCLUDE_DIRECTORY})

  add_executable(${SOURCE_NAME} ${CMAKE_CURRENT_SOURCE_DIR}/${SOURCE_NAME}.cpp  )
  target_compile_options(${SOURCE_NAME} PUBLIC ${HOST_COMPILER_OPTIONS})

  add_sycl_to_target(${SOURCE_NAME} ${CMAKE_CURRENT_SOURCE_DIR}/${SOURCE_NAME}.cpp 
    ${CMAKE_CURRENT_BINARY_DIR})

endforeach()
