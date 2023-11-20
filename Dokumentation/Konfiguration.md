# Konfiguration der Joli-Box

- Als Profil muss lolin_d32_pro_sdmmc_pe 19 gewählt werden in Platformio für Wemos Lolin D32 pro 86, D32 pro FePo und auch E32 LiPo 96. 
- In settings.h muss PORT_EXPANDER_ENABLE aktiviert werden. Siehe hier 21.
- In settings-lolin_d32_pro_sdmmc_pe.h muss POWER von 32 auf 115 geändert werden.
- In settings-lolin_d32_pro_sdmmc_pe.h muss INVERT_POWER 15 aktiviert werden.


## settings.h

```34: #define PORT_EXPANDER_ENABLE``` Zeile aktivieren

```57: #define SAVE_PLAYPOS_BEFORE_SHUTDOWN``` Zeile aktivieren

```58: #define SAVE_PLAYPOS_WHEN_RFID_CHANGE``` Zeile aktivieren

```124: #define BUTTON_0_SHORT    CMD_NEXTTRACK```

```125: #define BUTTON_1_SHORT    CMD_PREVTRACK```

```126: #define BUTTON_2_SHORT    CMD_PLAYPAUSE```

```127: #define BUTTON_3_SHORT    CMD_MEASUREBATTERY```

```128: #define BUTTON_4_SHORT    CMD_SEEK_BACKWARDS```

```129: #define BUTTON_5_SHORT    CMD_SEEK_FORWARDS```

```131: #define BUTTON_0_LONG     CMD_LASTTRACK```

```132: #define BUTTON_1_LONG     CMD_FIRSTTRACK```

```133: #define BUTTON_2_LONG     CMD_PLAYPAUSE```

```134: #define BUTTON_3_LONG     CMD_SLEEPMODE```

```135: #define BUTTON_4_LONG     CMD_VOLUMEUP```

```136: #define BUTTON_5_LONG     CMD_VOLUMEDOWN```


```138: #define BUTTON_MULTI_01   CMD_NOTHING ```  //CMD_TOGGLE_WIFI_STATUS (disabled now to prevent children from unwanted WiFi-disable)

```139: #define BUTTON_MULTI_02   CMD_ENABLE_FTP_SERVER```

```140: #define BUTTON_MULTI_03   CMD_NOTHING``` 

```141: #define BUTTON_MULTI_04   CMD_NOTHING```

```142: #define BUTTON_MULTI_05   CMD_NOTHING```

```143: #define BUTTON_MULTI_12   CMD_TELL_IP_ADDRESS```

```144: #define BUTTON_MULTI_13   CMD_NOTHING```

```145: #define BUTTON_MULTI_14   CMD_NOTHING```

```146: #define BUTTON_MULTI_15   CMD_NOTHING```

```147: #define BUTTON_MULTI_23   CMD_NOTHING```

```148: #define BUTTON_MULTI_24   CMD_NOTHING```

```149: #define BUTTON_MULTI_25   CMD_NOTHING```

```150: #define BUTTON_MULTI_34   CMD_NOTHING```

```151: #define BUTTON_MULTI_35   CMD_NOTHING```

```152: #define BUTTON_MULTI_45   CMD_NOTHING```

```203: constexpr const char accessPointNetworkSSID[] = "Jolibox";``` Von  `ESPuino`  auf `Jolibox` ändern

```207: constexpr const char nameBluetoothSinkDevice[] = "Jolibox";```  Von `ESPuino` auf `Jolibox` ändern


## settings-lolin_d32_pro_sdmmc_pe.h

``` 95: #define POWER   115```  Wert von `32` auf `115` ändern

``` 97: #define INVERT_POWER```  Zeile aktivieren    

```215: #define NUM_INDICATOR_LEDS	12 ``` Von `24` auf `12` ändern