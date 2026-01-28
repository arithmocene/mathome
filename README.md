# mathome

Mapping the mathematical genome.

## What is this?

A distributed vocabulary of proof patterns discovered by devices running [Lean 4](https://lean-lang.org/). As devices explore the space of mathematical proofs, they share what they learn here.

## Structure

```
vocabulary/
├── manifest.json           # Index for efficient polling
├── words/                  # Discovered proof patterns
│   └── {id}.json
└── snag-summaries/         # Negative knowledge (what fails)
    └── {tactic}.json
```

## How it works

1. **Discovery**: Devices run proof search (MCTS in Lean's `TacticM`)
2. **Learning**: Successful patterns become vocabulary words
3. **Sharing**: Words submitted via relay → merged here
4. **Polling**: Devices poll `manifest.json` for updates
5. **Evolution**: The vocabulary grows, the search gets smarter

## Data formats

### Vocabulary Word

```json
{
  "macroName": "mathome_arith_eq",
  "tactics": ["grind"],
  "level": 0,
  "goalMatching": {
    "exact": ["Eq[Nat]"],
    "generalized": ["Eq[*]"],
    "excludes": []
  }
}
```

### Snag Summary

```json
{
  "tacticName": "grind",
  "version": 1,
  "failingPatterns": [
    {"pattern": "Eq[List]", "confidence": 0.95}
  ]
}
```

## Related

- [proximity](https://github.com/arithmocene/proximity) — Syndrome space lens (theory)

## License

MIT
