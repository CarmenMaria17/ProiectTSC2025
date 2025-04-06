# ProiectTSC2025

# Diagrama Bloc

![image](https://github.com/user-attachments/assets/6be7cce0-c347-423c-88e3-3e90b86d44f9)


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

# Bill of Materials - OpenBook Project

| Component | Description | Datasheet | Purchase Link |
|-----------|-------------|-----------|--------------|
| ESP32-C6-WROOM-1-N8 | Main microcontroller module | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-c6_datasheet_en.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Espressif-Systems/ESP32-C6-WROOM-1-N8) |
| W25Q512JVEIQ | 64MB External NOR Flash Memory | [Datasheet](https://www.winbond.com/resource-files/W25Q512JV%20RevI%2005132020%20Plus.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Winbond/W25Q512JVEIQ) |
| DS3231SN | Real-Time Clock Module | [Datasheet](https://datasheets.maximintegrated.com/en/ds/DS3231.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Analog-Devices-Maxim-Integrated/DS3231SN) |
| BME688 | Environmental Sensor (Temp/Humidity) | [Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme688-ds000.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Bosch-Sensortec/BME688) |
| MCP73831 | LiPo Battery Charging Controller | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/20001984g.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Microchip-Technology/MCP73831T-5ACI-OT) |
| MAX17048G+T10 | Battery Fuel Gauge | [Datasheet](https://datasheets.maximintegrated.com/en/ds/MAX17048-MAX17049.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Analog-Devices-Maxim-Integrated/MAX17048G%2bT10) |
| XC6220A331MR-G | 3.3V LDO Voltage Regulator | [Datasheet](https://www.torexsemi.com/file/xc6220/XC6220.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Torex-Semiconductor/XC6220A331MR-G) |
| PFMF.050.1 | USB-C Connector | [Datasheet](https://cdn.amphenol-cs.com/media/wysiwyg/files/drawing/pfmf.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Amphenol-FCI/PFMF0501) |
| USBLC6-2SC6Y | USB ESD Protection | [Datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf) | [Mouser](https://www.mouser.com/ProductDetail/STMicroelectronics/USBLC6-2SC6Y) |
| FH34SRJ-24S-0.5SH | E-Paper Display Connector | [Datasheet](https://www.hirose.com/product/document?clcode=CL0684-0832-7-99&productname=FH34SRJ-24S-0.5SH(99)&series=FH34&documenttype=Catalog&lang=en&documentid=D49681_en) | [Mouser](https://www.mouser.com/ProductDetail/Hirose-Connector/FH34SRJ-24S-0.5SH) |
| 112A-TAAR-R03 | SD Card Connector | [Datasheet](https://www.attend.com.tw/sites/default/files/2022-05/112A-TAAR-R03.pdf) | [Mouser](https://www.mouser.com/ProductDetail/Attend/112A-TAAR-R03) |
| EVQPUJ02K | Tactile Switches (Buttons) | [Datasheet](https://industry.panasonic.com/ww/components/devices/mechanical-components/switches/light-touch-switches/products/evqpuj02k) | [Mouser](https://www.mouser.com/ProductDetail/Panasonic/EVQPUJ02K) |

# Alte poze

![Screenshot 2025-04-06 194355](https://github.com/user-attachments/assets/f6a0d3d8-5469-4f42-b72e-c700dec84ab4)
![Screenshot 2025-04-06 194247](https://github.com/user-attachments/assets/bac51ebf-e645-47f2-8099-25c2ea2e21cb)



