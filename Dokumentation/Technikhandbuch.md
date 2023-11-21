# Technikhandbuch
![Jolibox](Dokumentation/../images/Jolibox-Transparent.png)

Harald Woizischke
info@woizischke.de


Technische Beschreibung einer Kinder-Musikbox auf Basis eines ESP32. 
Kinder können die Musik oder Hörspiele mit Rfid-Tags auswählen.
Die Konfiguration der Box erfolgt über eine Webschnittstelle im Browser.

# Einleitung
Dieses Dokument beschreibt alle zum Bau notwendigen Komponenten.
Die Gehäuseteile wurden mit Autocad Fusion 360 entworfen und mit einem 3D-Drucker in PLA gedruckt.
Als Systemplattform wurde die Lösung von Torsten Stauder (biologist) gewählt. Einzelheiten zum Projekt sind im Internet unter https://forum.espuino.de/ zu finden.

#Elektronik Baugruppen
Es wurden folgende Baugruppen und Bauteile zur Realisierung eingesetzt.
- ESPuino-mini 4Layer von biologist - https://forum.espuino.de/t/espuino-mini-4layer/1661/1
- D32 pro FePo. von biologist - https://forum.espuino.de/t/develboard-d32-pro-lifepo4/1109
- Tastatur auf Lochrasterplatine. Tasten aus Set - https://de.aliexpress.com/item/1005003510575948.html?spm=a2g0o.order_list.order_list_main.16.d9f15c5fe9UN4b&gatewayAdapt=glo2deu
- Akku 18650 3.2V 2.000mAh LiFePO4 - https://www.eremit.de/p/18650-3-2v-2-000mah-lifepo4
- Zusatzplatine für Akkuhalterung auf Lochrasterplatine
- Visaton vs-f8sc/8 Lautsprecher - https://www.amazon.de/dp/B0056BQXCW?psc=1&ref=ppx_yo2ov_dt_b_product_details
- RFID-Reader RC522
- 12 LED aus 5v RGB LED-Streifen WS2812B 144 Pixel/m - https://www.amazon.de/gp/product/B08P6XN49P/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1 
- 3mm LED rot für Ladeanzeige
- USB-C Ladebuchse - https://de.aliexpress.com/item/1005004913934656.html?spm=a2g0o.order_list.order_list_main.26.d9f15c5fe9UN4b&gatewayAdapt=glo2deu
- Micro-Switch für Not-Reset - https://www.amazon.de/VILLCASE-Endschalter-Scharnierhebel-Steuerung-Mikroschalter/dp/B08H52SDG2/ref=d_pd_sbs_sccl_3_3/260-8649301-8058855?pd_rd_w=cNDNg&content-id=amzn1.sym.41628bd4-d899-4783-a506-d8de0d1214b9&pf_rd_p=41628bd4-d899-4783-a506-d8de0d1214b9&pf_rd_r=3GDTZH136VNYB0NSFS06&pd_rd_wg=YOhk4&pd_rd_r=c7a0bea7-4bae-44c3-859b-27eb5bccfb86&pd_rd_i=B08H52SDG2&psc=1 
- Amazon BASIC PLA - https://www.amazon.de/gp/product/B07CTQDQ77/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1

# ESPuino-mini_4Layer
 ![ESPuino-mini_4Layer](images/ESPuino-mini_4Layer.png)

# D32_FePo_rev4
![D32_FePo_rev4](images/D32_FePo_rev4.png)

# Kabelplan

## RFID-Reader 5180
```
Stecker         Farbe           PN5180
5V     ------   sw   ---------  5V
3.3V   ------   rt   ---------  3.3	
RST    ------   ws   ---------  RST
CS     ------   ge   ---------  NSS
MOSI   ------   or   ---------  MOSI
MISO   ------   gn   ---------  MISO
SCK    ------   bl   ---------  SCK
BSY    ------   vi   ---------  BUSY
IRQ    ------   gr   ---+  +--  GND
GND    ------   br   ---|--+    GPIO
                        +----   IRQ
                                AUX
                                REQ 
```

## Rotary-Encoder
```
Stecker     Farbe           Encoder
DT  -----   sw   -+    +-  CLK
CLK -----   rt   -+----+-  DT
BTN -----   ws   --------  SW
3.3 -----   ge   --------  +
GND -----   or   --------  GND
```

## NeoPixel
```
Stecker     Farbe          LED-Stripe	
-   -----   rt    -------  -	
D1  -----   sw    -------  D0
+   -----   ge    -------  5V
```