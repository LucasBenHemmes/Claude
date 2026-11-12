# Claude skills & plugins

Verzamelplek voor de skills en plugins die ik met Claude Code gebruik.

## Plugins van anderen

Staan in [`.claude/settings.json`](.claude/settings.json):

- `extraKnownMarketplaces`: waar de plugin vandaan komt (meestal een GitHub-repo)
- `enabledPlugins`: welke plugin aan staat, als `"<plugin>@<marketplace>": true`

Nieuwe plugin toevoegen: voeg de marketplace en de plugin toe aan die twee lijsten.

Huidige plugins:

| Plugin | Bron | Gecontroleerd |
|---|---|---|
| `mattpocock-skills` | [mattpocock/skills](https://github.com/mattpocock/skills) | v1.3.2, geen hooks/MCP/allowed-tools |

## Eigen skills

Zet ze in [`.claude/skills/`](.claude/skills/), één map per skill met een `SKILL.md`.

## Veiligheid: check vóór je iets toevoegt

1. Bekende auteur, actieve repo, licentie?
2. Lees elke `SKILL.md` helemaal.
3. Bestanden die geen Markdown zijn: `find . -type f ! -name '*.md' ! -path './.git/*'`
4. Riskante patronen: `grep -rnEi 'curl|wget|\| *sh|eval|base64|rm -rf|\.ssh|token|secret' .`
5. Let op `hooks/`, `.mcp.json` en `allowed-tools` in de frontmatter.
