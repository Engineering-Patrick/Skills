# Skills Dokumentation

Skills sind wiederverwendbare Arbeitsanweisungen, die du im Terminal mit `/skillname` aufrufen kannst. Sie ermöglichen es dir, mir spezifische Workflows für dein Projekt zu definieren.

## Struktur eines Skills

Jeder Skill ist eine Markdown-Datei im Verzeichnis `.claude/skills/`:

```markdown
---
name: my-skill
description: Was dieser Skill tut (eine Zeile)
type: task
---

# Titel

Deine Anleitung hier. Dies wird mir angezeigt, wenn der Skill aufgerufen wird.
```

## Felder im Frontmatter

- **name**: Der Name des Skills (wird in `/skillname` verwendet)
- **description**: Eine kurze Beschreibung (wird in der Skill-Liste angezeigt)
- **type**: `task` für Arbeitsschritte

## Beispiele für Skills

### 1. Projekt-Setup Skill

```markdown
---
name: setup-project
description: Initialisiere ein neues Projekt mit allen Dependencies
---

# Projekt-Setup

1. Installiere alle Dependencies mit `npm install`
2. Richte die Umgebungsvariablen ein
3. Starte den Entwicklungsserver mit `npm run dev`
```

### 2. Code-Review Skill

```markdown
---
name: review-changes
description: Überprüfe Änderungen auf Best Practices
---

# Code Review

Überprüfe die folgenden Punkte:
- Type Safety (TypeScript/ESLint)
- Sicherheit (keine SQL-Injection, XSS, etc.)
- Performance (keine N+1 Queries, etc.)
- Tests (Sind alle kritischen Pfade getestet?)
```

### 3. Deploy Skill

```markdown
---
name: deploy-production
description: Sichere Deployment zu Production
---

# Production Deployment

1. Stelle sicher, dass alle Tests grün sind
2. Überprüfe die Versionsnummer in package.json
3. Pushe zu main branch
4. Starte den Build-Prozess
```

## Skills verwenden

Rufe einen Skill auf mit:
```
/skillname
```

Beispiel:
```
/setup-project
```

## Best Practices

- **Klar und konkret**: Schreib genaue Schritte, keine vagen Richtlinien
- **Kontextabhängig**: Bezieh dich auf spezifische Dateien oder Commands deines Projekts
- **Wiederverwendbar**: Schreib Skills, die du mehrfach nutzen wirst
- **Wartbar**: Aktualisiere Skills, wenn sich die Prozesse ändern

## Verfügbare Skills in diesem Projekt

Siehe `.claude/skills/` für die Gesamtliste.
