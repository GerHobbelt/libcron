cmake_minimum_required(VERSION 3.6)

project(top)

option(BUILD_CRON_TESTS "Build Cron Tests" OFF)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose Release or Debug" FORCE)
endif()

add_subdirectory(libcron)

if(BUILD_CRON_TESTS)
    add_subdirectory(test)
    add_dependencies(cron_test libcron)
endif()

install(TARGETS libcron DESTINATION lib)
install(DIRECTORY libcron/include/libcron DESTINATION include)
install(DIRECTORY libcron/externals/date/include/date DESTINATION include)
