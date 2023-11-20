# Deutsche Übersetzung der README.md aus dem biologist79-Repository](Dokumentation/README.md-biologist.md)

## Forum

Der Autor biologist79 hat ein deutschsprachiges Forum aufgesetzt, welches mit reichlich Doku
  versehen ist. biologist würde es freuen, euch dort zu sehen: <https://forum.espuino.de>. Ihr könnt euch
  dort mit eurem Github-Login einloggen, jedoch auch "normal" anmelden. Dokumentation findet ihr
  insbesondere hier: <https://forum.espuino.de/c/dokumentation/anleitungen/10>.

## News

> :warning: Bis Ende Oktober 2023 hat ESPuino das Framework von ESP32-Arduino1 auf ESP32-Arduino2 umgestellt. Dies brachte viele Verbesserungen mit sich, aber wie sich herausstellte, läuft diese Version aufgrund von Speicherbeschränkungen nicht mehr sicher auf ESP32 ohne PSRAM. Bitte achten Sie also unbedingt darauf, einen ESP32-WROVER zu verwenden!

## ESPuino - was ist das?

Die Grundidee von ESPuino besteht darin, RFID-Tags zur Steuerung eines Audioplayers zu verwenden. Sogar für Kinder ist dieses Konzept einfach: Legen Sie einen mit einem RFID-Tag versehenen Gegenstand (Karte, Spielzeugfigur usw.) auf eine Schachtel und die Musik beginnt mit der Wiedergabe von Inhalten von der SD-Karte oder dem Webradio. Legen Sie einen anderen RFID-Tag darauf und etwas anderes wird abgespielt. So einfach ist das.

