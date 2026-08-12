# Skills Repository

Persönliche Skills und Automationen für Claude Code.

## 🎯 Verfügbare Skills

Alle Skills sind in [.claude/skills/](./.claude/skills) definiert.

### beratungs-outreach
Schreibt personalisierte, fundierte Erst-Nachrichten an Partner und Führungskräfte von Beratungsunternehmen. 

**Nutzen:** `/beratungs-outreach`

**Siehe auch:** [.claude/SKILLS.md](./.claude/SKILLS.md) für allgemeine Dokumentation

## 📖 Struktur

```
.
├── .claude/                           # Claude Code Konfiguration
│   ├── settings.json                  # Konfiguration
│   ├── SKILLS.md                      # Dokumentation für alle Skills
│   └── skills/                        # Skill-Definitionen
│       ├── beratungs-outreach.md      # Beratungs-Outreach Skill
│       ├── beratungs-outreach/        # Assets für den Skill
│       │   └── assets/
│       ├── example-skill.md           # Template für neue Skills
│       └── [weitere Skills]
└── README.md                          # Diese Datei
```

## 🚀 Neue Skills erstellen

Siehe [.claude/SKILLS.md](./.claude/SKILLS.md) für detaillierte Anleitung.

Kurz:
1. Neue Datei in `.claude/skills/my-skill.md` erstellen
2. Mit YAML-Header starten:
   ```markdown
   ---
   name: my-skill
   description: Was der Skill tut
   ---
   ```
3. Mit `/my-skill` aufrufen
