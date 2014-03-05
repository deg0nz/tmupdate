

# tmUpdate
### Script zum Abgleich lokaler Daten mit Telematikserver der TH Wildau


Ich habe mir im Dezember 2013 ein kleines Bashscript geschrieben, das die Daten vom Telematikserver der TH Wildau mit einem lokalen Ordner synchronisiert.
Dies soll der Versuch einer Dokumentation dieses Scripts sein.
Das Script benutzt Rsync zur Synchronisation. Es werden 2 Arrays erstellt um die Dozentenordner Online zu durchlaufen und die Daten dann jeweils mit einem lokalen Ordner abzugleichen.

### Authentifizierung am Telematikserver:

Damit man nich jedes mal sein Passwort beim Durchlauf der Arrays eingeben muss, muss als erstes ein SSH-Key erzeugt werden, falls noch keiner vorhanden ist. Dieser muss dann auf den TM-Server kopiert werden.
Dazu muss der Befehl ssh-keygen benutzt werden: 

	$ ssh-keygen -t rsa -b 2048
	Generating public/private rsa key pair.
	Enter file in which to save the key (/home/username/.ssh/id_rsa): 
	Enter passphrase (empty for no passphrase): 
	Enter same passphrase again: 
	Your identification has been saved in /home/username/.ssh/id_rsa.
	Your public key has been saved in /home/username/.ssh/id_rsa.pub.

Danach muss der erzeugte Key auf den Telematikserver kopiert werden:

	$ ssh-copy-id DEINANMELDENAME@www.tm.th-wildau.de
	DEINANMELDENAME@www.tm.th-wildau.de's password: 

**ssh-copy-id kann auf dem Mac per [Homebrew](http://brew.sh) installieren**

Danach kann ggf. noch gecheckt werden, ob der Key auf auf dem Server liegt. Der müsste dann in ~/.ssh/authorized_keys liegen.

Von diesem Moment an müsstest du dich ohne Passwort am Server anmelden können:
	
	$ ssh DEINANMELDENAME@www.tm.th-wildau.de
	[...Server blabla...]
	DEINANMELDENAME@tms2:~$ exit
	Abgemeldet
	Connection to www.tm.th-wildau.de closed.


Man kann das Ganze auch hier noch einmal nachlesen (en):[Serverfault.com - how to automate ssh login with password](http://serverfault.com/questions/241588/how-to-automate-ssh-login-with-password)

###Verändern des Scripts:

Wenn das alles funktioniert können wir uns ans Verändern des Scripts machen.
Du kannst es ganz normal mit jedem Texteditor öffnen.
Das Script ist weitestgehend so kommentiert, dass man die Veränderungen selbst vornehmen kann, ich werde hier dennoch alles einmal erklären:

USER - Hier wird dein Anmeldename eingegeben (der Selbe, den du zuvor zum ssh login benutzt hast) 
 
STUDIENGANG - Hier wird das Kürzel deines Studiengangs eingetragen (= der Ordnername in den jeweiligen Dozenten-Ordnern)

SEMESTER - Der Ordner, der bei dir lokal das jeweilige Semester angibt 
 
LOCALPATH -  Der absolute Pfad der zu deinem Telematikordner führt (unter OSX z.B.: /Users/[UserName]/Documents/Telematik ; unter Linux z.B.: /home/[UserName]/Telematik) 
 
Danach werden der Reihe nach die Namen der Dozenten eingegeben - genau so, wie sie auch auf dem TM-Server heißen. 
 
Als nächstes müssen die Ordnernamen für die jeweiligen Fächer in <i>genau der Reihenfolge </i>wie die Dozenten eingeben werden - Sprich: "Da wo der Dozent #0 steht, muss nachfolgend auch das Fach dieses Dozenten bei #0 stehen!" 
 
Für andere Semester und andere Dozenten müssen dann ggf. die Variablen verändert werden. Wichtig dabei ist nur, dass die vorgegebene Syntax eingehalten wird. Bei Veränderungen müssen dann natürlich auch die Einträge in den Arrays LOCALDIRS und REMOTEDIRS analog verändert werden. Auch hier gilt wieder: Reihenfolge beachten!! 
 
Ich werde dann auch immer versuchen, für neue Semester auch Updates hier ins Blog hochzuladen.
 
 
Als letztes muss das Script noch ausführbar gemacht werden:
  
	$ chmod +x tmUpdate
  
 
**Wenn es ausführbar ist, kannst du das Script nach /usr/local/bin kopieren um den Befehl direkt ins Terminal eingeben zu können.**
 
###Installation:
	git clone https://github.com/deg0nz/tmupdate.git   

Anleitung mit code ist hier: [tmUpdate auf Kayuk.de](http://kayuk.de/blog/2014/01/script-zum-abgleich-lokaler-daten-mit-telematikserver-der-th-wildau/)


## License

(The MIT License)

Copyright © 2014 deg0nz, LLC. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.# This is my README

