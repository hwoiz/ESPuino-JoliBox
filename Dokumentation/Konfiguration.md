# Konfiguration der Joli-Box

- Als Profil muss lolin_d32_pro_sdmmc_pe 19 gewählt werden in Platformio für Wemos Lolin D32 pro 86, D32 pro FePo und auch E32 LiPo 96. 
- In settings.h muss PORT_EXPANDER_ENABLE aktiviert werden. Siehe hier 21.
- In settings-lolin_d32_pro_sdmmc_pe.h muss POWER von 32 auf 115 geändert werden.
- In settings-lolin_d32_pro_sdmmc_pe.h muss INVERT_POWER 15 aktiviert werden.


## settings.h
```34: #define PORT_EXPANDER_ENABLE``` Zeile aktivieren    <br>
```57: #define SAVE_PLAYPOS_BEFORE_SHUTDOWN``` Zeile aktivieren <br>
```58: #define SAVE_PLAYPOS_WHEN_RFID_CHANGE``` Zeile aktivieren <br>
```203: constexpr const char accessPointNetworkSSID[] = "Jolibox";``` Von ESPuino auf Jolibox ändern <br>
```124: #define BUTTON_0_SHORT    CMD_NEXTTRACK``` <br>
```125: #define BUTTON_1_SHORT    CMD_PREVTRACK``` <br>
```126: #define BUTTON_2_SHORT    CMD_PLAYPAUSE``` <br>
```127: #define BUTTON_3_SHORT    CMD_MEASUREBATTERY``` <br>
```128: #define BUTTON_4_SHORT    CMD_SEEK_BACKWARDS``` <br>
```129: #define BUTTON_5_SHORT    CMD_SEEK_FORWARDS``` <br>

```131: #define BUTTON_0_LONG     CMD_LASTTRACK``` <br>
```132: #define BUTTON_1_LONG     CMD_FIRSTTRACK``` <br>
```133: #define BUTTON_2_LONG     CMD_PLAYPAUSE``` <br>
```134: #define BUTTON_3_LONG     CMD_SLEEPMODE``` <br>
```135: #define BUTTON_4_LONG     CMD_VOLUMEUP``` <br>
```136: #define BUTTON_5_LONG     CMD_VOLUMEDOWN``` <br>

```138: #define BUTTON_MULTI_01   CMD_NOTHING ```  //CMD_TOGGLE_WIFI_STATUS (disabled now to prevent children from unwanted WiFi-disable) <br>
```139: #define BUTTON_MULTI_02   CMD_ENABLE_FTP_SERVER``` <br>
```140: #define BUTTON_MULTI_03   CMD_NOTHING``` <br>
```141: #define BUTTON_MULTI_04   CMD_NOTHING``` <br>
```142: #define BUTTON_MULTI_05   CMD_NOTHING``` <br>
```143: #define BUTTON_MULTI_12   CMD_TELL_IP_ADDRESS``` <br>
```144: #define BUTTON_MULTI_13   CMD_NOTHING``` <br>
```145: #define BUTTON_MULTI_14   CMD_NOTHING``` <br>
```146: #define BUTTON_MULTI_15   CMD_NOTHING``` <br>
```147: #define BUTTON_MULTI_23   CMD_NOTHING``` <br>
```148: #define BUTTON_MULTI_24   CMD_NOTHING``` <br>
```149: #define BUTTON_MULTI_25   CMD_NOTHING``` <br>
```150: #define BUTTON_MULTI_34   CMD_NOTHING``` <br>
```151: #define BUTTON_MULTI_35   CMD_NOTHING``` <br>
```152: #define BUTTON_MULTI_45   CMD_NOTHING``` <br>
```207: constexpr const char nameBluetoothSinkDevice[] = "Jolibox";```  Von ESPuino auf Jolibox ändern

## settings-lolin_d32_pro_sdmmc_pe.h
``` 95: #define POWER   115```  Wert von 32 auf 115 ändern
``` 97: #define INVERT_POWER```  Zeile aktivieren    
```215: #define NUM_INDICATOR_LEDS	12 ```Von 24 auf 12 ändern