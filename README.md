# ProiectTSC2025

## Diagrama Bloc

![image](https://github.com/user-attachments/assets/cf016ced-38cc-4f77-a24d-0b3fbc02e55c)


## Descriere scurta

### Microcontroller
- **ESP32-C6**: Procesor principal cu WiFi/BLE, controlează toate componentele

### Display și Stocare
- **Display E-Ink**: Afișaj cu consum minim (1.5" 200x200px)
- **Card SD**: Stocarea cărților electronice
- **Memorie Flash 64MB**: Pentru firmware și cache

### Alimentare
- **USB-C**: Încărcare și transfer date
- **Circuit încărcare baterie**: MCP73831 pentru bateria LiPo
- **Baterie LiPo**: Alimentare portabilă 3.7V
- **Regulator 3.3V**: Stabilizator tensiune pentru ESP32 și senzori

### Senzori
- **BME680**: Temperatură și umiditate, conexiune I2C

### Alte Componente
- **RTC DS3231**: Ceas în timp real pentru timekeeping
- **Butoane**: Navigare și control prin GPIO

### Interfețe
- **SPI**: Display, card SD, memorie flash
- **I2C**: Senzori, RTC
- **GPIO**: Butoane și control

## ESP32-C6 - Alocarea pinilor

### Pini pentru comunicatie
- **SPI_CLK**: Clock pentru interfata SPI (conectat la Flash, SD Card, Display)
- **SPI_MOSI**: Master Out Slave In pentru SPI
- **SPI_MISO**: Master In Slave Out pentru SPI
- **SS_SD**: Chip Select pentru SD Card
- **SS_FLASH**: Chip Select pentru memoria Flash
- **SS_DISP**: Chip Select pentru Display E-Ink
- **I2C_SCL**: Clock pentru interfata I2C
- **I2C_SDA**: Linia de date pentru I2C
- **EPD_DC**: Data/Command pentru display-ul E-Ink
- **EPD_RST**: Reset pentru display-ul E-Ink
- **EPD_BUSY**: Semnal de status de la display-ul E-Ink

### Alte pini specifici
- **RTC_INT**: Intrerupere de la modulul RTC
- **VBAT**: Alimentare de la baterie
- **3V3**: Alimentare 3.3V
- **GND**: Masa

# Bill of Materials

| Componenta | Model | Datasheet |
|-----------|--------------|-----------|
| ESP32-C6-WROOM-1-N8 | [Model](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://www.mouser.com/catalog/specsheets/Espressif_ESP32_C6_WROOM_1%20_Datasheet_V0.1_PRELIMINARY_en.pdf?srsltid=AfmBOooHQKNitqODRaaPjoZInfWKTacDER1t5uRK6sKqT13TrzvVo_B7) |
| BME680 | [Model](https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme680-ds001.pdf) |
| DS3231SN# | [Model](https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda) | [Datasheet](https://www.alldatasheet.com/view.jsp?Searchword=Ds3231sn%20datasheet&gad_source=1&gbraid=0AAAAADcdDU-Gy9URfMxGmqiPg7ci5L3wR&gclid=Cj0KCQjwqcO_BhDaARIsACz62vMkK3ETSnW2w7mo0Fa-wgWJGn89AxWCyIND6k5X8MmoPl6hv6VWwT8aAiS-EALw_wcB) |
| W25Q512JVEIQ | [Model](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://www.mouser.com/datasheet/2/949/W25Q512JV_SPI_RevB_06252019_KMS-2487502.pdf?srsltid=AfmBOoquExqDVgxEELF9CzuOGxHos0CD1nQDROHD6Eebdm2foNzqozqU) |
| MCP73831T-5ACI/OT | [Model](https://www.mouser.co.uk/ProductDetail/Microchip-Technology/MCP73831T-5ACI-OT?qs=hH%252BOa0VZEiAcgAcEkuamXg%3D%3D) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://ww1.microchip.com/downloads/en/DeviceDoc/MCP73831-Family-Data-Sheet-DS20001984H.pdf) |
| MAX17048G+T10 | [Model](https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda) | [Datasheet](https://www.alldatasheet.com/view.jsp?Searchword=Max17048&gad_source=1&gbraid=0AAAAADcdDU8aYfZtfJfdZ9I5j6RwZ_cbA&gclid=Cj0KCQjwqcO_BhDaARIsACz62vNa9xrVfzjCjADRwXD0RBbo4Nret3ywwteDGLJKZui8ZL8KdVlTE7caAvQxEALw_wcB) |
| USB4110-GF-A | [Model](https://componentsearchengine.com/part-view/USB4110-GF-A/GCT%20(GLOBAL%20CONNECTOR%20TECHNOLOGY)) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://gct.co/files/drawings/usb4110.pdf) |
| XC6220A331MR-G | [Model](https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex) | [Datasheet](https://www.alldatasheet.com/view.jsp?Searchword=Xc6220&gad_source=1&gbraid=0AAAAADcdDU8aYfZtfJfdZ9I5j6RwZ_cbA&gclid=Cj0KCQjwqcO_BhDaARIsACz62vPS06NB6tLgniZzfaVpKNu1m811BNk6AEPfg4DbP6f5S8QWA_pW_UQaAv-0EALw_wcB) |
| USBLC6-2SC6Y | [Model](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) | [Datasheet](https://www.digikey.com/en/htmldatasheets/production/1375342/0/0/1/usblc6-2sc6y) |
| KP-1608SURCK | [Model](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) | [Datasheet](//efaidnbmnnnibpcajpcglclefindmkaj/https://media.elv.com/file/107153_led_surck1608_data.pdf) |
| CPH3225A | [Model](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) | [Datasheet](https://octopart.com/datasheet/cph3225a-seiko-25340571) |
| BUTTON | [Model](https://industry.panasonic.com/global/en/products/control/switch/light-touch/number/evqpuj02k) | [Datasheet](https://www.lcsc.com/datasheet/lcsc_datasheet_2201121800_PANASONIC-EVQPUJ02K_C2936858.pdf) |

# Alte poze

![Screenshot 2025-04-06 194355](https://github.com/user-attachments/assets/f6a0d3d8-5469-4f42-b72e-c700dec84ab4)
![Screenshot 2025-04-06 194247](https://github.com/user-attachments/assets/bac51ebf-e645-47f2-8099-25c2ea2e21cb)



