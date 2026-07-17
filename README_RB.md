Wenn du wirklich nur eine einzige Codezeile anfassen oder auskommentieren musst, ist das Vorhaben extrem unkompliziert und du wirst keine Probleme mit Merge-Konflikten bekommen. Git ist intelligent genug, Zeilenänderungen automatisch mitzuziehen, solange der Hauptentwickler nicht exakt dieselbe Zeile umschreibt. [1] 
Das Setup für deinen schlanken Fork läuft in wenigen Schritten ab:
## 1. Das Repository forken & clonen
Klicke auf GitHub beim Repository [can1357/oh-my-pi](https://github.com/can1357/oh-my-pi) oben rechts auf Fork. Klone deine eigene Version anschließend lokal: [2, 3] 

git clone https://github.com
cd oh-my-pi

## 2. Upstream für einfache Updates einrichten
Damit du deine Version später mit einem einzigen Befehl aktuell halten kannst, fügst du das Original-Repository als upstream hinzu: [4] 

git remote add upstream https://github.com

## 3. Zeile anpassen und lokal verlinken
Nachdem du deine Änderung im Code vorgenommen hast (z.B. die Injektion der Tool-Beschreibungen gekürzt oder die entsprechende Zeile auskommentiert hast), registrierst du deine lokale Version im System. OMP nutzt Bun: [2] 

bun install
bun link

Ab jetzt greift das System auf deine modifizierte Version zu, sobald du omp im Terminal ausführst. [5] 
## 4. Updates einspielen (Keine "Merge-Hölle")
Wenn can1357 Updates veröffentlicht, holst du dir diese einfach über das Terminal. Da du nur eine isolierte Zeile geändert hast, läuft der Merge vollautomatisch durch: [4, 6, 7] 

git fetch upstream
git checkout main
git merge upstream/main
git push origin main

Sollte der Entwickler die betroffene Datei im Zuge eines Refactorings komplett löschen oder massiv umbauen, müsstest du deine Anpassung lediglich einmalig an der neuen Stelle einfügen. Bei einer einzigen Zeile ist das in 10 Sekunden erledigt. [1] 
Möchtest du, dass wir nach der exakten Zeile im OMP-Code suchen, welche für das Zusammenbauen der MCP-Tool-Beschreibungen zuständig ist?

[1] [https://github.com](https://github.com/can1357/oh-my-pi/issues/3841)
[2] [https://github.com](https://github.com/can1357/oh-my-pi)
[3] [https://www.reddit.com](https://www.reddit.com/r/git/comments/ou4vht/resolving_merge_conflict_when_merging_changes/)
[4] [https://stackoverflow.com](https://stackoverflow.com/questions/38949951/how-to-solve-merge-conflicts-across-forks)
[5] [https://grokipedia.com](https://grokipedia.com/page/Oh_My_Pi)
[6] [https://github.com](https://github.com/orgs/community/discussions/135244)
[7] [https://github.com](https://github.com/can1357/oh-my-pi/security)

