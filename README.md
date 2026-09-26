# agent-readiness-checks

The open specification of the agent-readiness checks behind [Scovant](https://scovant.com) —
every rule, its category, severity and maturity, plus the public parts of the scoring model.

**[CHECKS.md](CHECKS.md)** is generated from the live rule catalog on every release, so it
always matches [scovant.com/rules](https://scovant.com/rules) and the machine-readable
`https://scovant.com/api/public/rules`. If you want the rules as data, use that endpoint;
if you want them as a document you can diff between releases, this file is it.

## Two scanners, two check sets

| | Scovant Core (open source) | Scovant Cloud |
|---|---|---|
| What | Passive, evidence-first scanner you run yourself — CLI, GitHub Action, MCP server | Full-site crawl, real AI-agent simulations, CI regression detection, monitoring |
| Checks | Its own public check set with its own public scoring — [`docs/checks.md`](https://github.com/Scovant/scovant-core/blob/main/docs/checks.md) in the Core repo | The rules in [CHECKS.md](CHECKS.md) here |
| Where | [github.com/Scovant/scovant-core](https://github.com/Scovant/scovant-core) · `pip install scovant-core` | [scovant.com](https://scovant.com) |

The two check sets are related but not identical: Core covers what can be verified
passively from the outside without an account; Cloud adds full-site sampling, browser
rendering, agent simulations with a multi-model catalog, and the regression layer.

## Scoring transparency

The category weights, per-severity points and badge/grade thresholds are public and
appear in CHECKS.md exactly as the engine uses them. The exact multipliers of the
agent-blocking and failed-simulation caps are part of the proprietary engine and are
deliberately not published — the *existence* of the caps is. The reasoning is on
[scovant.com/scoring](https://scovant.com/scoring).

## Links

| Resource | Link |
|---|---|
| Rule catalog (interactive) | https://scovant.com/rules |
| Rule catalog (JSON) | https://scovant.com/api/public/rules |
| Scoring methodology | https://scovant.com/scoring |
| Open-source scanner | https://github.com/Scovant/scovant-core |
| CI examples | https://github.com/Scovant/ci-examples |
| Readiness checklist | https://github.com/Scovant/agent-readiness |
| Docs | https://scovant.com/docs |
| MCP discovery | https://scovant.com/.well-known/mcp.json |

## Contributing

CHECKS.md is generated — corrections to a rule's text belong in the catalog and land
here on the next release. Issues pointing out a check that fires wrongly on a real site
are welcome; include the URL and the finding.

## License

[CC BY 4.0](LICENSE) — reuse freely with attribution to [Scovant](https://scovant.com).
