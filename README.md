# 🛴 BRouter E-Scooter Profil (eKFV-konform)

Ein maßgeschneidertes Routing-Profil für [BRouter](https://brouter.de/) und [bikerouter.de](https://bikerouter.de), das speziell für Elektrokleinstfahrzeuge (E-Scooter) in Deutschland nach den Regeln der eKFV (Elektrokleinstfahrzeuge-Verordnung) entwickelt wurde. 

Dieses Profil legt den Fokus auf **Legalität, Sicherheit, exakte Fahrzeitberechnung und Fahrkomfort im dichten Stadtverkehr**. Es ist optimal abgestimmt auf eine Gesamtmasse von 77 kg (Fahrer + Scooter) und typische eKFV-Fahrzeuge (z. B. ePowerFun ePF-2, Xiaomi Scooter 4).

---

## 🚀 Features

* **⏱️ Präzise Ankunftszeit:** Das Physik-Modell ist auf eine maximale Motorunterstützung von 22 km/h abgestimmt. Die Engine liefert hochpräzise Fahrzeiten und berücksichtigt Abbremsvorgänge für Kurven.
* **⚖️ 100% Legales Routing:** Reine Fußwege und Fußgängerzonen sind konsequent gesperrt. Es wird ausschließlich auf Straßen, offiziellen Radwegen und gemeinsamen Rad-/Fußwegen navigiert.
* **🏞️ Fokus auf Nebenstraßen:** Stark befahrene Bundes- und Landstraßen werden massiv bestraft und vermieden. Das Routing bevorzugt Fahrradwege, leere Nebenstraßen und Wohngebiete.
* **🚦 Strikte Ampel-Vermeidung (Anti-Mittelinsel-Logik):** Ampeln haben einen stark negativen Kostenfaktor. Besonders große, mehrspurige Kreuzungen mit mehreren Mittelinseln (Bettelampeln) summieren diese Strafen extrem auf. Das Profil berechnet automatisch flüssige Schleichwege, um ständiges Stop-and-Go zu verhindern.
* **🚫 Keine Hindernisse:** Treppen und Fähren sind im Routing hart gesperrt (Umtragen entfällt komplett).

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
  Suche ganz unten nach `switch highway=traffic_signals 500`. Der Wert `500` bedeutet, dass BRouter einen Umweg von bis zu 500 Metern in Kauf nimmt, um eine Ampel zu umfahren. 
* **Treppen erlauben (Scooter tragen):** 
  Setze `assign allow_steps` von `0` auf `1` und entferne unten die Zeile `switch highway=steps 10000`.
* **Körpergewicht & Beschleunigung:**
  Die Massenberechnung steht aktuell auf `assign totalMass = 77`. Du kannst diesen Wert nach oben oder unten korrigieren, um die Trägheit des Modells beim Anfahren genau auf dich abzustimmen.

---

## ⚠️ Wichtiger rechtlicher Hinweis (Disclaimer)

Dieses Profil navigiert dich bestmöglich nach den Regeln der StVO / eKFV. **Beachte jedoch:** 
BRouter stützt sich auf die Daten von *OpenStreetMap (OSM)*. Das Profil geht davon aus, dass Fußwege für E-Scooter verboten sind, da OSM-Tags für das spezielle Zusatzschild *"Elektrokleinstfahrzeuge frei"* in der BRouter-Datenbank noch nicht nativ aufgelöst werden können. Du wirst daher im Zweifel auf die Straße geleitet, auch wenn der Fußweg daneben in der Realität das Freigabe-Schild hat. 

**Es gilt immer die echte Beschilderung vor Ort! Du fährst auf eigene Verantwortung.**

---
*Erstellt mit Fokus auf sichere und effiziente Mikromobilität.*
