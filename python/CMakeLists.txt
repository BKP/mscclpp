# Copyright (c) Microsoft Corporation.
# Licensed under the MIT license.

add_subdirectory(mscclpp)
add_subdirectory(test)

add_custom_target(pylib-copy)
add_custom_command(TARGET pylib-copy POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        ${CMAKE_CURRENT_BINARY_DIR}/mscclpp/_mscclpp.*.so
        ${CMAKE_CURRENT_SOURCE_DIR}/mscclpp
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        ${CMAKE_CURRENT_BINARY_DIR}/test/_ext.*.so
        ${CMAKE_CURRENT_SOURCE_DIR}/test/_cpp
    COMMAND ${CMAKE_COMMAND} -E echo "Copy python libraries"
)
