# Notebook zum Mitklicken (JupyterLite)

Das Notebook `content/brustkrebs-ml.ipynb` läuft komplett im Browser der Studierenden (JupyterLite mit Pyodide). Es braucht keine Installation, kein Konto und keinen Server. Python wird beim ersten Öffnen aus dem Internet geladen (ca. 30 bis 60 Sekunden).

## Inhalt des Notebooks

| Schritt | Thema | Folie |
|---|---|---|
| 0 | Vorbereitung (Laden) | Teil A |
| 1 | Daten ansehen: welches Merkmal trennt gut/bösartig? | Teil A |
| 2 | Trainings- und Testdaten (70/30) | Teil A |
| 3 | Logistische Regression mit 2 Merkmalen, Entscheidungsgrenze, Trainings- vs. Testfehler | Teil A |
| 4 | Modellkomplexität und Overfitting (Schieberegler). Dazu eine sichtbare Code-Zeile `anzahl_trainingspatientinnen = 80` zum Ändern (30 = mehr Overfitting, 398 = kaum Overfitting) | Teil A |
| 5 | Schwellenwert: Konfusionsmatrix, Sensitivität, Spezifität, PPV, ROC/AUC, PPV bei anderer Prävalenz (Screening 1 %) | Teil B |
| 6 | Kalibrierung (mit Konfidenzintervallen pro Gruppe) | Teil B |
| 7 | Unsicherheit: Konfidenzintervalle je nach Grösse des Testdatensatzes | Teil B |
| 8 | Bonus: Verteilungsverschiebung (Spital B misst Zellkerne grösser) | Teil B |

Der Programmcode ist in allen Zellen eingeklappt, ausser der einen Zeile in Schritt 4.

Die Zahlen auf der Folie „Die Konfusionsmatrix“ (49 / 4 / 15 / 103) entsprechen Schritt 5 mit Modell „einfach“ und Schwelle 0.5.

## Lokal testen (vor der Lektion)

Im Terminal:

```
cd notebook/website
python3 -m http.server 8000
```

Dann im Browser öffnen:
http://localhost:8000/notebooks/index.html?path=brustkrebs-ml.ipynb

(`website/` ist die fertig gebaute Seite. Nach Änderungen am Notebook neu bauen mit `jupyter lite build` im Ordner `notebook/`, siehe `requirements.txt`.)

## Veröffentlichen mit GitHub Pages (empfohlen)

1. Auf GitHub ein neues, **öffentliches** Repository anlegen, z.B. `jmm-ml-notebook`.
2. Den **Inhalt** des Ordners `notebook/` hochladen (inkl. des versteckten Ordners `.github/`; `website/` wird nicht gebraucht, siehe `.gitignore`).
3. Im Repository: *Settings → Pages → Build and deployment → Source: GitHub Actions*.
4. Der Workflow `.github/workflows/deploy.yml` baut die Seite bei jedem Push automatisch (ca. 2 Minuten, siehe Reiter *Actions*).
5. Link für die Studierenden:
   `https://<github-name>.github.io/jmm-ml-notebook/notebooks/index.html?path=brustkrebs-ml.ipynb`
6. Diesen Link in `vorlesung-ml.tex` bei `\notebookurl` eintragen. Der QR-Code auf den beiden Notebook-Folien wird automatisch daraus erzeugt.

Alternative ohne GitHub Actions: den Inhalt von `website/` auf einen beliebigen statischen Webspace hochladen (z.B. Uni-Webspace). Es muss nur per HTTPS erreichbar sein.

**Tipp:** Da die Studierenden Laptops verwenden (QR-Code eher fürs Handy), lohnt sich zusätzlich ein kurzer Link, z.B. eine Weiterleitung auf der Lab-Webseite.

## Hinweise für die Lektion

* Studierende sollen den Link **zu Beginn der Lektion** öffnen und Schritt 0 ausführen, damit Python geladen ist, wenn es losgeht.
* Spitalnetz: Die Seite lädt Python-Pakete von `cdn.jsdelivr.net`. Vorher im LUKS-WLAN testen.
* Jede Person arbeitet in ihrem eigenen Browser. Änderungen werden lokal im Browser gespeichert. Zum Zurücksetzen: Menü *File → Reload Notebook from Disk* oder Browserdaten der Seite löschen.
* Falls etwas hängt: *Kernel → Restart Kernel and Run All Cells*.
