# ココ・シール ハードウェア設計

## 表面実装部品

[JLPCB表面実装可能部品検索](https://jlcpcb.com/parts)

データシートとか型番もここから持ってきたい

## データシートや製品ページ

### 基本的モジュール

- MCU(ESP32-C3-WROOM-02-N4)
  - [データシート](https://documentation.espressif.com/esp32-c3-wroom-02_datasheet_en.pdf)
  - [JLPCB](https://jlcpcb.com/partdetail/3281215-ESP32_C3_WROOM_02N4/C2934560)
  - [購入ページ](https://akizukidenshi.com/catalog/g/g117493/)

- LoRa(E220-900T22S(JP))
  - [データシート](https://dragon-torch.tech/rf-modules/lora/e220-900t22s-jp/)
  - [購入ページ](https://akizukidenshi.com/catalog/g/g131361/)

- 3.3v 600mA レギュレータ(AP2112K-3.3TRG1)
  - [JLPCB](https://jlcpcb.com/partdetail/TECHPUBLIC-AP2112K_33TRG1/C23380830)
  - [データシート](./datasheets/AP2112K.pdf)

- OLED(SSD1306)
  - [データシート](https://akizukidenshi.com/goodsaffix/ssd1306.pdf)
  - [購入ページ](https://akizukidenshi.com/catalog/g/g112031/)

- ブザー(PKB24SPCH3601-B0)
  - [JLPCB](https://jlcpcb.com/partdetail/MurataElectronics-PKB24SPCH3601B0/C440255)
  - [データシート](https://akizukidenshi.com/goodsaffix/murata-piezo-buzzer.pdf)

- 2色LED(LT6CU7R)
  - [購入ページ](https://akizukidenshi.com/catalog/g/g108982/)
  - [データシート](https://akizukidenshi.com/goodsaffix/LT6CU7R.pdf)

### バッテリー回路

- 充電IC(TP4056-42-ESOP8)
  - [JLPCB](https://jlcpcb.com/partdetail/17264-TP4056_42ESOP8/C16581)
  - [データシート](https://www.lcsc.com/datasheet/C16581.pdf)

- Li-ion保護IC(DW01A)
  - [JLPCB](https://jlcpcb.com/partdetail/PUOLOP-DW01A/C351410)
  - [データシート](https://hmsemi.com/downfile/DW01A.PDF)

- デュアルMOSFET(FS8205A)
  - [JLPCB](https://jlcpcb.com/partdetail/TECHPUBLIC-FS8205A/C2830320)
  - [データシート](./datasheets/FS8205A.pdf)

### その他

- ESD保護素子(D+D-の静電気などの保護)(TPD2EUSB30A)
  - [JLPCB](https://jlcpcb.com/partdetail/TexasInstruments-TPD2EUSB30ADRTR/C94934)
  - [データシート](https://www.ti.com/cn/lit/ds/symlink/tpd2eusb30a.pdf)

- MMOSFET(AO3400A)
  - [JLPCB](https://jlcpcb.com/partdetail/Alpha_OmegaSemicon-AO3400A/C20917)
  - [データシート](./datasheets/AO3400A.pdf)

## GPIO割り当て

Strapping pins に割り当てられているため、2, 8, 9 はちょっと使いづらい

|GPIO|機能|入出力|周辺回路|プルアップ/プルダウン|備考|
|:-:|:-:|:-:|:-:|:-:|:-:|
|0|ADC|IN|バッテリー電圧分圧回路|-|R1=R2=100kΩくらい|
|1|GPIO|IN|タクトスイッチ1|プルアップ|
|2|GPIO|OUT|2色LED_R|プルアップ|Strapping Pin, 起動時に誤点灯の可能性あり|
|3|GPIO|OUT|ブザー制御MOSFET|-|MOSFETを通してバッテリーから直で電源供給予定|
|4|I2C|I/O|OLED SDA|-|おそらくモジュール側でPU実装済|
|5|I2C|I/O|OLED SCK|-|おそらくモジュール側でPU実装済|
|6|GPIO|OUT|LoRa M1|-|
|7|GPIO|OUT|LoRa M0|-|
|8|GPIO|OUT|2色LED_G|プルアップ|Strapping Pin, 起動時に誤点灯の可能性あり|
|9|GPIO|IN|タクトスイッチ2|プルアップ|Strapping Pin, 押しながら起動するとDownload Mode として起動|
|10|GPIO|IN|LoRa AUX|-|
|18|USB D-|I/O|USB-C D-|-|ESD保護素子を挟む|
|19|USB D+|I/O|USB-C D+|-|ESD保護素子を挟む|
|20|UART TXD|OUT|LoRa RXD|-|固定|
|21|UART RXD|IN|LoRa TXD|-|固定|