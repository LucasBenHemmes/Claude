# Claude skills & plugins

Verzamelplek voor de skills en plugins die ik met Claude Code gebruik.

## Installeren op een computer (eenmalig)

```bash
claude plugin marketplace add LucasBenHemmes/claude
```

```bash
claude plugin install lucas-skills@lucas
```

```bash
claude plugin install mattpocock-skills@lucas
```

```bash
claude plugin install apple-design@lucas
```

```bash
claude plugin install humanizer@lucas
```

In deze repo zelf gebeurt dit automatisch via [`.claude/settings.json`](.claude/settings.json).

## Opbouw

- [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json): de catalogus. Elke plugin heeft een `name` en een `source` (een map hier, of een GitHub-repo).
- [`plugins/lucas-skills/`](plugins/lucas-skills/): mijn eigen skills, in `skills/<naam>/SKILL.md`.

## Iets toevoegen

- **Eigen skill:** nieuwe map in `plugins/lucas-skills/skills/` en `version` ophogen in `plugins/lucas-skills/.claude-plugin/plugin.json`.
- **Plugin van een ander:** nieuw item in `marketplace.json`, bijv. `{ "name": "...", "source": { "source": "github", "repo": "eigenaar/repo" } }`. Zet hem in `.claude/settings.json` onder `enabledPlugins` als `"<naam>@lucas": true`.

| Plugin | Bron | Gecontroleerd |
|---|---|---|
| `lucas-skills` | deze repo | eigen werk |
| `mattpocock-skills` | [mattpocock/skills](https://github.com/mattpocock/skills) | v1.3.2, geen hooks/MCP/allowed-tools |
| `apple-design` | [emilkowalski/skills](https://github.com/emilkowalski/skills) (alleen `skills/apple-design`) | `4061b67`, alleen Markdown, MIT |
| `humanizer` | [blader/humanizer](https://github.com/blader/humanizer) | v4.0.0 (`b48c832`), geen hooks/MCP/allowed-tools, MIT |

## Veiligheid: check vóór je iets toevoegt

1. Bekende auteur, actieve repo, licentie?
2. Lees elke `SKILL.md` helemaal.
3. Bestanden die geen Markdown zijn: `find . -type f ! -name '*.md' ! -path './.git/*'`
4. Riskante patronen: `grep -rnEi 'curl|wget|\| *sh|eval|base64|rm -rf|\.ssh|token|secret' .`
5. Let op `hooks/`, `.mcp.json` en `allowed-tools` in de frontmatter.
