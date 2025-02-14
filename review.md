# Review-Prozess / How-to Pull-Request

## Ziel

Ziel unseres Review-Prozesses ist hauptsächlich die Sicherstellung der Einhaltung unserer [Standards](./standards.md). Es ist nicht unser Anspruch, jedes neu hinzugekommene Lied inhaltlich (auf musikalische Korrektheit des Satzes) zu prüfen. Das liegt daran, dass die Quellenlage häufig unklar ist und das Kontrollieren z.B. nach Tonaufnahmen sehr zeitaufwändig ist. Das soll explizit nicht heißen, dass keine Kontrolle erfolgen darf, sie ist lediglich nur nicht der Standard.

## Überblick

Im Folgenden findest du eine Kurzschrittfolge über den Reviewprozess und eine ausführliche Schrittfolge für Einsteiger\*innen.

## Kurz und knapp: Schritte zum Beitragen neuer Lieder

1. Neue Lieder setzen und auf einem neuen Branch beitragen
2. Review-Schritte (siehe unten) selbst durchgehen
3. Pull-Request für den Merge vom neuen Branch auf main anlegen
4. In der Signal-Gruppe Bescheid geben, damit jemand das Pull-Request reviewed

## Kurz und knapp: Review-Schritte

1. Zu mergenden Branch auschecken
2. Läuft die Kompilierung ohne Fehler durch?
3. Sind die [Standards](./standards.md) befolgt worden? Stimmen die Autor\*innenangaben?
   1. Falls ja: Pull-Request genehmigen und mergen
   2. Falls nein: Korrekturen anfragen

## Ausführliche Anleitung: neue Lieder einfügen

*Dies ist eine Einführung in unser Review-System. Damit das ganze möglichst praxisnah erklärt wird, machen wir ein Beispiel. Nehmen wir an, du hast das Lied "Sturm und Drang" gesetzt und willst es dem Liederpool hinzufügen. In dieser Anleitung gehen wir jetzt alle Schritte durch, die es braucht, bis das Lied vollständig im Liederpool angekommen ist. Bei Fragen oder Irritationen meld dich gerne bei uns!*

*Bevor du dich mit Pull Requests beschäftigst, solltest du [Lilypond eingerichtet](einrichtung_lilypond.md), [Git eingerichtet](GITME.md) und wichtige Infos zum [Liederpool](liederpool.md) gelesen haben.*

*Anmerkung vorweg: Alle beschriebenen Schritte funktionieren in jeder Git-GUI etwas anders. Das ist nervig, aber leider nicht zu ändern. Deswegen orientiere dich an den zugrundeliegenden Git-Befehlen und suche im Zweifel in der Doku deiner GUI, wie man den Git-Befehl in deinem Programm ausführt. Eine andere Möglichkeit ist, das du aus deinem Programm eine Konsole (oder Git Bash) öffnest und es darüber machst.*

### 1. Schritt: Ein neuer Branch

Du hast das Lied "Sturm und Drang" gemäß unseren [Standards](standards.md) gesetzt. Jetzt soll das Lied in einen neuen Branch gepusht werden.

1. Erstell einen neuen Branch im Submodul `lilypond-song-includes`. Der Git-Befehl dafür lautet `git branch branchname`, wobei du `branchname` mit dem Namen des neuen Branches ersetzen musst. In unserem Falle zum Beispiel `sturmunddrang`. Der Name ist nicht unglaublich wichtig, aber er sollte der Übersicht halber etwas mit deinen geplanten Änderungen zu tun haben und nicht zu allgemein sein (also nicht: "neues Lied").

2. Check in diesen Branch aus, das heißt: Wechsle den Branch vom main-Branch in den neu erstellten Branch. Falls du dich nicht im `main`-Branch befindest, checke unbedingt vorher in den `main`-Branch aus. Der Git-Befehl dafür lautet `git checkout sturmunddrang`.

3. Committe deine Änderungen, in unserem Beispiel also das neue Lied. Der Git-Befehl dafür lautet `git -m commit "neues Lied: Sturm und Drang"`. Bitte fass in einem Commit immer nur zusammenhängende Änderungen zusammen. Wenn du beispielsweise Korrekturen in den Docs und in den Liedbausteinen vornimmst, mach dafür zwei Commits. Außerdem häng eine Commit-Message (dafür steht das `-m`) an, in der du kurz beschreibst, was du geändert hast.
   Jetzt sind deine Änderungen lokal in einen neuen Branch commitet.

