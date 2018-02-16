# Dokumentationsvorlagen
Hier können die aktuell gültigen Vorlagen für die Protokolle und Diplomarbeiten der Abteilung HIT abgerufen werden.

## Protokollvorlagen
Genauere Informationen zur Installation, Konfiguration und Kompilierung der Protokollvorlage finden sich im zugehörigen Repository unter https://github.com/TGM-HIT/latex-protocol.

### Installation
Im Ordner, welcher das Protokoll beinhalten soll kann die Vorlage über Git heruntergeladen werden:
``` sh
git clone https://github.com/tgm-hit/latex-protocol.git
```

Es ist auch möglich mit bekannten Editoren in den entsprechenden Betriebssystemen mit der Vorlage zu arbeiten.

## Diplomarbeitsvorlage
Genauere Informationen zur Installation, Konfiguration und Kompilierung der Diplomarbeitsvorlage finden sich im zugehörigen Repository unter https://github.com/TGM-HIT/diploma-thesis.

### Installation
Die Vorlage der Diplomarbeit kann über Git heruntergeladen werden:
``` sh
git clone https://github.com/tgm-hit/diploma-thesis.git
```
## Build
Am einfachsten kann das Dokument über den `make` Befehl erstellt werden, wenn dieses am System vorhanden ist.
``` sh
make
```

Alternativ kann das Dokument auch folgende Latex Befehle zu diesem Ergebnis:
```
pdflatex -interaction=nonstopmode -shell-escape protocol	# Initial compilation
makeglossaries protocol 					# Compile glossaries
pdflatex -interaction=nonstopmode -shell-escape protocol	# Progressive compilation for glossaries
bibtex protocol 						# Compile bibliography
pdflatex -interaction=nonstopmode -shell-escape protocol	# Progressive compilation for bibtex
pdflatex -interaction=nonstopmode -shell-escape protocol	# Progressive compilation for bibtex
```

### TexMaker / TexStudio
Bei der Verwendung der populären Entwicklungsprogramme TexMaker oder TexStudio, kann ein eigenes Kommando über `Optionen` &rarr; `Konfiguriere TexStudio / TexMaker` &rarr; `Erzeugen` &rarr; `Benutzerkommando` hinzugefügt werden:
```sh
pdflatex -shell-escape -interaction=nonstopmode % | txs:///makeglossaries | pdflatex -shell-escape -interaction=nonstopmode % | txs:///bibtex | pdflatex -shell-escape -interaction=nonstopmode % | pdflatex -shell-escape -interaction=nonstopmode % | txs:///view-pdf-internal --embedded
```

Natürlich kann auch der `make` Befehl mit der Umgebungsvariable `LOG=true` verwendet werden:
```sh
make LOG=true | txs:///view-pdf-internal --embedded
```
