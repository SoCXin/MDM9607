ugelis_library()

ugelis_library_sources_ifdef(CONFIG_I2C_ATMEL_SAM3	i2c_atmel_sam3.c)
ugelis_library_sources_ifdef(CONFIG_I2C_BITBANG		i2c_bitbang.c)
ugelis_library_sources_ifdef(CONFIG_I2C_CC32XX		i2c_cc32xx.c)
ugelis_library_sources_ifdef(CONFIG_I2C_DW		    i2c_dw.c)
ugelis_library_sources_ifdef(CONFIG_I2C_ESP32		i2c_esp32.c)
ugelis_library_sources_ifdef(CONFIG_I2C_GPIO		i2c_gpio.c)
ugelis_library_sources_ifdef(CONFIG_I2C_IMX		    i2c_imx.c)
ugelis_library_sources_ifdef(CONFIG_I2C_MCUX		i2c_mcux.c)
ugelis_library_sources_ifdef(CONFIG_NRFX_TWI		i2c_nrfx_twi.c)
ugelis_library_sources_ifdef(CONFIG_NRFX_TWIM		i2c_nrfx_twim.c)
ugelis_library_sources_ifdef(CONFIG_I2C_QMSI		i2c_qmsi.c)
ugelis_library_sources_ifdef(CONFIG_I2C_QMSI_SS		i2c_qmsi_ss.c)
ugelis_library_sources_ifdef(CONFIG_I2C_SAM_TWI		i2c_sam_twi.c)
ugelis_library_sources_ifdef(CONFIG_I2C_SAM_TWIHS	i2c_sam_twihs.c)
ugelis_library_sources_ifdef(CONFIG_I2C_SBCON		i2c_sbcon.c)
ugelis_library_sources_ifdef(CONFIG_I2C_NIOS2		i2c_nios2.c)
ugelis_library_sources_ifdef(CONFIG_I2C_GM		    i2c_gm.c)

ugelis_library_sources_ifdef(CONFIG_I2C_STM32_V1
	i2c_ll_stm32_v1.c
	i2c_ll_stm32.c
	)
ugelis_library_sources_ifdef(CONFIG_I2C_STM32_V2
	i2c_ll_stm32_v2.c
	i2c_ll_stm32.c
	)

ugelis_library_sources_ifdef(CONFIG_USERSPACE		i2c_handlers.c)

add_subdirectory_ifdef(CONFIG_I2C_SLAVE			slave)
