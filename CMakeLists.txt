cmake_minimum_required(VERSION 3.15.3 FATAL_ERROR)

set (CMAKE_CXX_STANDARD 11)



########################################################################
# Stuff to move into Toolchain file
########################################################################

set(OSAL_SYSTEM_OSTYPE posix)
set(OSAL_SYSTEM_BSPTYPE "generic-linux")
set(TOOLCHAIN_NAME "x86_linux")

########################################################################
# End of Toolchain file
########################################################################


########################################################################
# Project declaration
########################################################################
project(osal_example VERSION 1.0.0)

########################################################################

########################################################################
## OSAL Section
########################################################################

set(OSAL_SOURCE_DIR "./osal")
list(APPEND OSAL_CONFIGURATION_FILE "default_config.cmake")
add_subdirectory(osal "os") # this is the osal direcotry!

########################################################################
## App section
########################################################################

#Stuff to move into subfolder
add_executable(osal_test 
./src/tasking-example.c)

target_link_libraries(osal_test PUBLIC
    osal
)