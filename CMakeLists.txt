cmake_minimum_required(VERSION 3.9.2)
set (CMAKE_CXX_STANDARD 17)

project(ads)

IF(CMAKE_BUILD_TYPE MATCHES Release)
  message(" --- Building in Release Mode ---")
  
  add_subdirectory(bin_tree)
  add_subdirectory(bloom_filter)
  add_subdirectory(trie)

ENDIF(CMAKE_BUILD_TYPE MATCHES Release)

IF(CMAKE_BUILD_TYPE MATCHES Debug)
  message(" --- Building in Debug Mode ---")

  include(GoogleTest)
  find_package(Threads REQUIRED)
  # Enable ExternalProject CMake module
  include(ExternalProject)
  # Download and install GoogleTest
  ExternalProject_Add(
      gtest
      URL https://github.com/google/googletest/archive/release-1.8.1.zip
      PREFIX ${CMAKE_CURRENT_BINARY_DIR}/gtest
      # Disable install step
      INSTALL_COMMAND ""
  )
  # Get GTest source and binary directories from CMake project
  ExternalProject_Get_Property(gtest source_dir binary_dir)
  # Create a libgtest target to be used as a dependency by test programs
  add_library(libgtest IMPORTED STATIC GLOBAL)
  add_dependencies(libgtest gtest)
  # Set libgtest properties
  set_target_properties(libgtest PROPERTIES
      "IMPORTED_LOCATION" "${binary_dir}/googlemock/gtest/libgtest.a"
      "IMPORTED_LINK_INTERFACE_LIBRARIES" "${CMAKE_THREAD_LIBS_INIT}"
  )
  # Create a libgmock target to be used as a dependency by test programs
  add_library(libgmock IMPORTED STATIC GLOBAL)
  add_dependencies(libgmock gtest)
  # Set libgmock properties
  set_target_properties(libgmock PROPERTIES
      "IMPORTED_LOCATION" "${binary_dir}/googlemock/libgmock.a"
      "IMPORTED_LINK_INTERFACE_LIBRARIES" "${CMAKE_THREAD_LIBS_INIT}"
  )

  set(GTEST_INSTALLED TRUE)

  add_subdirectory(bin_tree)
  add_subdirectory(bloom_filter)
  add_subdirectory(trie)

  enable_testing()
ENDIF(CMAKE_BUILD_TYPE MATCHES Debug)
