# TSC2025 Project

## Block Diagram

![image](https://github.com/user-attachments/assets/cf016ced-38cc-4f77-a24d-0b3fbc02e55c)

## Brief Description

### Microcontroller
- **ESP32-C6**: Main processor with WiFi/BLE, controls all components

### Display and Storage
- **E-Ink Display**: Minimal power consumption display (1.5" 200x200px)
- **SD Card**: Electronic book storage
- **64MB Flash Memory**: For firmware and cache

### Power
- **USB-C**: Charging and data transfer
- **Battery charging circuit**: MCP73831 for LiPo battery
- **LiPo Battery**: 3.7V portable power
- **3.3V Regulator**: Voltage stabilizer for ESP32 and sensors

### Sensors
- **BME680**: Temperature and humidity, I2C connection

### Other Components
- **RTC DS3231**: Real-time clock for timekeeping
- **Buttons**: Navigation and control via GPIO

### Interfaces
- **SPI**: Display, SD card, flash memory
- **I2C**: Sensors, RTC
- **GPIO**: Buttons and control

## ESP32-C6 - Pin Allocation

### Communication pins
- **SPI_CLK**: Clock for SPI interface (connected to Flash, SD Card, Display)
- **SPI_MOSI**: Master Out Slave In for SPI
- **SPI_MISO**: Master In Slave Out for SPI
- **SS_SD**: Chip Select for SD Card
- **SS_FLASH**: Chip Select for Flash memory
- **SS_DISP**: Chip Select for E-Ink Display
- **I2C_SCL**: Clock for I2C interface
- **I2C_SDA**: Data line for I2C
- **EPD_DC**: Data/Command for E-Ink display
- **EPD_RST**: Reset for E-Ink display
- **EPD_BUSY**: Status signal from E-Ink display

### Other specific pins
- **RTC_INT**: Interrupt from RTC module
- **VBAT**: Battery power
- **3V3**: 3.3V power
- **GND**: Ground

# Bill of Materials

| Component | Model | Datasheet |
|-----------|--------------|-----------|
| BD5229G-TR | [Model](https://www.digikey.ee/en/models/658502) | [Datasheet](https://www.rohm.com/datasheet?p=BD5229G&dist=Digi-key&media=referral&source=digi-key.com&campaign=Digi-key) |
| ESP32 WROVER 0805 Capacitor | [Model](https://ro.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) | [Datasheet](https://ro.mouser.com/datasheet/2/40/schottky-3165252.pdf) |
| 112A-TAAR-R03 | [Model](https://www.snapeda.com/parts/112A-TAAR-R03/Attend/view-part/) | [Datasheet](https://www.snapeda.com/parts/112A-TAAR-R03/Attend/datasheet/) |
| 744043680 | [Model](https://ro.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D) | [Datasheet](https://www.we-online.com/components/products/datasheet/744043680.pdf) |
| LED Chip 0603 | [Model](https://grabcad.com/library/0603-smd-led-1) | [Datasheet](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/datasheet/) |
| MAX17048G+T10 | [Model](https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/MAX17048G+T10/Analog%20Devices/datasheet/) |
| MBR0530 Schottky Diode | [Model](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/MBR0530/ON%20Semiconductor/datasheet/) |
| PGB1010603MR | [Model](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse%20Inc./datasheet/) |
| QWIIC Connector | [Model](https://www.snapeda.com/parts/PRT-14417/SparkFun/view-part/) | [Datasheet](https://www.snapeda.com/parts/PRT-14417/SparkFun%20Electronics/datasheet/) |
| ESP32 WROVER BME680 Sensor | [Model](https://www.digikey.ro/en/models/7401317) | [Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme680-ds001.pdf) |
| FH34SRJ-24S-0.5SH | [Model](https://www.snapeda.com/parts/FH34SRJ-24S-0.5SH(99)/Hirose/view-part/) | [Datasheet](https://www.snapeda.com/parts/FH34SRJ-24S-0.5SH(99)/Hirose%20Connector/datasheet/) |
| Resistor 0402 | [Model](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) | [Datasheet](https://www.yageo.com/upload/media/product/products/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf) |
| ESP32 WROVER MCP73831 Power Management | [Model](https://www.snapeda.com/parts/MCP73831T-2ACI/OT/Microchip/view-part/) | [Datasheet](https://www.snapeda.com/parts/MCP73831T-2ACI/OT/Microchip/datasheet/) |
| ESP32C6 Varistor 1812 | [Model](https://www.snapeda.com/parts/RC0603JR-070RL/Yageo/view-part/) | [Datasheet](https://www.snapeda.com/parts/RC0603JR-070RL/Yageo/datasheet/) |
| ESP32C6 WROOM-1-N8 | [Model](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif%20Systems/datasheet/) |
| Capacitor 0402 | [Model](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) | [Datasheet](https://componentsearchengine.com/Datasheets/2/CC0402MRX5R5BB106.pdf) |
| SI1308EDL-T1-GE3 MOSFET | [Model](https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay+Siliconix/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay%20Siliconix/datasheet/) |
| SJ | [Model](https://grabcad.com/library/solder-jumpers-1) | [Datasheet]() |
| CPH3225A | [Model](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/CPH3225A/Seiko%20Instruments/datasheet/) |
| Button | [Model](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) | [Datasheet](https://industry.panasonic.com/global/en/downloads?tab=catalog&small_g_cd=203&part_no=EVQPUJ02K) |
| DS3231SN | [Model](https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/DS3231SN%23/Analog%20Devices/datasheet/) |
| USBLC6-2SC6Y | [Model](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) | [Datasheet](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/datasheet/) |
| W25Q512JVEIQ | [Model](https://www.digikey.ro/en/models/10244706) | [Datasheet](https://www.winbond.com/resource-files/W25Q512JV%20SPI%20RevB%2006252019%20KMS.pdf) |
| XC6220A331MR-G | [Model](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [Datasheet](https://product.torexsemi.com/system/files/series/xc6220.pdf) |
| TPTP20R | [Model](https://ro.mouser.com/ProductDetail/Adafruit/3825?qs=%252bEew9%252b0nqrAn6n76%252bB5vZg%3D%3D&utm_source=findchips&utm_medium=aggregator&utm_campaign=3825&utm_term=3825&utm_content=Adafruit&_gl=1*1t6jdbp*_ga*MTQ5NTQ1ODI1LjE3NDMyMzgzNTY.*_ga_15W4STQT4T*MTc0Mzc4MDU5Ni4xMi4xLjE3NDM3ODM2MzIuNDIuMC4w) | [Datasheet](https://cdn-shop.adafruit.com/product-files/3825/3825_diagram.PDF) |
| USB4110-GF-A | [Model](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)) | [Datasheet](https://gct.co/files/drawings/usb4110.pdf) |


# Other images

![image7](https://github.com/user-attachments/assets/dc42971f-ae28-43a6-8cb5-bb3610e25a13)
![Screenshot 2025-04-06 194247](https://github.com/user-attachments/assets/bac51ebf-e645-47f2-8099-25c2ea2e21cb)