Dieses Projekt basiert auf dem beliebten Mikrocontroller [ESP32 by
Espressif](https://www.espressif.com/en/products/hardware/esp32/overview). Warum? Es ist leistungsstark und die sofort einsatzbereite WLAN-Unterstützung ermöglicht weitere Funktionen wie einen integrierten Webserver, Smarthome-Integration über MQTT, Webradio und FTP-Server. Und sogar Bluetooth! Mein Hauptaugenmerk lag jedoch darauf, das Projekt auf eine modulare Basis zu portieren: Die MP3-Dekodierung erfolgt in Software und die digitale Musikausgabe erfolgt über das beliebte [I2S protocol](https://en.wikipedia.org/wiki/I%C2%B2S).
Wir brauchen also einen [DAC](https://en.wikipedia.org/wiki/Digital-to-analog_converter) , um daraus ein analoges Signal zu machen: Ich habe alle meine Tests mit
[MAX98357A](https://learn.adafruit.com/adafruit-max98357-i2s-class-d-mono-amp/pinouts),
[UDA1334](https://www.adafruit.com/product/3678),
[MS6324](https://forum.espuino.de/t/kopfhoererplatine-basierend-auf-ms6324-und-tda1308/1099/) und
[PCM5102a](https://github.com/biologist79/ESPuino/tree/master/PCBs/Headphone%20with%20PCM5102a%20and%20TDA1308)durchgeführt. Allgemeiner Hinweis: ESPuino nutzt die Bibliothek
[ESP32-audioI2S](https://github.com/schreibfaul1/ESP32-audioI2S/); also sollte alles, was mit dieser Bibliothek funktionieren soll, auch mit ESPuino funktionieren (aber vielleicht nicht sofort einsatzbereit). Dies gilt insbesondere für
[ES8388](https://github.com/schreibfaul1/ESP32-audioI2S/blob/master/examples/ESP32_ES8388/ESP32_ES8388.ino).

## Hardware-Setup

Sie könnten mit einem Steckbrett mit Überbrückungsdrähten beginnen, ich empfehle jedoch dringend , sofort mit einer Leiterplatte zu beginnen, die speziell für ESPuino entwickelt wurde. Es sind mehrere verfügbar, aber
[ESPuino-mini 4L (SMD)](https://forum.espuino.de/t/espuino-mini-4layer/1661) kann als die neueste Generation angesehen werden. Darüber hinaus benötigen Sie ein ESP32-Entwicklungsboard wie (oder ein anderes, das Pin-kompatibel ist):

- [D32 pro LiFePO4](https://forum.espuino.de/t/esp32-develboard-d32-pro-lifepo4/1109)
- [E32 LiPo](https://forum.espuino.de/t/esp32-develboard-e32-lipo/1135)
- [Wemos Lolin D32 pro](https://www.wemos.cc/en/latest/d32/d32_pro.html)

> :warning: **Aufgrund von Speicherbeschränkungen ist es mittlerweile zwingend erforderlich, ESP32 mit PSRAM zu verwenden.** Vor diesem Hintergrund müssen Sie sicherstellen, dass Ihr Entwicklungsboard über einen ESP32-WROVER verfügt. Und Sie sollten darauf achten, dass 16 MB Flash-Speicher zur Verfügung stehen (beides gilt für alle oben genannten Entwicklungsboards).

Optional kann eine [headphone-pcb](https://forum.espuino.de/t/kopfhoererplatine-basierend-auf-ms6324-und-tda1308/1099/)
an [ESPuino-mini 4L (SMD)](https://forum.espuino.de/t/espuino-mini-4layer/1661) angeschlossen werden .

Sie können Leiterplatten jedoch auch gerne selbst entwickeln. Beachten Sie jedoch auch hier, dass Ihr ESP32 PSRAM benötigt, um ESPuino ordnungsgemäß auszuführen.

## Erste Schritte

- [Viel mehr Dokumentation gibt es hier](https://forum.espuino.de/c/dokumentation/anleitungen/10).
- Sie müssen [Visual Studio Code](https://code.visualstudio.com/) von Microsoft installieren.
- Installieren Sie das [PlatformIO Plugin](https://platformio.org/install/ide?install=vscode) in [Visual Studio
  Code](https://code.visualstudio.com/) und schauen Sie sich unbedingt die
  [documentation](https://docs.platformio.org/en/latest/integration/ide/pioide.html).
  an . Eine Schritt-für-Schritt-Anleitung finden Sie
  [hier](https://randomnerdtutorials.com/vs-code-platformio-ide-esp32-esp8266-arduino/.)
- Installieren Sie [Git](https://git-scm.com/downloads) und erstellen Sie mit . eine Kopie („Klon“) meines Repositorys auf Ihrem lokalen Computer `git clone https://github.com/biologist79/ESPuino.git`. Mit Git können Sie Ihr lokales Repository ganz einfach auf dem neuesten Stand halten, ohne es kopieren und einfügen zu müssen. Um es auf dem neuesten Stand zu halten, führen Sie Folgendes aus `git pull origin master`. Weitere Informationen 
  [hier](https://stackoverflow.com/questions/1443210/updating-a-local-repository-with-changes-from-a-github-repository)
  und
  [hier](https://forum.espuino.de/t/espuino-in-platformio-anlegen-und-mit-git-aktuell-halten/891).
- (Optional) Installieren Sie [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
  als Plugin (um erweiterte Git-Funktionen in VSCode zu haben).
- Da das Git-Repository nun lokal gespeichert ist, importieren Sie diesen Ordner als Projekt in Platformio.
- Wählen Sie die [gewünschte Umgebung](https://forum.espuino.de/t/projekt-und-profilwechsel-in-visual-studio-code/768) (z.B. lolin_d32_pro_sdmmc_pe).
- Bearbeiten Sie `src/settings.h` ntsprechend Ihren Anforderungen.
- Boardspezifische (`HAL`) Konfigurationsdatei bearbeiten (z. B. `settings-lolin_d32_pro_sdmmc_pe.h` für Lolin D32/D32 pro). Wenn Sie ein Board betreiben, das dort 
  nicht aufgeführt ist: Beginnen Sie mit `settings-custom.h` und ändern Sie es entsprechend Ihren Anforderungen. 
- Schließen Sie Ihr Entwicklungsboard über USB an, klicken Sie auf das Alien-Kopf-Symbol in der linken Seitenleiste, 
  wählen Sie die Projektaufgabe aus, die Ihrem gewünschten HAL entspricht, und führen Sie aus Upload and Monitor. 
  Alle notwendigen Bibliotheken werden automatisch abgerufen und die Kompilierung des Codes beginnt. Danach wird 
  Ihr ESP32 mit der Firmware geflasht. Abhängig von Ihrem Entwicklungsboard kann es erforderlich sein, eine Taste 
  zu drücken, damit ESP32 in den Flash-Modus wechselt (nicht erforderlich für Lolin32, D32 und D32 pro).
- Schauen Sie sich nun die serielle Ausgabe unten im Fenster von Visual Studio Code an. Beim ersten Start können 
  einige Fehlermeldungen erscheinen (im Zusammenhang mit fehlenden Einträgen in NVS). Keine Sorge, das ist einfach 
  normal. Stellen Sie jedoch sicher, dass die SD-Karte erkannt wird, da dies zwingend erforderlich ist!
- Wenn alles gut gelaufen ist, sollte ESPuino beim ersten Start einen Zugangspunkt öffnen und ESPuino bietet ein 
  Captive-Portal an, das auf Ihrem Computer angezeigt wird. Wenn das nicht der Fall ist, verbinden Sie sich mit 
  einem WLAN namens „ESPuino“ und geben Sie es `http://192.168.4.1` in Ihren Webbrowser ein. Geben Sie dort 
  (oder im Captive-Portal) die WLAN-Anmeldeinformationen und den Hostnamen ein. Nachdem Sie die Konfiguration 
  gespeichert haben, starten Sie ESPuino neu.
- Nach dem Neustart versucht ESPuino, sich Ihrem WLAN anzuschließen (mit den zuvor eingegebenen Anmeldeinformationen). 
  War dies erfolgreich, wird in der seriellen Konsole eine IP angezeigt. Über diese IP können Sie mit einem Webbrowser 
  auf die GUI von ESPuino zugreifen; Stellen Sie sicher, dass Sie Javascript zulassen. Wenn die mDNS-Funktion in aktiv ist
  `src/settings.h`, können Sie anstelle der IP den konfigurierten Hostnamen erweitert um .local verwenden. Sie können also 
  `http://espuino.local` für Web-GUI und FTP verwenden.
- Über FTP und Web-GUI können Sie Daten hochladen (erwarten Sie einen Durchsatz von 320 kB/s bis zu 700 kB/s).
- Bei Bedarf muss FTP nach dem Booten aktiviert werden! Vergessen Sie nicht, eine Aktion zuzuweisen 
  `ENABLE_FTP_SERVER` in `settings.h` um sie aktivieren zu können. Neopixel blinkt grün (1x), wenn die Aktivierung 
  erfolgreich war. Es wird nach dem nächsten Neustart automatisch deaktiviert. Bedeutet: Sie müssen es jedes Mal 
  aktivieren, wenn Sie es benötigen (wenn zwischendurch ein Neustart erfolgte). Klingt nervig und ist es vielleicht 
  auch, aber es wird auf diese Weise ausgeführt, um mehr Heap-Speicher (für Webstream) zur Verfügung zu haben, wenn 
  FTP nicht benötigt wird.
- Über den Webbrowser können Sie verschiedene Einstellungen konfigurieren und RFID-Tags mit Aktionen verknüpfen. 
  Wenn die MQTT/FTP-Unterstützung nicht kompiliert wurde, werden ihre Konfigurationsregisterkarten nicht angezeigt.

## SD-card: SPI or SD-MMC (1 bit)-mode?

Es ist zwingend erforderlich, dass die SD-Karte funktioniert. ESPuino startet nicht ohne funktionierende SD-Karte (zumindest sofern dies `NO_SDCARD` aktiviert wurde). Es stehen jedoch zwei Modi für die Schnittstelle zu SD-Karten zur Verfügung: SPI und SDMMC (1 Bit). Beachten Sie, dass SDMMC doppelt so schnell ist wie SPI und einen GPIO weniger benötigt. Im Grunde ist es also ein Kinderspiel.

## Welcher RFID-Leser: RC522 oder PN5180?

RC522 ist sozusagen der ESPuino-Standard. Es ist günstig und funktioniert, allerdings müssen RFID-Tags in der Nähe des Lesegeräts angebracht werden. PN5180 hat stattdessen eine bessere RFID-Reichweite/-Empfindlichkeit und kann auch ISO-15693/iCode SLIX2-Tags, auch bekannt als „Tonies“, lesen (Sie benötigen ein Passwort, um Tonies zu lesen). Sie können ESPuino auch mit einer ISO-14443-Karte aktivieren (nachdem Sie PN5180 mit einer neuen Firmware geflasht haben). Diese Funktion wird LPCD genannt. Nachteile PN5180: Es ist teurer und benötigt mehr GPIOs (6/7 statt 4). Meiner Meinung nach lohnt es sich! Weitere Informationen finden Sie im Abschnitt zur Verkabelung des PN5180 weiter unten. Hinweis: Wenn Sie nur 3,3 V verwenden, achten Sie darauf, diese 3,3 V an die 5 V UND 3,3 V des PN5180 anzuschließen. Klingt seltsam, ist aber notwendig.

## 3.3 V oder 5 V?

ESP32 läuft nur mit 3,3 V. Aber was ist mit der Peripherie?

- 3,3 V! Denn: Wenn Sie den Batteriebetrieb mit LiPo/LiFePO4 planen, stehen keine 5 V zur Verfügung (es sei denn, USB ist angeschlossen oder Sie verwenden einen Aufwärtswandler). Deshalb liegt mein Fokus nur auf 3,3 V. Wenn Sie stattdessen 5 V verwenden möchten, tun Sie dies. Beachten Sie jedoch, dass dies möglicherweise nicht mit dem Batteriemodus kompatibel ist.
- MAX98357A: Bietet mehr Leistung bei 5 V, läuft aber auch bei 3,3 V. Wie auch immer: Es ist immer noch laut genug (meiner Meinung nach).
- Neopixel: Laut Spezifikation benötigt es 5 V, läuft aber auch mit 3,3 V.
- RC522: benötigt 3,3 V (niemals mit 5 V betreiben!)
- PN5180: Stellen Sie bei 3,3 V sicher, dass sowohl die 5-V- als auch die 3,3-V-Pins mit 3,3 V verbunden sind.
- SD-Karte: benötigt 3,3 V, kann aber auch an 5 V angeschlossen werden, wenn ein Spannungsregler vorhanden ist
- Drehgeber: 3,3 V (nicht mit 5 V versorgen! Dem Encoder ist es egal, ob er an 3,3 oder 5 V angeschlossen ist, aber GPIOs von ESP32 schon!)

## WiFi

Für Web-GUI, FTP, MQTT und Webradio ist WLAN zwingend erforderlich. Allerdings kann WLAN vorübergehend oder dauerhaft deaktiviert werden (und ESPuino merkt sich diesen Zustand nach dem nächsten Neustart). Es gibt zwei Möglichkeiten, WLAN (wieder) zu aktivieren/deaktivieren:

- erwenden Sie eine spezielle  [Modifikationskarte]  (https://forum.espuino.de/t/was-sind-modifikationskarten/37) , die über die Web-GUI konfiguriert werden kann.
- Weisen Sie einer Schaltfläche (oder einer Mehrfachschaltfläche) die Aktion `CMD_TOGGLE_WIFI_STATUS` zu . Dadurch wird der aktuelle WLAN-Status umgeschaltet.

## Bluetooth

> :warning: **Aufgrund von Speicherbeschränkungen ist es nicht möglich, Bluetooth parallel zu WLAN zu betreiben.** Das bedeutet, dass Sie kein Webradio über Bluetooth streamen oder auf die Web-GUI zugreifen können, während dieser Modus aktiviert ist.

### ESPuino als A2DP-Senke (Stream zu ESPuino)

ESPuino kann als Bluetooth-Senke (A2DP-Senke) verwendet werden. In diesem Modus können Sie Audio (z. B. von einem mobilen Gerät) über Bluetooth auf Ihren ESPuino streamen. Dieser Modus kann über eine RFID-Modifikationskarte oder durch Zuweisen einer Aktion `CMD_TOGGLE_BLUETOOTH_MODE` zu einer Taste (oder Mehrfachtaste) aktiviert/deaktiviert werden. Wenn Sie dies anwenden, wird ESPuino sofort neu gestartet. Aktiviertes Bluetooth wird durch vier langsam rotierende blau-violette LEDs angezeigt. Nachdem das Bluetooth-Gerät gekoppelt wurde, leuchten die LEDs blau.

### ESPuino als A2DP-Quelle (Stream von ESPuino)

ESPuino kann auch zum Streamen von Audio (A2DP-Quelle) an ein Bluetooth-Headset oder externe Bluetooth-Lautsprecher verwendet werden. Dieser Modus kann über eine RFID-Modifikationskarte oder durch Zuweisen einer Aktion `CMD_TOGGLE_BLUETOOTH_SOURCE_MODE` zu einer Taste (oder Mehrfachtaste) aktiviert/deaktiviert werden. Wenn Sie dies anwenden, wird ESPuino sofort neu gestartet. Aktiviertes Bluetooth wird durch vier langsam rotierende blau-violette LEDs angezeigt. Nachdem das Bluetooth-Headset verbunden ist, leuchten die LEDs blau.

## Port-Expander

Es kann Situationen geben, in denen Ihnen die GPIOs ausgehen. Um diesem Problem zu begegnen, kann ein Port-Expander [PCA9555](https://www.nxp.com/docs/en/data-sheet/PCA9555.pdf) erwendet werden, um die Anzahl der Eingangskanäle zu erweitern (der Ausgangsmodus wird nur in Sonderfällen unterstützt). PCA9555 bietet 2 Ports mit jeweils 8 Kanälen – also insgesamt 16 Kanäle. Um PCA9555 zu aktivieren, müssen Sie aktivieren
`PORT_EXPANDER_ENABLE`. Wie GPIOs in Ihrer entwicklungsboardspezifischen Einstellungsdatei können Sie Nummern zuweisen. Der Bereich ist 100(Port 0 Kanal 0) -> `115` (port 1 channel 7). (Port 1 Kanal 7). Über expanderI2cAddressden Port-Expander kann die I2C-Adresse geändert werden. Dies geschieht `0x20` wenn die Pins `A0`, `A1`, `A2` mit GND verbunden sind.

## Nachdem ESPuino mit Ihrem WLAN verbunden ist

Nachdem Sie ESPuino zu einem Teil Ihres LANs/WLANs gemacht haben, ist die „normale“ Web-GUI unter der von Ihrem Router zugewiesenen IP (oder dem konfigurierten Hostnamen) verfügbar. Mit dieser GUI können Sie:

- Das WLAN konfigurieren
- Verknüpfungen zwischen RFID-Tag, Datei/Verzeichnis/URL und Wiedergabemodus erstellen
- Bindungen zwischen RFID-Tag und einem Modifikationstyp herstellen
- MQTT konfigurieren (falls aktiviert)
- FTP konfigurieren (falls aktiviert)
- Konfigurieren Sie die Anfangslautstärke, die maximale Lautstärke (Lautsprecher/Kopfhörer), die Helligkeit von Neopixel (Nachtmodus/Standard) und die Inaktivitätszeit
- Konfigurieren Sie die Spannungspegel für den Batteriemodus
- Protokolle / Status / aktuelle Spur anzeigen
- Kontrollspieler
- Modifikationen ausführen (z. B. Modifikationskarte)
- Audiodateien hochladen (Webübertragung genannt)
- OTA-Updates durchführen (ESP32 nur mit 16 MB Flash-Speicher)
- NVS-RFID-Zuweisungen importieren + löschen
- ESPuino neu starten + herunterfahren

> :information_source: Wenn Sie einen RFID-Tag am RFID-Lesegerät anbringen, wird die entsprechende ID automatisch an die GUI übertragen. Es ist also nicht erforderlich, solche IDs manuell einzugeben (es sei denn, Sie möchten dies). Der Dateipfad wird automatisch durch Auswahl einer Datei/eines Verzeichnisses im Dateibrowser ausgefüllt.

<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI1.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI2.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI3.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI4.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI5.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI6.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI7.jpg"
width="30%"></img>
<img
src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt-GUI_connection_broken.jpg"
width="30%"></img>
<img src="https://raw.githubusercontent.com/biologist79/ESPuino/master/pictures/Mgmt_GUI_action_ok.jpg" width="30%"></img>

## Interaktion mit ESPuino

### Wiedergabemodi
Es geht nicht einfach nur darum, Musik zu spielen; Es werden verschiedene Wiedergabemodi unterstützt:

- `Single track` => spielt einen Titel einmal ab
- `Single track (loop)` => spielt einen Titel für immer ab
- `Single track of a directory (random). Followed by sleep` => wählt einen einzelnen Titel aus einem Verzeichnis aus, spielt ihn ab und schläft anschließend ein. Neopixel wird gedimmt.
- `Audiobook`=> einzelne Datei oder Playlist/Ordner; Die letzte Wiedergabeposition (Datei und Wiedergabeliste) wird gespeichert (beim Drücken der Pause-Taste oder beim Wechseln zu einem anderen Titel) und beim nächsten Mal wiederverwendet
- `Audiobook (loop)` =>  wie ein Hörbuch, aber in einer Endlosschleife
- `Folder/playlist (alph. sorted)` => spielt alle Titel in alph ab. Einmalig aus einem Ordner bestellen
- `Folder/playlist (random order)` => spielt alle Titel eines Ordners einmal in zufälliger Reihenfolge ab
- `Folder/playlist (alph. sorted)` => spielt alle Titel in alph ab. Bestellen Sie für immer aus einem Ordner
- `Folder/playlist (random order)` => spielt alle Titel in zufälliger Reihenfolge aus einem Ordner für immer ab
- `All tracks of a random subdirectory (sorted alph.)` => spielt alle Titel in zufälliger Reihenfolge aus einem Ordner für immer ab
- `All tracks of a random subdirectory (random order)` => spielt alle Titel in zufälliger Reihenfolge eines zufällig ausgewählten Unterverzeichnisses eines bestimmten Verzeichnisses ab
- `Webradio` => immer nur ein „Track“: spielt einen Webstream ab
- `List (files from SD and/or webstreams) from local .m3u-File` =>  kann eine oder mehrere Dateien/Webradiosender mit lokaler .m3u als Quelldatei sein

### Modifikation von RFID-Tags
Es gibt spezielle RFID-Tags, die Musik nicht von selbst starten, sondern Dinge verändern können. Bei einer zweiten Anwendung wird die vorherige Aktion/Änderung rückgängig gemacht.

Stellen Sie also zunächst sicher, dass Sie die Musik starten, und verwenden Sie dann eine Modifikationskarte, um die gewünschte Modifikation anzuwenden:

- Alle Tasten sperren/entsperren
- Schlafen Sie nach 5/30/60/120 Minuten
- Ruhezustand nach Ende des aktuellen Titels
- Nach Ende der Playlist schlafen
- Schlafen Sie nach fünf Titeln
- Neopixel dimmen
- Wiederhole Titel
- Wiederhole Playlist
- WLAN umschalten (aktivieren/deaktivieren) => Wenn Sie WLAN deaktivieren, während der Webstream aktiv ist, wird ein laufender Webstream sofort gestoppt!
- Bluetooth-Senke umschalten (aktivieren/deaktivieren) => ESPuino wird sofort neu gestartet. In diesem Modus können Sie über BT auf Ihren ESPuino streamen.
- Bluetooth-Quelle umschalten (aktivieren/deaktivieren) => ESPuino wird sofort neu gestartet. In diesem Modus kann Ihr ESPuino über BT an ein externes Gerät streamen.

> :information_source: Alle Schlafmodi dimmen (Neopixel) automatisch, da es abends beim Zubettgehen verwendet werden soll. Naja, zumindest ist das der Hinweis meiner Kinder :-)
>
> :information_source: Der Track- und Playlist-Loop-Modus kann gleichzeitig aktiviert werden, aber solange der Track-Loop nicht deaktiviert ist, ist der Playlist-Loop nicht wirksam

### Neopixel-LEDs (optional)

Zeigt verschiedene Dinge an. Vergessen Sie nicht, die Anzahl der LEDs über zu konfigurieren #define NUM_LEDS. Die meisten Designs verwenden einen Neopixel-Ring, aber auch ein linearer Streifen ist möglich.

> :information_source: Einige Neopixel verwenden eine umgekehrte Adressierung, was zu dem „Problem“ führt, dass alle Effekte gegen den Uhrzeigersinn angezeigt werden. Wenn Sie dieses Verhalten ändern möchten, aktivieren Sie einfach `NEOPIXEL_REVERSE_ROTATION`.

#### Boot

- Beim Booten: jede zweite LED (rotierend orange)
- SD kann nicht gemountet werden: LEDs blinken rot (bleibt für immer, es sei denn, die SD-Karte ist verfügbar oder `SHUTDOWN_IF_SD_BOOT_FAILS` ist aktiv)

#### Status

- **Leerlauf**: Vier LEDs drehen sich langsam (weiß, wenn WLAN verbunden ist; grün, wenn WLAN deaktiviert ist oder ESPuino gerade eine WLAN-Verbindung herstellt)
- **Bluetooth**: vier langsam rotierende LEDs in blauer Farbe
- **Fehler**: Alle LEDs blinken rot (1x), wenn eine Aktion nicht akzeptiert wurde
- **OK**: Alle LEDs blinken grün (1x), wenn eine Aktion akzeptiert wurde
- **Ausschalten**: Roter Kreis, der wächst, bis die lange Druckzeit erreicht ist
- **Tasten gesperrt**: Titel-Fortschritts-LEDs rot gefärbt

#### Wiedergabe

- **Warten**: violett; vier schnell rotierende LEDs beim Erstellen einer Playlist. Die Dauer hängt von der Anzahl der Dateien in Ihrer Playlist ab.
- **Titel-Fortschritt**: Regenbogen; Anzahl der LEDs im Verhältnis zum Spielfortschritt
- **Playlist-Fortschritt**: blau; erscheint im Playlist-Modus nur kurz mit Beginn jedes neuen Titels; Anzahl der LEDs im Verhältnis zum Fortschritt
- **Webstream**: zwei langsam rotierende LEDs, die im Verlauf des Streams ihre Farben regenbogenartig ändern
- **Laurstärke**: grün => rot-Farbverlauf; Anzahl der LEDs im Verhältnis zur aktuellen bis zur maximalen Lautstärke
- **Paused**: Track-Fortschritts-LEDs färben sich orange
- **Rücklauf**: Wenn die Einzelspurschleife aktiviert ist, wird beim Neustart des angegebenen Titels ein LED-Rücklauf durchgeführt

#### Batteriestatus (optional)

- **Unterspannung**: blinkt dreimal rot, wenn die Batteriespannung zu niedrig ist. Dieser Spannungspegel kann über die GUI konfiguriert werden.
- Durch kurzes Drücken der Taste des Drehgebers wird die Batteriespannung über Neopixel angezeigt. Ober- und Unterspannungsabschaltungen können per GUI eingestellt werden. Wenn beispielsweise die Unterspannung auf 3,2 V und die Oberspannung auf 4,2 V eingestellt ist, zeigen 50 % der LEDs eine Spannung von 3,7 V an.

### Tasten

> :warning: In diesem Abschnitt wird mein Standarddesign beschrieben: 3 Tasten + Drehgeber. Fühlen Sie sich frei, die Anzahl der Schaltflächen (bis zu 5) und Schaltflächenaktionen entsprechend Ihren Anforderungen und  `settings.h` Ihrer entwicklungsboardspezifischen Konfigurationsdatei (z. B. `settings-lolin32.h`). zu ändern. Es können maximal fünf Tasten + Drehgeber aktiviert werden. Die Mindestdauer für langes Drücken (zur Unterscheidung vom kurzen Drücken) in ms wird durch definiert `intervalToLongPress`. Alle verfügbaren Aktionen sind in aufgeführt `src/values.h`. Wenn Sie GPIO >= 34 verwenden, stellen Sie sicher, dass Sie einen externen Pullup-Widerstand (10 k) hinzufügen.

- **Vorherige (kurz):** vorheriger Titel / Anfang des ersten Titels, wenn gedrückt, während der erste Titel abgespielt wird
- **Vorheriger (lang):** erster Titel der Playlist
- **Nächster (kurz):** nächster Titel der Playlist
- **Nächster (lang):** letzter Titel der Playlist
- **Pause/Play (kurz o. lang):** Pause/Play
- **Drehgeber (drehen):** Lautstärke +/-
- **Drehgeber (lang drücken):** ausschalten (nur wenn an)
- **Drehgeber (kurz drücken):** einschalten (im ausgeschalteten Zustand)
- **Drehgeber (kurz drücken):** Batteriespannung über Neopixel anzeigen (wenn eingeschaltet und
  `MEASURE_BATTERY_VOLTAGE` ist aktiv)
- **Vorherige und Nächster:** WLAN aktivieren/deaktivieren

### Musikwiedergabe

- Die Musikwiedergabe beginnt sofort, nachdem ein gültiger RFID-Tag angebracht wurde (sofern dieser ESPuino bekannt ist).
- Wenn `PLAY_LAST_RFID_AFTER_REBOOT` aktiviert, merkt sich ESPuino die zuletzt angewendete RFID => Musik-Autoplay.
- Soll ein Ordner abgespielt werden, der viele MP3s enthält, kann die Erstellung der Playlist einige Sekunden dauern.
- Der Name einer Datei einschließlich Pfad darf 255 Zeichen nicht überschreiten.
- Während die Playlist generiert wird, zeigt Neopixel den Warten-Modus an.
- Nachdem der letzte Titel abgespielt wurde, zeigt Neopixel den Leerlauf-Modus an.

### Hörbuchmodus

Dieser Modus unterscheidet sich von den anderen, da die letzte Wiedergabeposition gespeichert wird, wenn...
- Der nächste Titel beginnt.
- erster/vorheriger/letzter Titel, der per Taste angefordert wird.
- Pause wurde gedrückt.
- Der Titel beendet ist.
- Die Wiedergabeliste ist zu Ende (die Position wird auf den ersten Titel und die Dateiposition 0 zurückgesetzt).
- Standardmäßig wird die letzte Wiedergabeposition beim Anbringen eines neuen RFID-Tags nicht gespeichert. Sie können dies aber mit `SAVE_PLAYPOS_WHEN_RFID_CHANGE` aktivieren.
- Standardmäßig wird die letzte Wiedergabeposition beim Herunterfahren nicht gespeichert. Sie können dies mit `SAVE_PLAYPOS_BEFORE_SHUTDOWN` aktivieren .

### FTP (optional)

- FTP muss nach dem Booten aktiviert werden! Vergessen Sie nicht, eine Aktion `ENABLE_FTP_SERVER` in `settings.h` zuzuweisen oder eine Modifikationskarte zu verwenden, um es zu aktivieren!
  Neopixel blinkt grün (1x), wenn die Aktivierung erfolgreich war. Es wird nach dem nächsten Neustart automatisch deaktiviert. Bedeutet: Sie müssen es jedes Mal aktivieren, wenn Sie es benötigen (wenn zwischendurch ein Neustart erfolgte). Klingt nervig und ist es vielleicht auch, aber es läuft auf diese Weise, um Heap-Speicher zu sparen, wenn FTP nicht benötigt wird.
- Warum FTP? Nun ja: Um nicht ständig die SD-Karte freizulegen oder ESPuino für das Hinzufügen neuer Musik zu zerlegen, ist es möglich, Musik per FTP auf die SD-Karte zu übertragen. Eine andere Möglichkeit besteht darin, dies über eine Web-GUI (Webtransfer) zu tun.
- DStandardbenutzer und Passwort sind auf `esp32` / `esp32` eingestellt, können aber über die GUI geändert werden.
- Gesichertes FTP ist nicht verfügbar. Stellen Sie daher sicher, dass SSL/TLS deaktiviert ist.
- Software: Meine Empfehlung ist [Filezilla](https://filezilla-project.org/), da es kostenlos und für mehrere Plattformen verfügbar ist.
- Bitte beachten Sie: Bei paralleler Musikwiedergabe sinkt diese Rate drastisch! Stoppen Sie daher besser die Wiedergabe, wenn Sie Dateiübertragungen durchführen.

### Energie sparen

Wie bereits im Abschnitt „Modifikationen“ beschrieben, stehen verschiedene Schlafmodi zur Verfügung. Zusätzlich wird der ESP32-Controller nach 10 Minuten Inaktivität in den Tiefschlaf versetzt (konfigurierbar über maxInactivityTime), es sei denn, ESPuino spielt keine Musik ab, hat einen angeschlossenen FTP-Client und keine Eingaben über Tasten. Bei jeder Tastenbetätigung wird der Zähler zurückgesetzt.

### Backups

Da alle Zuordnungen zwischen RFID-IDs und Aktionen (Wiedergabemodus, abzuspielende Datei usw.) im NVS des ESP gespeichert werden, besteht das Problem darin, dass alles verloren geht, wenn das ESP kaputt ist. Hier ist ein Backup also praktisch. Jedes Mal, wenn Sie über die GUI eine Zuordnung zwischen einem RFID-Tag und einer Aktion ändern oder eine neue hinzufügen, wird eine Sicherungsdatei auf der SD-Karte gespeichert. Der Name der Datei kann über `backupFile` geändert werden. Also besser nicht löschen! Mithilfe der Web-GUI können Sie das Upload-Formular verwenden, um eine solche Datei zu importieren.

### Smarthome/MQTT (optional)

Alles, was über RFID-Tags und -Tasten gesteuert werden kann, kann auch über MQTT gesteuert werden (mit Ausnahme des Umschaltens des WLAN-Status, da dies keinen Sinn ergibt). Alle manuellen Interaktionen (Tasten, RFID-Tags) werden auch parallel an MQTT gesendet, sodass alles immer synchron ist (es sei denn, die WLAN-/MQTT-Verbindung ist unterbrochen).

Um es nutzen zu können, muss ein MQTT-Broker ausgeführt werden. [Mosquitto](https://mosquitto.org/) zum Beispiel. Nach der Verbindung abonniert ESPuino alle Befehlsthemen. Statusthemen werden verwendet, um Status an den Broker zu senden, um andere zu informieren, wenn sich etwas geändert hat (Änderung der Lautstärke, neue Playlist, neuer Titel, was auch immer).

In meinem Heim-Setup verwende ich [openHAB](https://www.openhab.org/) um MQTT in einer schönen GUI zu „kapseln“, auf die über App + Web zugegriffen werden kann. Weitere Informationen (und Bilder) finden Sie im [openHAB directory](https://github.com/biologist79/ESPuino/tree/master/openHAB).

> :information_source: Ich habe eine Beispielkonfiguration für openHAB2  [beschrieben](https://github.com/biologist79/ESPuino/tree/master/openHAB). Mittlerweile ist jedoch openHAB3 verfügbar und alle beschriebenen Dinge können auch per GUI konfiguriert werden. Beachten Sie, dass openHAB ziemlich komplex ist und Sie einige Zeit aufwenden müssen, um sich damit vertraut zu machen.

#### MQTT topics

Nutzen Sie gerne Ihre eigenen Smarthome-Umgebungen (anstelle von openHAB). Die verfügbaren MQTT-Themen werden wie folgt beschrieben.

> :information_source: Wenn Sie einen Befehl an ESPuino senden möchten, müssen Sie ein cmnd-topic verwenden, während ESPuino seine Zustände über state-topics zurückschickt. Wenn Sie also die Lautstärke auf 8 ändern möchten, müssen Sie diese Nummer über topic-variable senden `topicLoudnessCmnd`. Unmittelbar danach sendet ESPuino eine Bestätigung dieses Befehls mit `topicLoudnessState`. Um MQTT in die Hände zu bekommen, empfehle ich dieses [als](https://www.hivemq.com/mqtt-essentials/) Einführung (deckt mehr ab, als Sie für ESPuino benötigen).

| topic-variable          | range           | Bedeutung                                                                                                                                                |
| ----------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| topicSleepCmnd          | 0 or OFF        | Schalten Sie ESPuino sofort aus                                                                                                                          |
| topicSleepState         | ON or OFF       | Sendet den letzten Status von ESPuino                                                                                                                             |
| topicRfidCmnd           | 12 digits       | Legen Sie die Anzahl der RFID-Tags fest, die ein RFID-Tag „emuliert“ (z. B. 123789456089)                                                                              |
| topicRfidState          | 12 digits       | ID des aktuellen RFID-Tags (falls keine Modifikationskarte)                                                                                                    |
| topicTrackState         | String          | Sendet die aktuelle Titelnummer, die Gesamtzahl der Titel und den vollständigen Pfad des aktuellen Titels. ZB „(2/10) /mp3/kinderlieder/Ri ra rutsch.mp3“                 |
| topicTrackControlCmnd   | 1 -> 7          | `1`=stop; `2`=unused!; `3`=play/pause; `4`=next; `5`=prev; `6`=first; `7`=last                                                                         |
| topicCoverChangedState  |                 | Zeigt an, dass sich das Titelbild möglicherweise geändert hat. Aus Leistungsgründen sollte die Anwendung das Bild nur laden, wenn es für den Benutzer sichtbar ist |
| topicLoudnessCmnd       | 0 -> 21         | Lautstärke einstellen (abhängig von minVolume / maxVolume)                                                                                                        |
| topicLoudnessState      | 0 -> 21         | Sendet die Lautstärke (abhängig von minVolume / maxVolume).                                                                                                       |
| topicSleepTimerCmnd     | EOP             | Nach Ende der Wiedergabeliste ausschalten                                                                                                                        |
|                         | EOT             | Ausschalten nach Titelende                                                                                                                           |
|                         | EO5T            | Ausschalten nach fünf Titeln                                                                                                                     |
|                         | 1 -> 2^32       | Dauer in Minuten bis zum Ausschalten                                                                                                                       |
|                         | 0               | Timer deaktivieren (falls aktiv)                                                                                                                           |
| topicSleepTimerState    | various         | Sendet aktiven Timer (`EOP`, `EOT`, `EO5T`, `0`, ...)                                                                                                    |
| topicState              | Online, Offline | `Online` beim Einschalten, `Offline` beim Ausschalten                                                                                                 |
| topicCurrentIPv4IP      | IPv4-string     | Sendet die IP-Adresse von ESPuino (z. B. 192.168.2.78)                                                                                                       |
| topicLockControlsCmnd   | ON, OFF         | Legen Sie fest, ob Bedienelemente (Tasten, Drehgeber) gesperrt werden sollen                                                                                             |
| topicLockControlsState  | ON, OFF         | Wird gesendet, wenn Bedienelemente (Tasten, Drehgeber) gesperrt sind                                                                                                 |
| topicPlaymodeState      | 0 - 10          | Sendet den aktuellen Wiedergabemodus (Einzeltitel, Hörbuch...; siehe  [Widergabemodus](#playback-modes))                                                        |
| topicRepeatModeCmnd     | 0 - 3           | Wiederholungsmodus einstellen: `0`=no; `1`=track; `2`=playlist; `3`=both                                                                                             |
| topicRepeatModeState    | 0 - 3           | Sendet den Wiederholungsmodus                                                                                                                                      |
| topicLedBrightnessCmnd  | 0 - 255         | Stellen Sie die Helligkeit von Neopixel ein                                                                                                                             |
| topicLedBrightnessState | 0 - 255         | Sendet Helligkeit von Neopixel                                                                                                                           |
| topicBatteryVoltage     | float           | Spannung (z. B. 3,81)                                                                                                                                    |
| topicBatterySOC         | float           | Aktuelle Batterieladung in Prozent (z. B. 83,0)                                                                                                          |
| topicWiFiRssiState      | int             | Numerische WLAN-Signalstärke (dBm)                                                                                                                     |
| topicSRevisionState     | String          | Software-Revision                                                                                                                                      |

## Entwicklung und Beiträge

### Codeformatierung

Es wird die automatische Codeformatierung über  `clang-format` verwendet. Die Konfiguration/Regeln finden Sie in `.clang-format`. Wenn Sie Visual Studio Code als IDE verwenden, ist die Unterstützung hierfür automatisch über die C++-Erweiterung verfügbar.

Verwenden Sie beim Bearbeiten des Quellcodes Strg+Umschalt+I, um die automatische Formatierung für die Datei auszuführen, oder Strg+K Strg+F für den ausgewählten Code.

Weitere Optionen über die automatische Formatierung beim Speichern oder Bearbeiten der Datei finden Sie in der [Dokumentation](https://code.visualstudio.com/docs/cpp/cpp-ide#_code-formatting).

Das CI (über „GitHub Actions“) prüft Änderungen beim Pushen, um den Quellcode sauber zu halten und den Entwicklern und Betreuern Feedback zu geben.

Um die Ausgabe `git blame` trotz der massiven Änderungen bei der Einführung neuer Formatierungsregeln sauber zu halten, haben wir eine `.git-blame-ignore-revs` Liste der zu ignorierenden Commits. In VSCode sollte dies automatisch verwendet werden, wenn Sie die Erweiterung „GitLens“ verwenden. Stellen Sie andernfalls sicher, dass Sie das Konfigurationsfragment für Git anwenden, indem Sie es  `git config --local include.path ../.gitconfig` einmal in Ihrem lokalen Klon ausführen.