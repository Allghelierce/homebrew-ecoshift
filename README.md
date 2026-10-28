# EcoShift Homebrew tap

Installs `carbon`, the [EcoShift](https://github.com/JWanderer73/EcoShift) CLI that finds the lowest-emission time in the next 48 hours to run a long job.

```bash
brew install allghelierce/ecoshift/ecoshift
carbon windows --duration 3h          # headline, chart and table
carbon windows --duration 3h --json   # for coding agents
```

To teach Claude Code when to run it, install its skill (brew prints this after installing):

```bash
mkdir -p ~/.claude/skills
cp -R "$(brew --prefix)/share/ecoshift/skills/carbon-windows" ~/.claude/skills/
```

The forecasts are synthetic until the EcoShift API is deployed, and the output says so.

## Releasing a new version

1. Tag a release in JWanderer73/EcoShift, like `v0.2.0`.
2. Update `url` and `sha256` in `Formula/ecoshift.rb`, and run `brew update-python-resources ecoshift` if dependencies changed.
3. Check it with `brew install --build-from-source ecoshift && brew test ecoshift && brew audit --strict ecoshift`.
