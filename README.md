# 🛴 BRouter E-Scooter Profil (eKFV-konform & sicherheitsoptimiert)

Ein praxiserprobtes, maßgeschneidertes Routing-Profil für [BRouter](https://brouter.de/) und [bikerouter.de](https://bikerouter.de), speziell entwickelt für Elektrokleinstfahrzeuge (E-Scooter) in Deutschland nach den Vorgaben der **eKFV** (Elektrokleinstfahrzeuge-Verordnung).

Dieses Profil kombiniert **maximale Verkehrssicherheit, 100%ige Gesetzeskonformität und direkte Streckenführung**.

---

## 🚀 Key Features

* **🛡️ Landstraßen- & Tempolimit-Schutz (Neu):** 
  Bundes- (`primary`), Land- (`secondary`) und Kreisstraßen (`tertiary`) ohne baulichen Radweg oder Schutzstreifen werden massiv abgewertet und umfahren. Du wirst nicht mehr auf unübersichtliche 70- bis 100-km/h-Straßen im Mischverkehr geleitet. Besitzt die Straße hingegen einen separaten Radweg (`hascycleway`), nutzt BRouter sie sehr gerne für schnelles Vorankommen.
* **⚖️ 100% eKFV-konform (Anti-"Radfahrer frei"):** 
  Reine Fußwege und Fußgängerzonen sind gesperrt. Gehwege mit dem bloßen Zusatzschild *"Radfahrer frei"* (`bicycle=yes`) werden strikt blockiert, da E-Scooter diese rechtlich nicht befahren dürfen. Geroutet wird ausschließlich über echte Radwege (`bicycle=designated`), Straßen und freigegebene Wege.
* **🚧 Schutz vor verschlossenen Toren & Werksgeländen:** 
  Wege über Kundenparkplätze sowie physische Tore (`barrier=gate`) und Schranken (`barrier=lift_gate`) sind hart gesperrt. Das verhindert, dass man abends oder am Wochenende vor verschlossenen Toren auf Betriebsgeländen strandet.
* **🚦 Ausbalancierte Ampel-Logik:** 
  Ampeln und Bettelampeln werden moderat bestraft. Große Kreuzungen werden sinnvoll umfahren, ohne dass die Navigation in absurde Zickzack-Fahrten durch verwinkelte Wohngebiete verfällt.
* **⏱️ Exakte Fahrzeitberechnung (ETA):** 
  Das Physikmodell ist exakt auf die gesetzliche Maximalunterstützung von **22 km/h** und das reale Gesamtgewicht abgestimmt. Die errechneten Ankunftszeiten stimmen auf die Minute genau.
* **🚫 Barrierefrei:** 
  Treppen (`steps`) und Fähren (`ferry`) sind vollständig ausgeschlossen – kein lästiges Tragen des Scooters.

---

## 📥 Installation & Nutzung

### Option A: Routenplanung via Webbrowser (bikerouter.de) & Export zu Komoot
1. Öffne [bikerouter.de](https://bikerouter.de).
2. Klicke oben links auf das Zahnrad-Symbol (**Profil anpassen / Custom profile**).
3. Füge den Inhalt der Profil-Datei in das Textfeld ein und klicke auf **Anwenden**.
4. Plane deine Route und exportiere sie als **GPX-Datei**.
5. **Wichtig beim Komoot-Import:** 
   * Wähle beim Import zwingend **"Der Originalroute folgen"** (bzw. als *Aufgezeichnete Tour* importieren).
   * Lass Komoot die Route **nicht** automatisch anpassen, da Komoot sonst die eKFV- und Sicherheitsfilter wieder mit seiner eigenen Fahrrad-Logik überschreibt.

### Option B: Offline-Navigation in OsmAnd
1. Kopiere die Profildatei in das BRouter-Verzeichnis deines Smartphones (unter `BRouter/segments4/profiles/`).
2. Wähle in den OsmAnd-Navigationseinstellungen BRouter als Navigationsdienst aus.
3. *Tipp:* Für Android empfiehlt sich die Version **OsmAnd~** (via F-Droid), da dort alle Offline-Karten und Features ohne In-App-Käufe verfügbar sind.

---

## 🛠️ Tuning & Anpassungen

Die Profildatei ist strukturiert aufgebaut und kann leicht angepasst werden:

* **Gesamtgewicht (`totalMass`):** 
  Standardmäßig auf `77` kg (Fahrer + Scooter) gesetzt. Passe diesen Wert an dein tatsächliches Setup an, um Ankunftszeit und Beschleunigungskurven weiter zu verfeinern.
* **Ampel-Malus:** 
  In der `---context:node`-Sektion regelt `switch highway=traffic_signals 350` die Strafe für Ampeln. Erhöhe den Wert (z. B. auf `500`–`800`), wenn du Ampeln noch weiträumiger meiden willst.
* **Treppen erlauben (Scooter tragen):** 
  Setze `assign allow_steps` in der globalen Konfiguration auf `1` und entferne `switch highway=steps 10000` im Costfactor-Block.

---

## ⚠️ Rechtlicher Hinweis (Disclaimer)

Dieses Routing-Profil optimiert Strecken nach den Regeln der deutschen Straßenverkehrsordnung (StVO) und der Elektrokleinstfahrzeuge-Verordnung (eKFV) auf Basis der Daten von OpenStreetMap (OSM). 

Da die Kartendaten durch Freiwillige gepflegt werden, können Beschilderungen vor Ort abweichen. **Es gilt stets die tatsächliche Beschilderung und Verkehrsführung vor Ort! Die Nutzung erfolgt auf eigene Verantwortung.**
