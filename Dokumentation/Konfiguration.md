# Konfiguration der Joli-Box

- Als Profil muss lolin_d32_pro_sdmmc_pe 19 gewählt werden in Platformio für Wemos Lolin D32 pro 86, D32 pro FePo und auch E32 LiPo 96. 
- In settings.h muss PORT_EXPANDER_ENABLE aktiviert werden. Siehe hier 21.
- In settings-lolin_d32_pro_sdmmc_pe.h muss POWER von 32 auf 115 geändert werden.
- In settings-lolin_d32_pro_sdmmc_pe.h muss INVERT_POWER 15 aktiviert werden.


## settings.h

```34: #define PORT_EXPANDER_ENABLE``` Zeile aktivieren

```57: #define SAVE_PLAYPOS_BEFORE_SHUTDOWN``` Zeile aktivieren

```58: #define SAVE_PLAYPOS_WHEN_RFID_CHANGE``` Zeile aktivieren

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


## settings-lolin_d32_pro_sdmmc_pe.h

``` 95: #define POWER 115```  Wert von `32` auf `115` ändern

``` 97: #define INVERT_POWER```  Zeile aktivieren    

```215: #define NUM_INDICATOR_LEDS 12 ``` Von `24` auf `12` ändern