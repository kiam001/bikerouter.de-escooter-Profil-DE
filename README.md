# 🛴 BRouter E-Scooter Profil (eKFV-konform & sicherheitsoptimiert)

Ein praxiserprobtes, maßgeschneidertes Routing-Profil für [BRouter](https://brouter.de/) und [bikerouter.de](https://bikerouter.de/), speziell entwickelt für Elektrokleinstfahrzeuge (E-Scooter) in Deutschland nach den Vorgaben der **eKFV** (Elektrokleinstfahrzeuge-Verordnung).

Dieses Profil schließt die Lücke zwischen normalem Fahrrad-Routing und Autonavigation. Es kombiniert **maximale Verkehrssicherheit, 100%ige Gesetzeskonformität und extrem flüssiges Vorankommen**.

---

## 🚀 Key Features

* **⚖️ 100% eKFV-Legalität:** 
  Reine Fußwege und Fußgängerzonen sind gesperrt. Gehwege mit dem bloßen Zusatzschild *"Radfahrer frei"* (`bicycle=yes`) werden strikt blockiert, da E-Scooter hier rechtlich nichts verloren haben. Geroutet wird ausschließlich über echte Radwege (`bicycle=designated`), Straßen und freigegebene Wege.
* **🛡️ Schutz vor schnellen Landstraßen:** 
  Bundes- (`primary`), Land- (`secondary`) und Kreisstraßen (`tertiary`) ohne baulichen Radweg oder Schutzstreifen werden massiv abgewertet und umfahren. Das System navigiert dich nicht in lebensgefährlichen Mischverkehr bei 70 oder 100 km/h. Besitzt eine Hauptstraße jedoch einen separaten Radweg, wird dieser für direkte, schnelle Linien bevorzugt.
* **🚧 Keine Sackgassen an Werksgeländen:** 
  Wege über private Kundenparkplätze sowie physische Tore (`barrier=gate`) und Schranken (`barrier=lift_gate`) sind hart gesperrt. Das verhindert effektiv, dass man nach Feierabend plötzlich vor verschlossenen Toren auf Industrie- oder Privatgeländen strandet.
* **🚦 Ausbalancierte Ampel-Logik:** 
  Ampeln und Bettelampeln werden moderat bestraft. Nervige Stop-and-Go-Kreuzungen werden sinnvoll umfahren, ohne dass die Engine in absurde Zickzack-Fahrten durch engste Wohngebiete verfällt.
* **⏱️ Hochpräzise Echtzeit-Berechnung (ETA):** 
  Das Physikmodell ist exakt auf die gesetzliche Maximalunterstützung von **22 km/h** und das reale Systemgewicht kalibriert. 
  *Praxistest:* Auf einer urbanen Pendelstrecke von >41 km lag die reine Fahrzeit bei 1h 58m, was einer durchschnittlichen Bewegungsgeschwindigkeit von 21,1 km/h entspricht. Die errechneten Ankunftszeiten (inklusive Ampelstopps) stimmen auf die Minute genau.
* **🚫 Komplett barrierefrei:** 
  Treppen (`steps`) und Fähren (`ferry`) sind vollständig ausgeschlossen.

---

## 📥 Installation & Nutzung

### Option A: Routenplanung via Webbrowser & GPS-Computer / Komoot
Ideal, um Routen zu planen und als GPX-Track auf externe Geräte oder Navigations-Apps zu übertragen.
1. Öffne [bikerouter.de](https://bikerouter.de).
2. Klicke oben rechts auf das Zahnrad-Symbol (**Profil anpassen / Profile**).
3. Füge den Inhalt der Profil-Datei in das Textfeld ein und klicke auf **Anwenden**.
4. Plane deine Route und exportiere sie als **GPX-Datei**.
5. **Wichtig beim Import in Komoot:** 
   * Wähle beim Import zwingend **"Der Originalroute folgen"** (bzw. als *Aufgezeichnete Tour* importieren).
   * Lass die App die Route **nicht** anpassen! Andernfalls überschreibt Komoot die eKFV- und Sicherheitsfilter wieder mit der eigenen, für Scooter ungeeigneten Fahrrad-Logik.

### Option B: Offline-Navigation in OsmAnd
1. Kopiere die Profildatei auf dem Smartphone in das BRouter-Verzeichnis (meist unter `BRouter/segments4/profiles/`).
2. Wähle in den OsmAnd-Navigationseinstellungen *BRouter* als Navigationsdienst aus.

---

## 🛠️ Tuning & Anpassungen

Die Datei ist leicht lesbar strukturiert und kann einfach an das eigene Setup angepasst werden:

* **Gesamtgewicht (`totalMass`):** 
  Standardmäßig auf `77` kg gesetzt (Fahrer + Scooter). Passe den Wert an dein tatsächliches Systemgewicht an, um die Rollwiderstands- und Steigungsberechnung noch weiter zu perfektionieren.
* **Treppen erlauben (Scooter tragen):** 
  Setze `assign allow_steps` in der globalen Konfiguration von `0` auf `1` und entferne `switch highway=steps 10000` aus dem Costfactor-Block, falls du leichte Scooter für Abkürzungen tragen möchtest.

---

## ⚠️ Rechtlicher Hinweis (Disclaimer)

Dieses Routing-Profil optimiert Strecken bestmöglich nach den aktuellen Regeln der deutschen Straßenverkehrsordnung (StVO) und der Elektrokleinstfahrzeuge-Verordnung (eKFV) auf Basis der Daten von OpenStreetMap (OSM). 

Da diese Kartendaten durch Freiwillige gepflegt werden, können Eintragungen fehlerhaft sein oder Beschilderungen vor Ort abweichen. **Es gilt stets die tatsächliche Beschilderung und Verkehrsführung vor Ort! Die Nutzung des Profils erfolgt auf eigene Verantwortung.**

## 🤖 AI Disclaimer

Dieses Routing-Profil sowie die dazugehörige Dokumentation wurden mit Unterstützung künstlicher Intelligenz (Google Gemini) entwickelt, analysiert und sicherheitsoptimiert. Der Code wurde sorgfältig iteriert und realen Praxistests unterzogen, um das bestmögliche und sicherste eKFV-Routing zu gewährleisten. Dennoch gilt: Algorithmen sind nicht unfehlbar – fahre stets mit gesundem Menschenverstand und achte auf den realen Straßenverkehr.
