# ココ・シール ハードウェア設計

## データシートなど

### 基本的モジュール

MCU: [ESP32-C3-WROOM-02-N4](https://documentation.espressif.com/esp32-c3-wroom-02_datasheet_en.pdf)

LoRa: [E220-900T22S(JP)](https://dragon-torch.tech/rf-modules/lora/e220-900t22s-jp/#04)

3.3v 600mA レギュレータ: [AP2112K-3.3TRG1](https://www.diodes.com/assets/Datasheets/AP2112.pdf)

OLED: [SSD1306](https://akizukidenshi.com/goodsaffix/ssd1306.pdf)

ブザー: [PKB24SPCH3601-B0](https://akizukidenshi.com/goodsaffix/murata-piezo-buzzer.pdf)

### バッテリー回路

充電IC: [TP4056](https://www.lcsc.com/datasheet/C16581.pdf)

Li-ion保護IC: [DW01A](https://hmsemi.com/downfile/DW01A.PDF)

デュアルMOSFET: [FS8205A](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/7158/5272_FS8205A.pdf)

### その他

ESD保護素子(D+D-の静電気などの保護): [TPD2EUSB30A](https://www.ti.com/product/ja-jp/TPD2EUSB30A)

## GPIO割り当て

|GPIO|機能|入出力|周辺回路|プルアップ/プルダウン|備考|
|:-:|:-:|:-:|:-:|:-:|:-:|
|0
|1
|2
|3
|4
|5
|6
|7
|8
|9
|10
|18|USB D-|I/O|USB-C D-|-|ESD保護素子を挟む
|19|USB D+|I/O|USB-C D+|-|ESD保護素子を挟む
|20|UART TXD|OUT|LoRa RXD|-|固定|
|21|UART RXD|IN|LoRa TXD|-|固定|