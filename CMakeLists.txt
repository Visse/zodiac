cmake_minimum_required(VERSION 3.6)

project(Zodiac)
# enable folders
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

enable_testing()

if (MSVC)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)

    # Some usefull errors
    add_compile_options(/we4700) # Error: uninitialized local variable used
    add_compile_options(/we4715) # Error: not all paths returs a value
endif(MSVC)



include_directories(.)

add_subdirectory(dependencies)
add_subdirectory(Common)
add_subdirectory(Pisces)


add_library(Zodiac INTERFACE)
target_link_libraries(Zodiac
    INTERFACE Common
    INTERFACE Pisces
)

install(TARGETS Zodiac EXPORT Zodiac)
#install(EXPORT Zodiac DESTINATION cmake NAMESPACE Zodiac:: FILE ZodiacConfig.cmake)

