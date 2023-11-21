# Benutzerhandbuch
## Einführung
Eine Musikbox auf Basis des Open Source Projekt ESPunino von Torsten Stauder. Die vollständige Projektdokumentation gibt es unter [https://forum.espuino.de/](https://forum.espuino.de).
Für die dort beschriebene Hard- und Softwarelösung wurde ein kindgerechtes, kompaktes Gehäuse für den 3D-Drucker entwickelt und so entstand das Unikat Musikbox `Jolibox` als Geschenk zu ihrem 2. Geburtstag.

## Box mit eigenem WLAN verbinden
Zirkulieren nach dem Einschalten der Box die LED in grün, konnte die Box kein lokales WLAN-Netzwerk erkennen. Die Box eröffnet nun für die Konfiguration des WLAN ein eigenes HilfsWLAN mit der SSID: `JoliBox` ohne Passwort. 
Sobald Rechner/Handy mit diesem WLAN verbunden sind, kann im Browser die Adresse http://192.168.4.1 aufgerufen werden. In der Webseite können nun die Zugangsdaten zum eigenen WLAN eingegeben werden. 
Im Feld `SSID` und `Passwort` die Zugangsdaten zum eigenen WLAN eingeben. Um die Box nicht nur mit der IP-Adresse aufrufen zu können, ist im Feld `Hostname` ein Netzwerkname anzugeben (z.B. JoliBox).

## Weboberfläche
Nachdem die Box mit dem lokalen Netzwerk verbunden ist, kann die Steuerung der Box auch alternativ mit dem Browser erfolgen. 
Die Adresse der Box ist http://jolibox.fritz.box . Sollte dies nicht funktionieren, kann die Weboberfläche der Box auch mit seiner IP-Adresse angesprochen werden. Die aktuelle IP-Adresse kann mit der Tastenkombination `Zurück + Play/Pause` von der Box angesagt werden.

## Abspielen von Inhalten
Die Auswahl der abzuspielenden Titel erfolgt über die mitgelieferten RFID-Karten, oder weitere selbst programmierter RFID-Tags. 
Alternativ kann auch ein Ordner/Titel über die Weboberfläche gestartet werden. Hierzu im Browser im Register RFID den gewünschten Ordner/Titel im auswählen und über einen Rechtsklick den Menüpunkt `Abspielen` auswählen.
Auf der eingebauten SD-Karte sind bei Auslieferung nachfolgende Ordner gespeichert und mit jeweils einer Karte verknüpft. 
Diese Ordner können über die Weboberfläche der Box mit weiteren Titeln ergänzt werden. Auch neue Ordner mit neuen Titeln können jederzeit der Sammlung über die Weboberfläche hinzugefügt werden.
|Musik|Hörspiele|
|-----|---------|
|Bewegungslieder 	(51 Lieder)	|Auf Traumreise mit Erwin der Ente 	(12 Folgen)
|Englische Kinderlieder 	(62 Lieder)	|Benjamin Blümchen 	(32 Folgen)
|Kindergartenlieder 	(48 Lieder)	|Kurzgeschichten 	(8 Folgen)
|Kinderlieder-Mix 	(173 Lieder)	|Leo Lausemaus 	(32 Folgen)
|Lieder für Krabbelkinder 	(153 Lieder)	|Maus-Hörspiel 	(133 Folgen)
|Lieder zum Mitmachen 	(40 Lieder)	|Petronella Apfelmus 	(27 Folgen)
|Rolf Zuckowski 	(150 Lieder)	|Unser Sandmännchen 	(79 Folgen)
|Schlaflieder 	(25 Lieder)		
|Spieluhr 	(66 Lieder)		
|Tierlieder 	(88 Lieder)		
|Unser Sandmännchen 	(97 Lieder)		
|Weihnachtslieder 	(34 Lieder	)	
|Zahnputzlieder 	(12 Lieder)		


##RFID-Tags zuordnen
Die RFID-Tags können über die Weboberfläche der Box zugeordnet werden. Hierzu die Weboberfläche aufrufen und dann ein RFID-Tag auf die Box legen. In der Registerkarte `RFID` wird nun die eindeutige Nummer des RFID-Tag angezeigt. Im oberen Teil der Webseite kann nun ein Ordner oder ein einzelner Titel ausgewählt werden. Anschließend über das DropDown-Menü einen `Abspielmodus` festlegen. Zum speichern der Einstellungen auf die Schaltfläche `Absenden` klicken.
Auf dieser Seite können bei Bedarf auch `Modifikationskarten` zur Funktionssteuerung der Box erstellt werden. Hierzu unten in den Tab `Modifikation` wechseln und im DropDown eine Funktion auswählen.

##Inhalte verwalten
Die Inhalte der Box können über die Weboberfläche oder alternativ über eine FTP-Verbindung verwaltet werden.
###Weboberfläche
- In der Registerkarte RFID kann der Inhalt der eingebauten SD-Karte verändert werden. 
Das Anlegen von neuen Ordnern und das Löschen von Ordner und Daten erfolgt über das Kontextmenü der rechten Maustaste.
- Neue Dateien können über die Schaltfläche `Dateien oder Ordner` ausgewählt, und dann mit der Schaltfläche `Upload` auf die Box in das gewählte Verzeichnis hochgeladen werden. 
Während des Upload sollte die Wiedergabe gestoppt werden, da es sonst zu Tonstörungen kommen kann und die Übertragungsgeschwindigkeit verringert wird.
Es gibt leider noch keine wirklich informative Fortschrittsanzeige, daher Geduld beim Upload.

###FTP
- Für eine FTP Verbindung zur Box muss zuerst der FTP-Server der Box eingeschaltet werden. Dies kann entweder über die Tastenkombination              innerhalb 30 Sekunden nach dem Einschalten Box, oder über die Weboberfläche erfolgen. Der FTP-Server bleibt dann bis zum nächsten Ausschalten der Box aktiv.
- Mit einem geeigneten FTP-Programm (z.B. WinSCP oder FileZilla) kann man sich nun mit der Box verbinden. Die Benutzerkennung und das Passwort lauten `esp32` Die Zugangskennung kann in der Weboberfläche bei Bedarf auch verändert werden.
- Das FTP-Programm zeigt nach der Anmeldung die vollständige Verzeichnisstruktur der eingebauten SD-Karte an und kann diese nach Belieben verändern.
## Akku laden
Im Boden der Box befindet sich die USB-C Ladebuchse. Zum Zeitpunkt der Auslieferung ist in der Ladebuchse ein Adapter für ein magnetisches Ladekabel eingesteckt. Dieser kann bei Bedarf auch herausgezogen werden und ein gewöhnliches USB-C Ladekabel zum Laden benutzt werden. Nach vollständiger Ladung erlöscht die Kontrollleuchte neben der Ladebuchse.
## Box zurücksetzen
Im Fehlerfall kann die Box mit einer Büroklammer in der gekennzeichneten Öffnung kurzzeitig stromlos gemacht werden und wieder in einen definierten Zustand versetzt werden. 
## Tastenbelegung
Die Box kann über einen Druck auf eine beliebige Taste eingeschaltet werden. Über einen langen Druck auf die rote Play/Pause Taste wird die Box ausgeschaltet. Sobald kein Titel mehr abgespielt wird schaltet die Box automatisch nach 10 Minuten ab.
Diverse Tastenkombinationen steuern das Abspielverhalten der Box.

|Taste  Tasten	|Kurzer Tastendruck	|Langer Tastendruck|
----------------|-------------------|------------------|
  |`Leiser`|Titel um 30 Sekunden vorspulen	|Lautstarke senken|
|`Zurück`|Vorheriger Titel in der Liste	|Letzter Titel der Playliste|
|`Play/Pause`|Start / Pause	|Box ausschalten|
|`Vor`|Nächster Titel in der Liste	|Erster Titel der Playliste|
|`Lauter`|Titel um 30 Sekunden zurückspulen 	|Lautstärke erhöhen|
|`Zurück` + `Vor`|Aktueller Titel wird endlos wiederholt|
|`Leiser` + `Vor`|LED auf Nachtmodus dimmen|
|`Play/Pause` + `Lauter`|Sleeptimer 30 Minuten und LED auf Nachtmodus dimmen (An / Aus)|
|`Vor` + `Lauter`|Schaltet den Bluetooth-Modus an/aus, bei dem man zur Box streamen kann (z.B. von einem Handy)|
|`Pay/Pause` + `Vor`|FTP-Server aktivieren zur Titelverwaltung über FTP. 
(Nur 30 Sekunden nach Einschalten zugelassen.)|
|`Zurück` + `Play/Pause`|IP-Adresse der Box ansagen|
|`Zurück` + `Lauter`|Keine Funktion|
|`Leiser` + `Play/Pause`|Keine Funktion|
|`Leiser` + `Zurück`|Keine Funktion|
|`Leiser` + `Lauter`|Keine Funktion (Wiedergabe an Bluetooth-Kopfhörer noch nicht möglich)|

> :information_source:  Diese Liste der Tastenbelegung ist auch an der Bodenplatte der Box angebracht.
