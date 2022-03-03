# Copyright (c) 2022 Cypress Semiconductor Corporation.
#
# SPDX-License-Identifier: Apache-2.0

# Add mtb-pdl-cat1
zephyr_compile_definitions(${CONFIG_SOC_PART_NUMBER})
zephyr_include_directories(drivers/include)
zephyr_include_directories(devices/COMPONENT_CAT1A/include)
zephyr_include_directories(devices/COMPONENT_CAT1A/include/ip)
zephyr_include_directories(devices/COMPONENT_CAT1A/templates/COMPONENT_MTB)

zephyr_library_sources(devices/COMPONENT_CAT1A/source/cy_device.c)
zephyr_library_sources(drivers/source/TOOLCHAIN_GCC_ARM/cy_syslib_gcc.S)

# TODO: when we remove bsp from board, system_psoc6_cm4.c need to add for
# CONFIG_SOC_FAMILY_CAT1A as well
if(CONFIG_SOC_FAMILY_PSOC6)
   zephyr_library_sources_ifdef(CONFIG_CPU_CORTEX_M4
   devices/COMPONENT_CAT1A/templates/COMPONENT_MTB/COMPONENT_CM4/system_psoc6_cm4.c)

   zephyr_library_sources_ifdef(CONFIG_CPU_CORTEX_M0PLUS
   devices/COMPONENT_CAT1A/templates/COMPONENT_MTB/COMPONENT_CM0P/system_psoc6_cm0plus.c)
endif()

# Peripheral drivers
zephyr_library_sources(drivers/source/cy_crypto.c)
zephyr_library_sources(drivers/source/cy_crypto_core_trng_v1.c)
zephyr_library_sources(drivers/source/cy_crypto_core_trng_v2.c)
zephyr_library_sources(drivers/source/cy_flash.c)
zephyr_library_sources(drivers/source/cy_gpio.c)
zephyr_library_sources(drivers/source/cy_ipc_drv.c)
zephyr_library_sources(drivers/source/cy_ipc_pipe.c)
zephyr_library_sources(drivers/source/cy_ipc_sema.c)
zephyr_library_sources(drivers/source/cy_mcwdt.c)
zephyr_library_sources(drivers/source/cy_prot.c)
zephyr_library_sources(drivers/source/cy_rtc.c)
zephyr_library_sources(drivers/source/cy_sar.c)
zephyr_library_sources(drivers/source/cy_scb_common.c)
zephyr_library_sources(drivers/source/cy_scb_i2c.c)
zephyr_library_sources(drivers/source/cy_scb_spi.c)
zephyr_library_sources(drivers/source/cy_scb_uart.c)
zephyr_library_sources(drivers/source/cy_sd_host.c)
zephyr_library_sources(drivers/source/cy_sysanalog.c)
zephyr_library_sources(drivers/source/cy_sysclk.c)
zephyr_library_sources(drivers/source/cy_syslib.c)
zephyr_library_sources(drivers/source/cy_syspm.c)
zephyr_library_sources(drivers/source/cy_systick.c)
zephyr_library_sources(drivers/source/cy_tcpwm_counter.c)
zephyr_library_sources(drivers/source/cy_tcpwm_pwm.c)
zephyr_library_sources(drivers/source/cy_trigmux.c)
zephyr_library_sources(drivers/source/cy_wdt.c)

zephyr_sources_ifdef(CONFIG_SOC_FAMILY_PSOC6 drivers/source/cy_sysint.c)
