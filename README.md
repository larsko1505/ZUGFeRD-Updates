# ZUGFeRD Rechnungsstudio – Updates

**Aktueller Programmstand: 1.1.12 (15. November 2026)**

Dieses GitHub-Repository ist der **öffentliche Verteilungskanal für verschlüsselte Programm- und Excel-Vorlagenupdates** des ZUGFeRD Rechnungsstudios für Hansen Transporte. Die Original-Excel-Dateien und der ausführbare Windows-Installer werden **nicht unverschlüsselt** als öffentliche Release-Dateien bereitgestellt.

## Aktuelle Veröffentlichungen

| Bestandteil | Freigabe | Inhalt |
| --- | --- | --- |
| Rechnungsstudio | [Programm 1.1.12](https://github.com/larsko1505/ZUGFeRD-Updates/releases/tag/programm-v1.1.12) | AES-256-GCM-verschlüsselter Setup-Download `.zufexe` |
| Excel-Rechnungsvorlagen | [Vorlagenrevision 1](https://github.com/larsko1505/ZUGFeRD-Updates/releases/tag/vorlagen-v1) | AES-256-GCM-verschlüsseltes Paket mit fünf `.xlsm`-Vorlagen (`.zufenc`) |

Die jeweils gültigen **digital signierten** Updateinformationen liegen in [`programm_verschluesselt.json`](programm_verschluesselt.json) und [`vorlagen_verschluesselt.json`](vorlagen_verschluesselt.json). Die Anwendung prüft die Ed25519-Signatur, Versionsnummer und SHA-256-Prüfsummen. Zum Entschlüsseln wird ein einmalig eingerichteter, **nicht im Installer enthaltener** Schlüssel benötigt.

**Wichtig:** Eine `.zufexe` ist **keine direkt startbare Windows-EXE**. Für die Erstinstallation wird eine lokale, vertrauenswürdig übertragene Setup-Datei benötigt.

## Was das Rechnungsstudio kann

Das Windows-Programm erstellt aus fünf verschieden aufgebauten Excel-Rechnungsvorlagen ZUGFeRD-/Factur-X-Rechnungen mit eingebetteter XML nach EN 16931 und PDF/A-3. Es unterstützt Excel-Arbeitskopien, PDF-/XML-Erstellung und technische Validierung. Rechnerbezogene Sicherungen und Arbeitsmappen liegen außerhalb des Windows-Programmordners und sollen bei Updates erhalten bleiben.

**Neu in 1.1.12:** Excel-Arbeitskopien heißen nach der Rechnungsnummer, beispielsweise `43.26-01-01.xlsm` bei Rechnungsnummer `43.26/01/01`. Wird die Nummer in Excel vor der PDF-Erstellung geändert, passt die Anwendung den Arbeitskopie-Dateinamen an. Eine bereits vorhandene Arbeitskopie wird **niemals überschrieben**.

**Seit 1.1.11:** Bei einer bereits existierenden Rechnungsnummer erscheint ein deutliches Warnfenster. Sicherste Wahl: Excel öffnen und Rechnungsnummer ändern. Eine noch nicht versendete/gebuchte Rechnung lässt sich nur nach mehreren Sicherheitsabfragen in einen gesonderten Ordner archivieren; **keine endgültige automatische Löschung**. Versendete oder gebuchte Rechnungen sind gegebenenfalls fachlich korrekt zu stornieren bzw. zu berichtigen.

**Seit 1.1.10:** Große anklickbare Hinweise für verfügbare **Excel-Vorlagenupdates** (gelb) und **Programmupdates** (violett) direkt in der Hauptansicht. Im Hintergrund wird beim Programmstart nach neuen signierten Versionen geprüft. Download und Installation erfolgen nur nach Bestätigung.

## Für Anwenderinnen und Anwender

1. Rechnungsstudio aus der bereitgestellten **lokalen Setup-EXE** installieren.
2. Bei der ersten Excel-Vorlagenaktualisierung den einmalig vom Herausgeber übermittelten Einrichtungscode eingeben.
3. Bei neuen GitHub-Versionen in der Hauptansicht auf den auffälligen Hinweis klicken oder über „Programmupdate prüfen“ bzw. „Excel-Vorlagen aktualisieren“ aktualisieren.
4. Das Programm sichert ältere aktive Vorlagen vor dem Ersetzen. Bereits erstellte Rechnungen und bearbeitete Arbeitskopien werden nicht automatisch geändert.

**Für den PC der Mutter ist kein GitHub-Konto erforderlich.** Version 1.1.8 enthält einen Fehler in der Versionsprüfung; dort ist zur Reparatur einmalig die manuelle Installation einer neueren Setup-Version nötig.

## Fünf Excel-Mastervorlagen bearbeiten und veröffentlichen

Die verbindlichen Originalvorlagen werden auf dem **eigenen Rechner** bearbeitet, gespeichert und geschlossen. Danach unter

`D:\Dokumente\ZUGFeRD-Rechnungsstudio\Github_Veroeffentlichung`

1. `EXCEL_MASTER_UEBERNEHMEN.cmd` starten und den Ordner der fünf bearbeiteten Vorlagen auswählen. Die Zuordnungen werden kontrolliert; Freigabekopien entstehen separat.
2. `EXCEL_VORLAGEN_VERSCHLUESSELT_VERÖFFENTLICHEN.cmd` starten, eine höhere Revisionsnummer wählen (nach 1 folgt 2) und den verschlüsselten GitHub-Release nach Prüfung bestätigen.

**Die fünf bearbeitbaren `.xlsm`-Dateien liegen nicht einzeln in diesem öffentlichen Repository.** Das gesonderte private Repository [`ZUGFeRD-Vorlagen-Privat`](https://github.com/larsko1505/ZUGFeRD-Vorlagen-Privat) wurde als optionale Ablage angelegt, enthält derzeit aber noch **keine** Original-XLSM und ist nicht die aktive Downloadquelle.

## Sicherheit und Grenzen

- Keine echten Rechnungen, persönlichen Daten, Excel-Master oder geheimen Freischaltcodes öffentlich veröffentlichen.
- Die Verschlüsselung schützt herunterladbare Programm-/Vorlagenpakete; wer den einmaligen Schlüssel kennt, kann diese entschlüsseln. Es gibt bei dieser GitHub-only-Verteilung **keinen separaten Widerruf pro PC**, sondern im Bedarfsfall nur einen Schlüsselwechsel.
- Der Windows-Installer ist **noch nicht mit einem Authenticode-Herausgeberzertifikat signiert**. Windows SmartScreen/UAC kann warnen. Defender- oder Windows-Schutzfunktionen nicht deaktivieren.
- Die Rechnungsnummernprüfung erfolgt derzeit **lokal pro PC**, nicht PC-übergreifend. Für parallele Rechnungsstellung auf mehreren PCs wäre eine zentrale Nummernverwaltung erforderlich.
- Ein erfolgreiches Entwicklertestprotokoll ersetzt nicht den Praxistest auf dem jeweiligen Windows-Rechner.

Quellcode und Entwicklungshistorie werden separat in einem privaten Repository gepflegt. Dieses Repository ist ausschließlich der Updatekanal.
