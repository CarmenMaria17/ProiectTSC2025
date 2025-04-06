# ProiectTSC2025

# Diagrama Bloc

![image](https://github.com/user-attachments/assets/395cf2fa-9804-4bfd-8931-e923f9c445ed)

# Bill Of Materials

| Component | Datasheet Link |
|-----------|---------------|
| ESP32-C6-WROOM-1-N8 | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-c6-wroom-1_datasheet_en.pdf) |
| W25Q512JVEIQ | [Datasheet](https://www.winbond.com/resource-files/W25Q512JV%20RevI%20112518.pdf) |
| DS3231SN# | [Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/ds3231.pdf) |
| BME680 | [Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme680-ds001.pdf) |
| USB4110-GF-A | [Datasheet](https://www.gct.co/connector/usb4110) |
| MCP73831T-5ACI/OT | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/MCP73831-Family-Data-Sheet-DS20001984H.pdf) |
| BD5229G-TR | [Datasheet](https://fscdn.rohm.com/en/products/databook/datasheet/ic/power/linear_regulator/bd5230g-e.pdf) |
| XC6220A331MR-G | [Datasheet](https://www.torexsemi.com/file/xc6220/XC6220.pdf) |
| MAX17048G+T10 | [Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/max17048-max17049.pdf) |
| USBLC6-2SC6Y | [Datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf) |
| PGB1010603MR | [Datasheet](https://www.littelfuse.com/~/media/electronics/datasheets/esd_suppression/littelfuse_esd_suppression_pgb1_datasheet.pdf.pdf) |
| DMG2305UX-7 | [Datasheet](https://www.diodes.com/assets/Datasheets/DMG2305UX.pdf) |
| Si1308EDL-T1-GE3 | [Datasheet](https://www.vishay.com/docs/68834/si1308edl.pdf) |
| CPH3225A | [Datasheet](https://datasheet.lcsc.com/lcsc/2110251730_TXC-Corporation-7M-12000MAAE_C547233.pdf) |
| EVQPUJ02K | [Datasheet](https://industrial.panasonic.com/cdbs/www-data/pdf/ATV0000/ATV0000C5.pdf) |
| KP-1608SURCK | [Datasheet](https://www.kingbright.com/attachments/file/psearch/000/00/00/KP-1608SURCK(Ver.15).pdf) |
| SD0805S020S1R0 | [Datasheet](https://www.bourns.com/docs/product-datasheets/sd.pdf) |
| PFMF | [Datasheet](https://www.littelfuse.com/~/media/electronics/datasheets/fuses/littelfuse_fuse_pfmf_datasheet.pdf) |
| R0402 | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/rchip/PYu-RC_Group_51_RoHS_L_11.pdf) |
| Condensatori SMD | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/mlcc/UPY-GPHC_X7R_16V-to-50V_18.pdf) |

# Descriere scurta

### Microcontroller
- **ESP32-C6**: Microcontroller principal cu WiFi/BLE, interfatare cu toate componentele prin SPI, I2C, UART si GPIO

### Display si stocare
- **Display E-Ink**: Interfatare prin SPI, consum minim (doar la refresh)
- **Slot SD Card**: Conectat prin SPI, pentru stocarea cartilor
- **Memorie Flash NOR W25Q512JVEIQ (64MB)**: Conectata prin SPI, pentru firmware si cache

### Alimentare
- **Conector USB-C** cu protectie ESD: Pentru incarcare si transfer date
- **Circuit incarcare baterie**: Controlor MCP73832 pentru bateria LiPo
- **Baterie LiPo**: 3.7V, alimenteaza intregul sistem
- **Regulator LDO 3.3V**: Furnizeaza tensiune stabilizata pentru ESP32 si periferice
- **Convertor DC/DC 5V/1A**: Pentru componentele care necesita 5V

### Senzori
- **BME680/688**: Senzor de mediu (temperatura, umiditate, presiune), conectat prin I2C
- **Optional**: Senzori PM si CO2 conectati prin UART (conform diagramei bloc)

### Alte componente
- **Modul RTC DS3231**: Ceas in timp real cu baterie backup, conectat prin I2C
- **Butoane (3 unitati)**: Pentru navigare si control, conectate direct la GPIO
- **Selector tip display**: Circuit pentru configurarea diferitelor tipuri de display E-Ink
- **Supervisor de tensiune si butoane Reset/IO**: Pentru monitorizarea tensiunii si control

### Interfete de comunicatie
- **SPI**: Display E-Ink, card SD, memorie flash
- **I2C**: Senzor BME680, modul RTC
- **UART**: Optional pentru senzorii externi
- **GPIO**: Butoane, control power management

### Consum energetic
Sistemul este proiectat pentru consum minim, cu multiple moduri de functionare:
- Mod activ (citire): ~50mA
- Mod standby: ~5-10mA
- Mod deep sleep: <1mA

# ESP32-C6 - Alocarea pinilor

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

### Pini de control si interfata utilizator
- **BTN_1**: Buton 1 pentru navigare
- **BTN_2**: Buton 2 pentru navigare/confirmare
- **BTN_3**: Buton 3 pentru navigare
- **BOOT**: Buton pentru boot/programare
- **RESET**: Pin de reset hardware

### Pini pentru management energie
- **BAT_ADC**: Masurare nivel baterie
- **PWR_CTRL**: Control alimentare
- **USB_DET**: Detectie conectare USB
- **CHG_STAT**: Status incarcare baterie

### Alte pini specifici
- **RTC_INT**: Intrerupere de la modulul RTC
- **VBAT**: Alimentare de la baterie
- **3V3**: Alimentare 3.3V
- **GND**: Masa

Aceasta alocare permite interfatarea eficienta cu toate componentele sistemului OpenBook.

# Alte poze

![Screenshot 2025-04-06 194355](https://github.com/user-attachments/assets/f6a0d3d8-5469-4f42-b72e-c700dec84ab4)
![Screenshot 2025-04-06 194247](https://github.com/user-attachments/assets/bac51ebf-e645-47f2-8099-25c2ea2e21cb)



