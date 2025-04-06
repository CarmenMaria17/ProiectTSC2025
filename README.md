# ProiectTSC2025

# Diagrama Bloc

![image](https://github.com/user-attachments/assets/395cf2fa-9804-4bfd-8931-e923f9c445ed)

# Bill Of Materials

| Component | Link Achiziție | Datasheet |
|-----------|---------------|-----------|
| ESP32-C6-WROOM-1-N8 |  | |
| W25Q512JVEIQ | | |
| DS3231SN# | | |
| BME680 | |
| USB4110-GF-A ||
| MCP73831T-5ACI/OT | |
| BD5229G-TR | |
| XC6220A331MR-G | |
| MAX17048G+T10 | |
| USBLC6-2SC6Y | |
| PGB1010603MR  ||
| DMG2305UX-7 | |
| Si1308EDL-T1-GE3 |  |
| CPH3225A | |
| EVQPUJ02K |  |
| KP-1608SURCK | |
| SD0805S020S1R0 |  |
| PFMF | |
| R0402 | |
| Condensatori SMD |  |

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