4. Pushe den neuen Branch. Das funktioniert mit dem Git-Befehl `git push`. **Wichtig:** Du musst dich dafür in deinem neuen Branch befinden.
   Jetzt befinden sich deine Änderungen remote in einem neuen Branch namens `sturmunddrang`.

### 2. Schritt: Der Pull-Request

Unser Liederpool befindet sich im `main`-Branch. Aus diesem Grund ist dieser Branch geschützt, man kann also nicht einfach auf ihn pushen. Dann wäre ein Review nämlich nicht systematisch möglich. Stattdessen findet nun folgender Prozess statt: Eine Änderung wird in einen eigenen Branch gepusht, der Branch wird überprüft (reviewed) und dann in `main` integriert. Dafür sind nun folgende Schritte notwendig:

1. Erstelle einen neuen Pull-Request. Dafür musst du auf unserem Git-Server auf die Seite [Pull Requests](https://git.zahlenlabyrinth.de/boernel/lilypond-song-includes/pulls) gehen. Dann klickst du auf den prominenten Button `Neuer Pull-Request`.

2. Wähle den Branch, von dem gepullt wird. Das Ziel ist dabei immer `boernel:main`. Bei pullen von solltest du deinen Branch auswählen, in unserem Beispiel also `boernel:sturmunddrang`.

3. Jetzt siehst du alle Commits, die sich in deinem Branch befinden. Außerdem siehst du eine Übersicht mit allen exakten getätigten Änderungen. Überprüfe noch einmal, ob alles dabei ist, dann klick im nächsten Schritt auf `Neuer Pull-Request`.

4. Jetzt kannst du dem Pull-Request noch Kommentare hinzufügen. Bearbeite, wenn gewünscht, den Titel und setze Haken im Kommentarfeld. Bei der Liste handelt es sich um eine Vorlage, die standardmäßig immer dabei ist. Bitte überprüfe alle Punkte. Im Idealfall sind alle Punkte erfüllt, dann kannst du sie abhaken. Wenn du dir nicht sicher bist, lass sie lieber offen. Einen Haken setzt du, indem du ein `x` in die Klammern anstatt des Leerzeichens setzt. Für unser Beispiel sähe es beispielsweise so aus:

   ```
   Sind alle Punkte erfüllt?

   - [x] Das Lied läuft mit Lilypond durch und produziert keine Fehler
   - [x] Lied wurde mindestens einmal komplett durchgespielt und durchgesungen
   - [ ] Quellen sind angegeben
   - [x] Standards wurden eingehalten
   ```

   Wenn du außerdem Hinweise oder Bemerkungen zu deinem Pull-Request hast, kannst du diese hier ebenfalls unterbringen.

5. Zum Schluss musst du nur noch auf `Pull-Request erstellen klicken`, dann bist du fertig. Wenn dein PR (=Pull-Request) bereit für den Review ist, dann kannst du im Menü rechts unter dem Punkt `Reviewer` das Team "Setzer" auswählen, dann werden alle benachrichtigt, die mit dem Liederpool arbeiten, dass es einenn zu reviewenden PR gibt. Außerdem kannst du auch in die Signal-Gruppe schreiben.

### 3. Schritt: Der Review

Nun kann es sein, dass es Änderungswünsche an deinem Commit gibt, weil es doch noch zusätzliche Informationen gibt, die darin fehlen, oder weil jemand einen Tippfehler gefunden hat. Das siehst du übrigens im Bereich deines Pull-Requests. Die Änderung funktioniert folgendermaßen:

1. Du gehst in deiner Git-GUI in den Branch, um den es im PR geht.

2. Du möchtest den Commit bearbeiten, in dem eine Änderung gewünscht wurde. Das geht über den Befehl `git commit --amend`, wenn es der letzte Commit ist. In deiner Git-GUI gibt es vermutlich die Möglichkeit, einen Commit zu bearbeiten ("modify", "amend", ...). Folge den Anweisungen.

3. Möglicherweise befindest du dich jetzt im Rebase-Status. Diesen kann man auch manuell aufrufen, indem man in seinem Branch `git rebase -i main` ausführt und den gewünschten zu ändernden Commit zum Editieren vorsieht. Nun kannst du die Änderungen vornehmen, die du machen möchtest. Dann kannst du die Änderungen committen und irgendwo "amend last commit"/"..." auswählen. Anschließend klickst du in deiner GUI "Continue"/"..." und folgst weiter den Anweisungen.

4. Du solltest jetzt wieder aus dem Rebase-Status raus sein. Der letzte Schritt ist, die neuen Änderungen zu pushen. **Achtung!** Du musst force-pushen, weil du die Änderungen auf dem Server ja überschreiben möchtest. Du überschreibst also Dinge auf dem Server! Der Git-Befehl lautet `git push --force`.

5. Fertig. Sind alle Änderungen genehmigt, kannst du - falls notwendig den `Branch durch Rebase aktualisieren` (**Achtung!** Dazu musst du erst die korrekte Methode auswählen. Bitte nutze **nicht** Mergen zum Aktualisieren). Zuletzt kannst du den Button `Rebasen und dann fast-forwarden` klicken, wenn dieser grün ist. Der Branch wird dann automatisch in den `main`-Branch überführt und anschließend gelöscht.

## Ausführliche Anleitung: Pull-Requests reviewen

### Schritt 1: Die Pull-Request-Oberfläche

Unter https://git.zahlenlabyrinth.de/boernel/lilypond-song-includes/pulls findest du alle aktuellen Pull-Requests (PRs). Wenn du in den PR gehst, den du reviewen willst, siehst du drei Reiter: `Diskussion`, `Commits` und `Geänderte Dateien`.

* Diskussion: Hier findest du eine Art "Kommentarspalte" zum PR. Offene Fragen, Kommentare und Diskussionen können hier gestellt/geführt werden. Außerdem werde im Diskussionsfeed Änderungen am PR festgehalten. In der Menüspalte rechts hast du einige Optionen: Du kannst Reviewer anfragen (entweder eine ganze Gruppe oder auch einzelne Personen), Label hinzufügen (das nutzen wir Stand jetzt noch nicht), Zuständigkeiten verteilen und weiteres. Das meiste nutzen wir allerdings nicht - nur "Reviewer anfragen" ist wichtig.

* Commits: Hier hast du einen Überblick über die Commits, die zum Pull-Request gehören.

* Geänderte Dateien: Hier hast du einen Überblick über alle geänderte Dateien des PRs. Wenn du Änderungswünsche hast, kannst du dies in Referenz auf die entsprechende Code-Zeile direkt tun. Das wird im Folgenden noch erklärt.

### Schritt 2: Überprüfen

1. Check in den Branch aus, dessen Pull-Request (PR) du reviewen willst, das heißt: Wechsle den Branch von deinem aktuellen Branch in den zu reviewenden Branch. Der Git-Befehl dafür lautet `git checkout sturmunddrang`.

2. Teste die geänderten Dateien. Mit anderen Worten: Kompiliere die Lieder einmal durch und führe eine Sichtprüfung durch. Wenn du das Lied kennst, kannst du es zum Beispiel auch durchsingen.

3. Überprüfe die Lieder hinsichtlich der Einhaltung der Standards und der Korrektheit der Autor\*innenangaben.

4. Wenn du einen Fehler findest, kannst du ihn entweder selbst ändern (siehe dazu vorheriges Kapitel, Abschnitt "Review") oder eine `Änderung anfragen`. Wie das geht, erfährst du jetzt:

   1. Gehe in den Reiter `Geänderte Dateien`

   2. Gehe in die Datei, in der du etwas ändern willst.

   3. Suche die Code-Zeile, in der du etwas ändern willst. Gehe mit der Maus über die Zeile und klicke auf das grüne Plus am Rand.

   4. Beschreibe deine Änderung so, dass sie für andere verständlich ist.

   5. Wiederhole die obigen Punkte für alle gewünschten Änderungen.

   6. Zuletzt klicke oben rechts auf die Schaltfläche `Überprüfen` und dann auf `Änderung anfragen`.

5. Wenn alles geklärt ist, kannst du den PR freigeben. Das machst du im Reiter `Geänderte Dateien` und dann oben rechts mit der Schaltfläche `Überprüfen`. Wenn du auf `Genehmigen` klickst, wurde der PR freigegeben.



-
