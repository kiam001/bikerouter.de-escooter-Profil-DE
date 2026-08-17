# 🛴 BRouter E-Scooter Profil (eKFV-konform)

Ein maßgeschneidertes Routing-Profil für [BRouter](https://brouter.de/) und [bikerouter.de](https://bikerouter.de), das speziell für Elektrokleinstfahrzeuge (E-Scooter) in Deutschland nach den Regeln der eKFV (Elektrokleinstfahrzeuge-Verordnung) entwickelt wurde. 

Dieses Profil legt den Fokus auf **Legalität, Sicherheit, Reichweiten-Kalkulation und Fahrkomfort**. Es ist optimiert für typische eKFV-Scooter (z.B. ePowerFun ePF-2, Xiaomi Scooter 4) und berücksichtigt die realen Leistungs- und Verbrauchsdaten.

---

## 🚀 Features

* **⚖️ 100% Legales Routing:** Reine Fußwege und Fußgängerzonen sind konsequent gesperrt. Es wird ausschließlich auf Straßen, offiziellen Radwegen und gemeinsamen Rad-/Fußwegen navigiert.
* **🏞️ Fokus auf Nebenstraßen:** Stark befahrene Bundes- und Landstraßen werden massiv bestraft und vermieden. Das Routing bevorzugt Fahrradwege, leere Nebenstraßen und Wohngebiete.
* **🚦 Ampel-Vermeidung:** Ampeln haben einen negativen Kostenfaktor. Das Profil berechnet automatisch Schleichwege und kleine Umwege, um lästige rote Ampeln zu umfahren und den Flow zu erhalten.
* **🚫 Keine Hindernisse:** Treppen und Fähren sind im Routing hart gesperrt (Umtragen entfällt).
* **🔋 Präzises Physik- & Akkumodell:** Das Profil berechnet den Verbrauch nicht über mechanische Radleistung, sondern simuliert die elektrische Arbeit aus dem Akku (inkl. Verluste durch kleine 10-Zoll-Reifen und stehenden Fahrer). 
  * Rechnet mit einem realistischen Verbrauch von **ca. 1,3 kWh pro 100 km** (~13 Wh/km).
  * Ergibt akkurate Vorhersagen (z.B. ca. 50 km Reichweite bei einem 653 Wh Akku).
* **💨 Geschwindigkeitsmodell:** Motorunterstützung kappt bei **22 km/h** (eKFV-Toleranzgrenze). Bergab wird der Scooter durch die Schwerkraft im physikalischen Modell schneller simuliert.

---

## 📥 Installation & Nutzung

### Option A: Nutzung im Webbrowser (bikerouter.de)
1. Öffne [bikerouter.de](https://bikerouter.de).
2. Klicke oben links auf das Zahnrad-Symbol (Profil anpassen / Custom profile).
3. Kopiere den gesamten Inhalt der Datei [`escooter-ekfv.brf`](escooter-ekfv.brf) aus diesem Repository.
4. Füge den Text in das Textfeld bei bikerouter.de ein.
5. Klicke auf "Anwenden" oder schließe das Fenster. Die Route wird nun nach den neuen Scooter-Regeln berechnet.

### Option B: Nutzung in OsmAnd (Android/iOS)
BRouter kann als Offline-Routing-Engine für OsmAnd genutzt werden.
1. Installiere die [BRouter App](https://brouter.de/brouter/revisions.html) auf deinem Smartphone.
2. Speichere die Datei `escooter-ekfv.brf` im BRouter-Verzeichnis auf deinem Handy (meist unter `BRouter/segments4/profiles/`).
3. Wähle das Profil in den BRouter-App-Einstellungen aus.
4. Stelle OsmAnd so ein, dass BRouter als Navigationsdienst für Fahrräder genutzt wird.

---

## 🛠️ Anpassungsmöglichkeiten (Tuning)

Die Profildatei ist ausführlich auf Deutsch kommentiert. Du kannst Parameter leicht selbst anpassen, indem du die Zahlenwerte änderst:

* **Ampeln meiden:** 
  Suche ganz unten nach `switch highway=traffic_signals 300`. Der Wert `300` bedeutet, dass BRouter bis zu 300 Meter Umweg in Kauf nimmt, um eine Ampel zu meiden. Erhöhe diesen Wert (z.B. auf `500`), um Ampeln noch radikaler zu umfahren.
* **Treppen erlauben (Scooter tragen):** 
  Setze `assign allow_steps` von `0` auf `1` und entferne unten die Zeile `switch highway=steps 10000`.
* **Akkukapazität / Verbrauch:**
  Die physikalischen Werte `C_r` (Rollwiderstand) und `C_R` (Luftwiderstand) sind absichtlich überspitzt, um den elektrischen Akkuverbrauch statt der Tretleistung zu simulieren. Wenn dein Scooter mehr oder weniger verbraucht, kannst du diese Werte leicht justieren.

---

## ⚠️ Wichtiger rechtlicher Hinweis (Disclaimer)

Dieses Profil navigiert dich bestmöglich nach den Regeln der StVO / eKFV. **Beachte jedoch:** 
BRouter stützt sich auf die Daten von *OpenStreetMap (OSM)*. Das Profil geht davon aus, dass Fußwege für E-Scooter verboten sind, da OSM-Tags für das spezielle Zusatzschild *"Elektrokleinstfahrzeuge frei"* in der BRouter-Datenbank noch nicht nativ aufgelöst werden können. Du wirst daher im Zweifel auf die Straße geleitet, auch wenn der Fußweg daneben das Freigabe-Schild hat. 

**Es gilt immer die echte Beschilderung vor Ort! Du fährst auf eigene Verantwortung.**

---
*Erstellt mit Fokus auf sichere und effiziente Mikromobilität.*
