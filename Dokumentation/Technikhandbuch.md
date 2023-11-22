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

# Hardware
## Elektronik Baugruppen
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

## ESPuino-mini_4Layer
 ![ESPuino-mini_4Layer](images/ESPuino-mini_4Layer.png)
 ![Espuino-mini_1](images/ESPuino-mini-Schaltung-1.png)
 ![Espuino-mini_2](images/ESPuino-mini-Schaltung-2.png)
 ![Espuino-mini_3](images/ESPuino-mini-Schaltung-3.png)
 ![Espuino-mini_4](images/ESPuino-mini-Schaltung-4.png)
 ![Espuino-mini_5](images/ESPuino-mini-Schaltung-5.png)
 ![Espuino-mini_6](images/ESPuino-mini-Schaltung-6.png)
 ** Hardware Konfiguration **
Auf Unterseite der Platine befinden sich mehrere Lötbrücken (JP1 bis JP7, JP5 fehlt), die konfiguriert werden können bzw. müssen. Sie werden im Folgenden beschrieben. Kursiv markiert ist die Konfiguration, die aus meiner Sicht „standard“ ist (sofern anwendbar):
JP1: *Schließe* 1+2 wenn du kein LPCD benötigst (Normalzustand). Schließe 2+3, wenn du LPCD benötigst. Auswirkung: Für LPCD wird das RFID-Modul dauerhaft mit Spannung versorgt, so dass eine etwas höhere Stromaufnahme im Deepsleep anfällt. Vergisst du JP1 komplett, so wird dein RFID-Reader nicht funktionieren, da er (egal wann) keine Versorgungsspannung erhält. Hinweis: Willst du dieses Feature nutzen, dann musst du auch die Brücke von JP4 schließen. Sollte dir unklar sein, was LPCD bedeutet, so findest du hier die Erklärung: 📗 [Was ist LPCD und wie funktioniert es?](https://forum.espuino.de/t/was-ist-lpcd-und-wie-funktioniert-es/1664).
**Pflicht!**
JP2: *Schließe* 1+2 wenn DT des Drehencoders auf GPI(O)39 geroutet werden soll. Schließe 2+3, wenn GPIO39 frei sein soll und DT stattdessen auf dem Port-Expander (109) landen soll. Stand jetzt (01/2023) macht ausschließlich GPIO Sinn, da ESPuino hier den Port-Expander noch nicht unterstützt. Vergisst du JP2 komplett, so funktioniert die Drehbewegung deines Drehencoders nicht (sofern du diesen verwendest).
**Pflicht wenn ein Drehencoder verwendet wird!**
JP3: Schließe 1+2 wenn CLK des Drehencoders auf GPIO34 geroutet werden soll. Schließe 2+3, wenn GPIO34 frei sein soll und DT stattdessen auf dem Port-Expander (110) landen soll. Stand jetzt (01/2023) macht ausschließlich GPIO Sinn, da ESPuino hier den Port-Expander noch nicht unterstützt. Vergisst du JP3 komplett, so funktioniert die Drehbewegung deines Drehencoders nicht (sofern du diesen verwendest).
**Pflicht wenn ein Drehencoder verwendet wird**
JP4: Schließe diese Brücke, wenn du LPCD verwenden möchtest (beachte dafür unbedingt auch JP1!).
**Optional!**
JP5: Gibt es nicht (mehr).
JP6: *Schließe* 1+2 wenn der 3.3 V-Pin am externen I2C-Konnektor dauerhaft mit Spannung versorgt werden soll. Schließe 2+3, wenn er im Deepsleep des ESP32 spannungslos geschaltet werden soll. Da so gut wie niemand bisher externe I2C-Devices anschließt, hat ein Vergessen der Brücke erstmal keine Auswirkungen. Hintergrund der Konfigurationsmöglichkeit ist [hier](https://forum.espuino.de/t/espuino-minid32-pro-lolin-d32-d32-pro-mit-sd-mmc-und-port-expander-smd/866/53) beschrieben.
**Optional!**
JP7: Wenn du einen zweiten MAX98357a 90 anschließen möchtest, dann solltest du diese Brücke schließen, so dass der aufgelötete MAX98357a nur den linken Kanal ausgibt. Der zweite MAX98357a wird automatisch den rechten Kanal ausgeben, so dass du stereo über zwei Lautsprecher nutzen kannst. Achte in diesem Falle auch drauf, dass du PLAY_MONO_SPEAKER auskommentieren musst.
**Optional!**

### Kabelplan

#### RFID-Reader 5180
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

#### Rotary-Encoder
```
Stecker     Farbe           Encoder
DT  -----   sw   -+    +-  CLK
CLK -----   rt   -+----+-  DT
BTN -----   ws   --------  SW
3.3 -----   ge   --------  +
GND -----   or   --------  GND
```

#### NeoPixel
```
Stecker     Farbe          LED-Stripe	
-   -----   rt    -------  -	
D1  -----   sw    -------  D0
+   -----   ge    -------  5V
```

## D32_FePo_rev4
![D32_FePo_rev4](images/D32_FePo_rev4.png)
![D32_FePo-Schaltung](images/D32_FePo-Schaltung-1.png)
![D32_FePo-Schaltung](images/D32_FePo-Schaltung-2.png)
![D32_FePo-Schaltung](images/D32_FePo-Schaltung-3.png)
![D32_FePo-Schaltung](images/D32_FePo-Schaltung-4.png)
![D32_FePo-Schaltung](images/D32_FePo-Schaltung-5.png)
> :warning:	**Wichtig**
> Auf keinen Fall darf ein LiPo-Akku angeschlossen werden. Der TP5000 unterstützt, wenn man ihn entsprechend beschaltet, zwar auch LiPo, ich habe ihn (aus Komplexitäts- und Platzgründen) jedoch fest auf FePo eingestellt. 
> Das Hauptproblem ist jedoch: Wird ein LiPo-Akku angeschlossen, so geht, je nach Akkuspannung (Ladung), mindestens das ESP32-Modul kaputt, weil die Spannung vom Akku (wie oben beschrieben und im Schaltplan sichtbar) nicht durch den Festspannungsregler läuft und Spannungen >3,6 V vom ESP32 nicht toleriert werden!!! LiPo liefert jedoch bis zu 4,2 V. Das Umgehen des Festspannungsreglers habe ich deswegen so gemacht, weil es die FePo-Spannung, die ja schon passt, unerwünscht reduzieren würde, wenn die Batteriespannung ebenfalls den gleichen Weg wie USB ginge.

## Zusatzplatine Akkuhalterung
Für den Anschuss von der Lade LED, dem Not-Reset-Schalter, der Ladebuchse und der Schutzschaltung für den Akku wurde eine Lochrasterplatine verwendet.
![Zusatzplatine-Layout](images/Zusatzplatine-Layout.png)
![Zusatzplatine-Schaltung](images/Zusatzplatine-Schaltung.png)

## Tastatur
![Tastatur](images/Tastatur.png)

# Software
## Dynamisches Button-Layout
Ursprünglich war in der Firmware des ESPuino fest verankert, dass die Bedienung über drei Tasten und einem Drehencoder zu erfolgen hat. Die Bedienung/Bedeutung der jeweiligen Tasten war dabei vorgegeben. Dies hat sich nun geändert: Tasten können nun wahlweise hinzugefügt und entfernt werden. Auch ist der Drehencoder nun optional.
An dieser Stelle sei erwähnt, dass das von mir empfohlene (und benutzte) Layout weiterhin drei Taster und ein Drehencoder ist. 
- Als neue Direktive in settings.h ist USEROTARY_ENABLE hinzugekommen. Wird kein Drehencoder gebraucht, so kann dies deaktiviert werden. Hinweis: Ist dies der Fall, so muss in der jeweiligen Develboard-spezifischen Config unbedingt WAKEUP_BUTTON angepasst werden.
- Mit dem eben bereits angesprochenen WAKEUP_BUTTON kann festgelegt werden, mit welcher Taste der ESPuino wieder aus dem Tiefschlaf geholt werden soll. Es ist an dieser Stelle darauf zu achten, dass nur sog. RTC-GPIOs 1 (0, 4, 12, 13, 14, 15, 25, 26, 27, 32, 33, 34, 35, 36, 39) verwendbar sind. Es können an dieser Stelle direkt Zahlen reingeschrieben werden oder aber z.B. auch Namen wie DREHENCODER_BUTTON oder NEXT_BUTTON. Soll dieses Feature deaktiviert werden, so ist eine 99 zu setzen. Nicht auskommentieren!
- In der Develboard-spezifischen Config sind die Tasten BUTTON_4 und BUTTON_5 hinzugekommen. Per Voreinstellung sind sie deaktiviert (99). Im Gegenzug können jedoch auch NEXT_BUTTON, PREVIOUS_BUTTON oder PAUSEPLAY_BUTTON wahlweise aktiviert oder deaktiviert werden.
- In settings.h können den Tastern nun beliebige Aktionen zugewiesen werden. Hierbei ist zu unterscheiden, ob es sich um eine Tastenkombination aus zwei Tasten (MULTI_n_SHORT) oder um eine einzige Taste (BUTTON_n_SHORT oder BUTTON_n_LONG) handelt. D.h. jeder einzelnen Taste kann man eine Aktion für kurzen Tastendruck und eine für langen Tastendruck zuweisen.
- Möchte man einer Taste keine Aktion zuweisen, so ist die Direktive CMD_NOTHING zu setzen. Dies muss entsprechend für einen kurzen und/oder langen Tastendruck gemacht werden.

Möchte man einer Taste eine Aktion zuweisen, so sind folgende Aktionen möglich (siehe values.h):

|Kommando	|Beschreibung|
------------|------------|
|CMD_LOCK_BUTTONS_MOD	|Sperrt alle Tasten und gibt sie [theoretisch] wieder frei. Macht als Tastenbelegung eher nicht so viel Sinn, da man mit gesperrten Tasten keine Tastenaktion mehr auslösen kann. Ist eher eine Aktion für Modifikationskarten.
|CMD_SLEEP_TIMER_MOD_15	|Schaltet sich nach 15 Minuten aus und LEDs werden gedimmt
|CMD_SLEEP_TIMER_MOD_30	|Schaltet sich nach 30 Minuten aus und LEDs werden gedimmt
|CMD_SLEEP_TIMER_MOD_60	|Schaltet sich nach 60 Minuten aus und LEDs werden gedimmt
|CMD_SLEEP_TIMER_MOD_120	|Schaltet sich nach 120 Minuten aus und LEDs werden gedimmt
|CMD_SLEEP_AFTER_END_OF_TRACK	|Schaltet sich nach Ende des Titels aus und LEDs werden gedimmt
|CMD_SLEEP_AFTER_END_OF_PLAYLIST	|Schaltet sich nach Ende der Playlist aus und LEDs werden gedimmt
|CMD_SLEEP_AFTER_5_TRACKS	|Schaltet sich nach Ende von fünf Titeln aus und LEDs werden gedimmt
|CMD_REPEAT_PLAYLIST	|Aktuelle Playlist wird endlos wiederholt
|CMD_REPEAT_TRACK	|Aktueller Titel wird endlos wiederholt
|CMD_DIMM_LEDS_NIGHTMODE	|Dimmt LEDs in Nachtmodus
|CMD_TOGGLE_WIFI_STATUS	|Schaltet WLAN an/aus
|CMD_TOGGLE_BLUETOOTH_SINK_MODE	|Schaltet den Bluetooth-Modus an/aus, bei dem man zu ESPuino streamen kann (z.B. von einem Handy).
|CMD_TOGGLE_BLUETOOTH_SOURCE_MODE	|Schaltet den Bluetooth-Modus an/aus, bei dem man von ESPuino zu einem externen Lautsprecher oder einem Kopfhörer streamen kann.
|CMD_ENABLE_FTP_SERVER	|Schaltet FTP-Server an (aus geht nicht)
|CMD_PLAYPAUSE	|Wechsel zwischen Pause und Play
|CMD_PREVTRACK	|Vorheriger Titel der aktuellen Playlist
|CMD_NEXTTRACK	|Nächster Titel der aktuellen Playlist
|CMD_FIRSTTRACK	|Sprung zu erstem Titel der aktuellen Playlist
|CMD_LASTTTRACK	|Sprung zu letztem Titel der aktuellen Playlist
|CMD_VOLUMEINIT	|Stellt aktuelle Lautstärke auf Lautstärke nach dem Start ein
|CMD_VOLUMEUP	|Erhöht Lautstärke um eine Einheit
|CMD_VOLUMEDOWN	|Reduziert Lautstärke um eine Einheit
|CMD_MEASUREBATTERY	|Startet Messung der Akkuspannung (wird über Log, Neopixel und MQTT anschließend ausgegeben)
|CMD_SLEEPMODE	|Schaltet ESPuino sofort aus
|CMD_SEEK_FORWARDS	|Springt n Sekunden nach vorne im Titel (Dauer in settings.h konfigurierbar
|CMD_SEEK_BACKWARDS	|Springt n Sekunden nach hinten im Titel (Dauer in settings.h konfigurierbar


# Erstkonfiguration der Jolibox

Nach der Übernahme des Sourcecode von biologist sind in folgenden Dateien einige Konfigurationen anzupassen.

## plattformio.ini

```
13: default_envs = lolin_d32_pro_sdmmc_pe  // Ist als Default voreingestellt
```
## settings.h

```34: #define PORT_EXPANDER_ENABLE``` Zeile aktivieren
```44: #define PLAY_MONO_SPEAKER``` Zeile aktivieren
```49: #define PLAY_LAST_RFID_AFTER_REBOOT``` Zeile aktivieren
```57: #define SAVE_PLAYPOS_BEFORE_SHUTDOWN``` Zeile aktivieren
```58: #define SAVE_PLAYPOS_WHEN_RFID_CHANGE``` Zeile aktivieren
```74: #define RFID_READER_TYPE_MFRC522_SPI``` Zeile auskommentieren
```76: #define RFID_READER_TYPE_PN5180``` Zeile aktivieren

Zeilen 124 bis 152 mit nachfolgenden Zeilen ersetzen

```
    #define BUTTON_0_SHORT    CMD_NEXTTRACK                   // Nächster Titel              	
    #define BUTTON_1_SHORT    CMD_PREVTRACK                   // vorheriger Titel              	
    #define BUTTON_2_SHORT    CMD_PLAYPAUSE                   // Play/Pause             	
    #define BUTTON_3_SHORT    CMD_NOTHING                     // nicht definiert
    #define BUTTON_4_SHORT    CMD_SEEK_BACKWARDS              // um 30 Sek. zurückspulen 
    #define BUTTON_5_SHORT    CMD_SEEK_FORWARDS               // um 30 Sek. vorspulen
    
    #define BUTTON_0_LONG     CMD_LASTTRACK                   // letzter Titel der Playliste
    #define BUTTON_1_LONG     CMD_FIRSTTRACK                  // erster Titel der Playliste
    #define BUTTON_2_LONG     CMD_SLEEPMODE                   // Ausschalten
    #define BUTTON_3_LONG     CMD_SLEEPMODE                   // nicht definiert
    #define BUTTON_4_LONG     CMD_VOLUMEUP                    // Lautstärke erhöhen
    #define BUTTON_5_LONG     CMD_VOLUMEDOWN                  // Lautstärke verringern
 
    #define BUTTON_MULTI_01   CMD_REPEAT_TRACK                // Titel endlos wdhl. 
    #define BUTTON_MULTI_02   CMD_ENABLE_FTP_SERVER           // FTP-Server aktivieren 
    #define BUTTON_MULTI_03   CMD_NOTHING                     // nicht definiert 
    #define BUTTON_MULTI_04   CMD_TOGGLE_BLUETOOTH_SINK_MODE  // Bluetooth-Modus an/aus
    #define BUTTON_MULTI_05   CMD_DIMM_LEDS_NIGHTMODE         // LED auf Nachtmodus 
    #define BUTTON_MULTI_12   CMD_TELL_IP_ADDRESS             // IP-Adresse der Box ansagen
    #define BUTTON_MULTI_13   CMD_NOTHING                     // nicht definiert
    #define BUTTON_MULTI_14   CMD_NOTHING                     // nicht definiert
    #define BUTTON_MULTI_15   CMD_NOTHING                     // nicht definiert
    #define BUTTON_MULTI_23   CMD_NOTHING                	  // nicht definiert
    #define BUTTON_MULTI_24   CMD_SLEEP_TIMER_MOD_30          // Sleeptimer 30 Minuten 
    #define BUTTON_MULTI_25   CMD_NOTHING                	  // nicht definiert
    #define BUTTON_MULTI_34   CMD_NOTHING                     // nicht definiert
    #define BUTTON_MULTI_35   CMD_NOTHING                     // nicht definiert
    #define BUTTON_MULTI_45   CMD_TOGGLE_BLUETOOTH_SOURCE_MODE // Bluetooth-Kopfhörer 
```

```203: constexpr const char accessPointNetworkSSID[] = "Jolibox";``` Von  `ESPuino`  auf `Jolibox` ändern
```207: constexpr const char nameBluetoothSinkDevice[] = "Jolibox";```  Von `ESPuino` auf `Jolibox` ändern
```215: #define NUM_INDICATOR_LEDS 12 ``` Von `24` auf `12` ändern


## settings-lolin_d32_pro_sdmmc_pe.h

``` 95: #define POWER 115```  Wert von `32` auf `115` ändern

``` 97: #define INVERT_POWER```  Zeile aktivieren    

