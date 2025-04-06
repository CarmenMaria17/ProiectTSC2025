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

# Bill Of Materials

| Componenta | Datasheet| Model |
|-----------|---------------|----------------|
| ESP32-C6-WROOM-1-N8 | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-c6_datasheet_en.pdf) | [Model](https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif+Systems/view-part/?ref=eda) |
| W25Q512JVEIQ | [Datasheet](https://www.winbond.com/resource-files/W25Q512JV%20RevI%2005132020%20Plus.pdf) | [Model](https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=eda) |
| DS3231SN# | [Datasheet](https://datasheets.maximintegrated.com/en/ds/DS3231.pdf) | [Model](https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda) |
| MAX17048G+T10 | [Datasheet](https://datasheets.maximintegrated.com/en/ds/MAX17048-MAX17049.pdf) | [Model](https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda) |
| BME688 | [Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme688-ds000.pdf) | [Model](https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home) |
| MCP73831 | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/20001984g.pdf) | [Model](https://www.mouser.co.uk/ProductDetail/Microchip-Technology/MCP73831T-5ACI-OT?qs=hH%252BOa0VZEiAcgAcEkuamXg%3D%3D) |
| BD5229G-TR | [Datasheet](https://fscdn.rohm.com/en/products/databook/datasheet/ic/power/voltage_detector/bd52xxg-e.pdf) | [Model](https://componentsearchengine.com/part-view/BD5229G-TR/ROHM%20Semiconductor) |
| PFMF.050.1 | [Datasheet](https://cdn.amphenol-cs.com/media/wysiwyg/files/drawing/pfmf.pdf) | [Model](https://www.mouser.com/ProductDetail/Amphenol-FCI/PFMF0501?qs=sGAEpiMZZMulM8LYMF8bxyg6IYwX%252B5CgQVcIoLYkYiM%3D) |
| USBLC6-2SC6Y | [Datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf) | [Model](https://www.snapeda.com/parts/USBLC6-2SC6Y/STMicroelectronics/view-part/?ref=eda) |
| 112A-TAAR-R03 | [Datasheet](https://www.attend.com.tw/sites/default/files/2022-05/112A-TAAR-R03.pdf) | [Model](https://www.mouser.com/ProductDetail/Attend/112A-TAAR-R03?qs=sGAEpiMZZMsg%2By7HCF96QHhTCuZhYGBTHJ9NEpPMzZc%3D) |
| FH34SRJ-24S-0.5SH | [Datasheet](https://www.hirose.com/product/document?clcode=CL0684-0832-7-99&productname=FH34SRJ-24S-0.5SH(99)&series=FH34&documenttype=Catalog&lang=en&documentid=D49681_en) | [Model](https://www.hirose.com/product/p/CL0684-0832-7-99) |
| DMG2305UX-7 | [Datasheet](https://www.diodes.com/assets/Datasheets/DMG2305UX.pdf) | [Model](https://www.diodes.com/part/view/DMG2305UX) |
| SI1308EDL-T1-GE3 | [Datasheet](https://www.vishay.com/docs/68732/si1308edl.pdf) | [Model](https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay+Siliconix/view-part/?ref=snap) |
| SD0805S020S1R0 | [Datasheet](http://datasheets.avx.com/schottky.pdf) | [Model](https://eu.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D) |
| MBR0530 | [Datasheet](https://www.onsemi.com/pdf/datasheet/mbr0520lt1-d.pdf) | [Model](https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=eda) |
| PGB1010603MR | [Datasheet](https://www.littelfuse.com/media?resourcetype=datasheets&itemid=3d1e98b7-4d37-463c-9380-c56c83b11c3c&filename=littelfuse-pulseguard-pgb1) | [Model](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda) |
| CPH3225A | [Datasheet](https://www.sii.co.jp/en/quartz/files/2021/03/CPH3225A_E.pdf) | [Model](https://www.snapeda.com/parts/CPH3225A/Seiko+Instruments/view-part/?ref=eda) |
| XC6220A331MR-G | [Datasheet](https://www.torexsemi.com/file/xc6220/XC6220.pdf) | [Model](https://www.torexsemi.com/products/voltage-regulators/ldo-regulators/xc6220/) |
| EVQPUJ02K | [Datasheet](https://industry.panasonic.com/ww/components/devices/mechanical-components/switches/light-touch-switches/products/evqpuj02k) | [Model](https://industry.panasonic.com/ww/products/industrial-devices/mechanical-components/switches/light-touch-switches/light-touch-switches/evqpuj02k) |
| KP-1608SURCK | [Datasheet](https://www.kingbrightusa.com/images/catalog/SPEC/APHHS1608LSURKCGKC.pdf) | [Model](https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/view-part/?ref=search&t=LED%200603) |
| QWIIC_RIGHT_ANGLE | [Datasheet](https://cdn.sparkfun.com/assets/1/4/d/8/3/Qwiic_Connector_Datasheet.pdf) | [Model](https://www.sparkfun.com/products/14417) |
| Rezistor SMD 0402 | [Datasheet](https://www.yageo.com/en/Product/resistors) | [Model](https://componentsearchengine.com/part-view/R0402%201%25%20100%20K%20(RC0402FR-07100KL)/YAGEO) |
| Capacitor SMD 0402 | [Datasheet](https://www.yageo.com/en/Product/mlcc) | [Model](https://componentsearchengine.com/part-view/CC0402MRX5R5BB106/YAGEO) |

# Alte poze

![Screenshot 2025-04-06 194355](https://github.com/user-attachments/assets/f6a0d3d8-5469-4f42-b72e-c700dec84ab4)
![Screenshot 2025-04-06 194247](https://github.com/user-attachments/assets/bac51ebf-e645-47f2-8099-25c2ea2e21cb)



