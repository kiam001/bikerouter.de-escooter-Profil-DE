# 🛴 BRouter E-Scooter Profil (eKFV-konform)

Ein praxiserprobtes, maßgeschneidertes Routing-Profil für [BRouter](https://brouter.de/) und [bikerouter.de](https://bikerouter.de), das speziell für Elektrokleinstfahrzeuge (E-Scooter) in Deutschland nach den Regeln der eKFV (Elektrokleinstfahrzeuge-Verordnung) entwickelt wurde. 

Dieses Profil legt den Fokus auf **Legalität, flüssiges Vorankommen im dichten Stadtverkehr und hochpräzise Fahrzeitberechnungen**. 

---

## 🚀 Features

* **⚖️ 100% Legales Routing (Anti-"Fahrrad frei"):** Reine Fußwege und Fußgängerzonen sind konsequent gesperrt. Das Profil blockiert rigoros geteilte Wege mit dem bloßen Zusatzschild "Radfahrer frei" (`bicycle=yes`), da E-Scooter hier nicht fahren dürfen. Nur echte Radwege (`bicycle=designated`) und legale Straßen werden für das Routing genutzt.
* **🚦 Balancierte Ampel-Vermeidung:** Ampeln, insbesondere nervige Radweg-Bettelampeln an Mittelinseln (`crossing=traffic_signals`), werden stark bestraft (`cost = 800`). Die Engine umfährt riesige Autobahnauffahrten und Mega-Kreuzungen, bleibt aber flexibel genug, um bei fehlenden Alternativen keine unlogischen Zickzack-Umwege zu generieren.
* **⏱️ Präzise Ankunftszeit:** Das Physik-Modell ist exakt auf eine maximale Motorunterstützung von 22 km/h abgestimmt. Die Fahrzeiten werden auf Basis des tatsächlichen Gesamtgewichts (Standard: 77 kg) und des realistischen Bremsverhaltens berechnet – perfekt verlässlich für die Live-Navigation.
* **🏞️ Dynamische Streckenwahl:** Bundes- und Landstraßen werden moderat bestraft. Das Routing bevorzugt leere Nebenstraßen und Wohngebiete, scheut aber nicht davor zurück, Hauptverkehrsadern als kurze "Brücke" zu nutzen, wenn man sich dadurch ewige Ampel-Wartezeiten erspart.
* **🚫 Keine Hindernisse:** Treppen und Fähren sind im Routing hart gesperrt (Umtragen entfällt komplett).

---

## 📥 Installation & Nutzung

### Option A: Routenplanung via Webbrowser (bikerouter.de) & Export zu Komoot
Die beste Methode, um perfekte Routen am PC zu planen und auf dem Smartphone abzufahren:
1. Öffne [bikerouter.de](https://bikerouter.de).
2. Klicke oben links auf das Zahnrad-Symbol (Profil anpassen / Custom profile).
3. Kopiere den gesamten Inhalt der Datei [`escooter-ekfv.brf`](escooter-ekfv.brf) aus diesem Repository in das Textfeld. Klicke auf "Anwenden".
4. Plane deine Route.
5. Exportiere die Route als **GPX-Track**.
6. **Wichtig für Komoot:** Importiere die GPX-Datei in Komoot zwingend als "Aufgezeichnete Tour" oder wähle "Der Originalroute folgen", damit Komoot die eKFV-legale Streckenführung nicht wieder durch seine eigene Fahrrad-Logik überschreibt!

### Option B: Offline-Nutzung in OsmAnd (Android/iOS)
BRouter kann als Offline-Routing-Engine für OsmAnd genutzt werden.
1. Installiere die [BRouter App](https://brouter.de/brouter/revisions.html) auf deinem Smartphone.
2. Speichere die Datei `escooter-ekfv.brf` im BRouter-Verzeichnis auf deinem Handy (meist unter `BRouter/segments4/profiles/`).
3. Wähle das Profil in den BRouter-App-Einstellungen aus und wähle in OsmAnd BRouter als Fahrrad-Navigationsdienst.

---

## 🛠️ Anpassungsmöglichkeiten (Tuning)

Die Profildatei ist ausführlich auf Deutsch kommentiert. Du kannst Parameter leicht selbst anpassen:

* **Ampeln meiden (Feintuning):** 
  Suche ganz unten nach `switch highway=traffic_signals 800`. Der Wert `800` regelt die Ampelstrafe. Erhöhe ihn, wenn BRouter dir zu viele Kreuzungen zumutet, oder senke ihn, wenn dir die Schleichwege zu extrem werden.
* **Treppen erlauben (Scooter tragen):** 
  Setze `assign allow_steps` von `0` auf `1` und entferne im Costfactor-Block die Zeile `switch highway=steps 10000`.
* **Körpergewicht & Beschleunigung:**
  Die Massenberechnung steht aktuell auf `assign totalMass = 77`. Passe den Wert einfach an das Gesamtgewicht (du + dein Scooter) an, um die Trägheit und Ankunftszeit absolut exakt auf dein Setup abzustimmen.

---

## ⚠️ Wichtiger rechtlicher Hinweis (Disclaimer)

Dieses Profil navigiert dich bestmöglich nach den Regeln der StVO / eKFV. **Beachte jedoch:** 
BRouter stützt sich auf die Daten von *OpenStreetMap (OSM)*. Das Profil geht davon aus, dass Fußwege für E-Scooter verboten sind, da das OSM-Tag für das spezielle Zusatzschild *"Elektrokleinstfahrzeuge frei"* in der BRouter-Datenbank noch nicht nativ aufgelöst werden kann. Du wirst daher im Zweifel auf die Straße geleitet, auch wenn der Gehweg in der Realität das Freigabe-Schild hat. 

**Es gilt immer die echte Beschilderung vor Ort! Du fährst auf eigene Verantwortung.**
