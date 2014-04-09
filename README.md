

# tmUpdate

#### Bitte geh auf [http://kayuk.de/blog/2014/03/tmupdate-aktualisierung-sose-2014/](http://kayuk.de/blog/2014/03/tmupdate-aktualisierung-sose-2014/) für detaillierte und aktuelle Informationen!!

### Nach dem Download müssen als erstes die Variablen im oberen Teil des Scripts angepasst werden!

Das Script ist (hoffentlich) weitestgehend so kommentiert, dass man die Veränderungen selbst vornehmen kann, ich werde hier dennoch alles einmal erklären:

* **TMUSER** - Hier wird dein Anmeldename eingegeben (Der von deinem Hochschulaccount)


* **STUDIENGANG** - Hier wird das Kürzel deines Studiengangs eingetragen (= der Ordnername in den jeweiligen Dozenten-Ordnern)


* **SEMESTER** - Der Ordner, der bei dir lokal das jeweilige Semester angibt


* **LOCALPATH** -  Der absolute Pfad der zu deinem Telematikordner führt (unter OSX z.B.: /Users/[UserName]/Documents/Telematik ; unter Linux z.B.: /home/[UserName]/Telematik)

* **MOUNTPATH** - Der absolute Pfad zu dem Ordner, in dem das SMB-Share gemountet (eingehangen) werden soll. Dein normaler User sollte Schreibrechte in diesem Verzeichnus haben! (unter OSX z.B.: /Volumes/Aufgabe ; unter Linux z.B.: /home/[UserName]/Aufgabe)

* **SYNCHOME** - Angabe, ob das Script auch deinen Home-Ordner Synchronisieren soll. Hier ist unter Umständen eine weitere Passworteingabe nötig. Wie du dir die Passworteinngabe sparen kannst, kannst du [hier](http://serverfault.com/questions/241588/how-to-automate-ssh-login-with-password) oder [hier](http://kayuk.de/blog/2014/01/script-zum-abgleich-lokaler-daten-mit-telematikserver-der-th-wildau/) nachlesen. (Bei dem Server, auf den der Key geschoben werden muss, handelt es sich um "home.tfh-wildau.de")

* **LOCALHOME** - Pfadangabe, mit welchem Ordner auf deiner Festplatte der Home-Ordner vom Telematikserver synchronisiert werden soll (nicht nötig, falls du bei SYNCHOME='Nein' angegeben hast)


* Danach werden der Reihe nach die Namen der Dozenten eingegeben - Exakt so, wie sie auch auf dem TM-Server heißen (*Achtung: Case Sensitive*). Die Anzahl variiert natürlich je nach Semester..


* Als nächstes müssen **deine lokalen Ordnernamen** bei den Variablen mit der Endung **_LOCAL** eingegeben werden. Die Fächer müssen in *genau der Reihenfolge* wie die Dozenten eingeben werden!! - Sprich: "Da wo der Dozent #0 steht, muss hier auch das Fach dieses Dozenten bei #0 stehen!"

danach ggf. noch ein

	chmod +x tmUpdate
um die Datei ausführbar zu machen und dann kann das Script kann mit `./tmUpdate` gestartet werden.

Es ist empfehlenswert, einen Symlink zur Datei nach /user/local/bin zu legen, damit man das Script von überall ausführen kann.
Das geht so:

	ln -s /PFAD/ZU/DEINEM/tmUpdate /usr/local/bin/tmUpdate
Dann kannst du alle neueren Versionen mit dem File in `/PFAD/ZU/DEINEM/tmUpdate` ersetzen und stets den selben Befehl zum aufrufen benutzen.

## License

(The MIT License)

Copyright © 2014 deg0nz, LLC. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.# This is my README

