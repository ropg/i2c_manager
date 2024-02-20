set(SOURCES "i2c_manager/i2c_manager.c")
set(INCLUDES "i2c_manager")

if (CONFIG_I2C_MANAGER_I2CDEV)
    list(APPEND SOURCES "i2cdev/i2cdev.c")
    list(APPEND INCLUDES "i2cdev")
endif()

if("${IDF_VERSION_MAJOR}.${IDF_VERSION_MINOR}" VERSION_GREATER_EQUAL "5.0")
    idf_component_register( SRCS ${SOURCES}
                            INCLUDE_DIRS ${INCLUDES}
                            REQUIRES driver)
else()
idf_component_register( SRCS ${SOURCES}
                            INCLUDE_DIRS ${INCLUDES}
                            )  
endif()
