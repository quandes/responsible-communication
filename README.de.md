# Responsible Communication

[English](README.md) | **Deutsch**

Ein offener Agent-Skill, der KI-gestütztem Schreiben vor der Veröffentlichung eine zweite
Stimme gibt. Er liest einen Entwurf, zeigt auf konkrete Stellen und fragt nach:
Ist diese Behauptung belegt? Wird hier eine Gruppe pauschal abgewertet? Beschreibt der
Text ein Risiko, oder erzeugt er vor allem Druck?

Der Skill entscheidet nicht für dich. Er legt seine Kriterien offen, ändert nichts heimlich,
und du kannst jedem Hinweis widersprechen. Deutliche Kritik darf deutlich bleiben.

> **Status: 0.2.0, Pilot.** Der Skill wird gerade an echten Entwürfen erprobt. Die
> Testfälle in diesem Repository beschreiben erwartetes Verhalten; unabhängig über
> mehrere Modelle ausgeführt wurden sie noch nicht. Rückmeldungen zu Fehlalarmen und
> übersehenen Problemen sind sehr willkommen.

## Was er tut

- **`reflect` (Standard):** Befunde mit Fundstelle, Kriterium, Beobachtung, Belegstatus,
  Sicherheit und einer Reflexionsfrage. Der Text bleibt unverändert.
- **`review` (auf Wunsch):** zusätzlich alternative Formulierungen, die den legitimen
  Aussagekern erhalten. Nichts wird automatisch übernommen.
- **`guardrail` (experimentell, in 0.2 nicht aktiv):** Prüfung gegen eine versionierte
  Organisationsrichtlinie. Anfragen fallen auf `reflect` zurück.

Kriterien: Entwürdigung, ungerechtfertigte Verallgemeinerung, unbelegte Tatsachen,
irreführende Dringlichkeit oder Bedrohung, Druck durch Schuld oder moralische
Zugehörigkeit, wesentliche Auslassungen, Privatsphäre und erfundene Authentizität,
behauptete Freigaben oder Verfügbarkeit. Siehe
[`criteria.md`](skills/responsible-communication-de/references/criteria.md) und die
[offengelegten Prinzipien](skills/responsible-communication-de/references/principles.md).

## Beispiel

Entwurf: *„Wer unsere KI nicht nutzt, wird bald abgehängt. Verantwortungsvolle Teams setzen deshalb auf unsere Lösung.“*

Der Skill merkt an, dass der erste Satz eine Entwicklung ohne Beleg behauptet und der
zweite moralische Anerkennung an eine Kaufentscheidung koppelt. Er fragt: *„Welches
Problem löst das Angebot nachweisbar, und wie können Leser selbst entscheiden, ob es für
sie relevant ist?“*

## Sprachen

Der Skill liegt in zwei eigenständigen Fassungen vor. Installiere **eine** davon:

| Ordner | Skill-Name | Sprache der Anweisungen |
|---|---|---|
| [`skills/responsible-communication`](skills/responsible-communication) | `responsible-communication` | Englisch (maßgeblich) |
| [`skills/responsible-communication-de`](skills/responsible-communication-de) | `responsible-communication-de` | deutsche Übersetzung |

Beide Fassungen prüfen Entwürfe in jeder Sprache und schreiben den Bericht in der Sprache
deiner Anfrage. Maßgeblich ist die englische Fassung; bei Abweichungen gilt sie.

## Installation

Repository klonen und den gewünschten Skill-Ordner in das Skill-Verzeichnis deines Agenten kopieren.

```bash
git clone https://github.com/quandes/responsible-communication.git

# Claude Code (persönlich) – oder .claude/skills/ innerhalb eines Projekts
cp -r responsible-communication/skills/responsible-communication-de ~/.claude/skills/

# Codex und andere Agent-Skills-Hosts – auf Projektebene
cp -r responsible-communication/skills/responsible-communication-de .agents/skills/
```

Danach den Agenten ausdrücklich beauftragen, zum Beispiel:
*„Prüfe diesen Entwurf mit responsible-communication-de im Modus reflect. Verändere ihn nicht.“*

Der Skill folgt der [Agent-Skills-Spezifikation](https://agentskills.io/specification).
Für Codex ist der automatische Aufruf abgeschaltet (`agents/openai.yaml`), denn die Prüfung
soll eine bewusste Entscheidung sein.

## Grenzen

- Der Skill ist eine Arbeitsanweisung für einen Host-Agenten, kein eigenständiges
  Programm. Host-Regeln und Werkzeuge bestimmen, was tatsächlich ausgeführt wird.
- Er ist keine juristische Prüfung, kein Gütesiegel und keine Veröffentlichungssperre.
  Freigaben müssen außerhalb des Sprachmodells durchgesetzt werden.
- Ein zweiter Durchgang mit demselben Modell ist keine unabhängige Prüfung.
- Ein Schutz vor Desinformation oder Prompt Injection wird nicht versprochen.
- Der Skill selbst speichert, protokolliert und überträgt nichts. Die Verarbeitung durch
  deinen Host ist davon getrennt.

## Rückmeldungen

Bitte ein Issue mit einem **anonymisierten Minimalbeispiel** anlegen: Modell,
Skill-Version, erwartetes Verhalten und tatsächliche Ausgabe. Keine privaten Entwürfe oder
persönlichen Details einfügen. Anpassungen sind willkommen; eigene Regeln bitte als solche
kennzeichnen (siehe
[Prinzipien](skills/responsible-communication-de/references/principles.md#anpassungen)).
Ein Fork ist keine Billigung durch die ursprünglichen Autoren.

## Hintergrund

Der Skill ist aus dem redaktionellen Projekt *KI mit Verantwortung* entstanden:
KI unterstützt, Menschen verantworten. Initiiert von Matthias Klinger, gepflegt von
[Quandes](https://quandes.com).

## Lizenz

[MIT](LICENSE)
