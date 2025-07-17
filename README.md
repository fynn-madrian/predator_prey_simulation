# Predator-Prey Reinforcement Learning Simulation

Dieses Projekt simuliert ein dynamisches Predator-Prey-Szenario zur Untersuchung lernfähiger Agenten mit Hilfe von Reinforcement Learning. Die Agenten agieren in einer physikalisch plausiblen 2D-Umgebung mit Hindernissen, Futterquellen und einem jagenden Gegenspieler. Das Trainingsverfahren basiert auf PPO (Proximal Policy Optimization) mit LSTM zur Verarbeitung sequentieller Beobachtungen.

Ziel ist es, die Lernfähigkeit und Generalisierbarkeit von Agentenverhalten in verschiedenen Subtasks wie Navigation, Flucht und Nahrungssuche zu analysieren. Die Umgebung ist vollständig modular und nutzt die PettingZoo-Schnittstelle.

---

## Visualisierte Verhaltensbeispiele

Die folgenden GIFs zeigen exemplarische Durchläufe trainierter Agenten in verschiedenen Szenarien. Alle Clips sind im Repository unter `animated_runs/` verfügbar:

- **circle_field**: Ein Agent leert effizient ein Futterfeld und weicht dabei gleichzeitig dem Jäger aus
        <img src="https://github.com/fynn-madrian/predator_prey_simulation/blob/single_agent/animated_runs/circle_field.gif" width="500"/>

- **flee_river**: Der Agent nutzt einen engen Pfad mit Fluss als Deckung und entkommt dem Jäger
        <img src="https://github.com/fynn-madrian/predator_prey_simulation/blob/single_agent/animated_runs/flee_river.gif" width="500"/>

- **flee_rocks**: Der Agent verwendet große Felsen zur Flucht und Sichtblockade gegenüber dem Jäger
        <img src="https://github.com/fynn-madrian/predator_prey_simulation/blob/single_agent/animated_runs/flee_rocks.gif" width="500"/>

- **spinning_navigate**: Navigation durch ein komplexes Feld mit Hindernissen zur Erreichung eines Ziels
        <img src="https://github.com/fynn-madrian/predator_prey_simulation/blob/single_agent/animated_runs/spinning_navigate.gif" width="500"/>

---

## Installation

```bash
# Virtuelle Umgebung erstellen
python -m venv venv
source venv/bin/activate      # Linux/macOS
venv\Scripts\activate       # Windows

# Abhängigkeiten installieren
pip install -r requirements.txt
```

---

## Konfiguration

Alle konfigurierbaren Parameter zur Umgebungsstruktur und Trainingsstrategie befinden sich in:

- `config.json` – grundlegende Einstellungen zur Map, Sichtfeld, Belohnungsstruktur etc.
- `algorithms.py` – Trainingsarchitektur und PPO-Hyperparameter

---

## Training

```bash
python main.py
```

Trainingsdaten werden automatisch unter `logs/<timestamp>/` gespeichert.

### Trainingsanalyse

```bash
python analyze_run.py
```
Generiert in `graphs/` verschiedene Plots zur Reward-Entwicklung, Episodenlängen etc.

### Video-Visualisierung eines Trainingslaufs

```bash
python visualize_run.py
```
Erzeugt ein `.avi`-Video der Simulation basierend auf Umgebungsdaten und Agentenpfaden.

---

## Evaluation

```bash
python evaluate.py
```
Das Evaluationsskript erlaubt eine systematische Bewertung von trainierten Modellen. Dabei werden je nach Szenario spezifische Metriken wie „Zeit bis Ziel“, „Überlebenszeit“ oder „gesammeltes Futter“ extrahiert. Die besten 5 Durchläufe werden unter `evaluate_log/` gespeichert.

