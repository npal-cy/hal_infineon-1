# Copyright (c) 2022 Cypress Semiconductor Corporation.
# SPDX-License-Identifier: Apache-2.0


# Add abstraction-rtos
zephyr_include_directories(include/)

# Enable CMSIS_RTOS_V2 support
zephyr_include_directories_ifdef(CONFIG_CMSIS_RTOS_V2 include/COMPONENT_RTX)
zephyr_library_sources_ifdef(CONFIG_CMSIS_RTOS_V2 source/COMPONENT_RTX/cyabs_rtos_rtxv5.c)

# Enable Zephyr support
zephyr_include_directories_ifdef(COMPONENT_ZEPHYR include/COMPONENT_ZEPHYR)
zephyr_library_sources_ifdef(COMPONENT_ZEPHYR source/COMPONENT_ZEPHYR/cyabs_rtos_zephyr.c)
