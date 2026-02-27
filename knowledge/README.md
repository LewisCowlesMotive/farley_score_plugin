# Knowledge Base

Reference documents used by both `/msec:farley-score` and `/msec:farley-score-coach` commands.

## Contents

### farley/

- **farley-properties-and-scoring.md** - Dave Farley's 8 Properties of Good Tests, scoring rubrics (0-10), Farley Index formula, sigmoid normalization, rating scale, and aggregation methodology
- **signal-detection-patterns.md** - Language-specific static detection heuristics for Java, Python, JavaScript/TypeScript, Go, and C#. Per-property signal tables mapping test smells to Farley properties. Includes mock anti-pattern detection (AP1-AP4) covering 9 mocking frameworks

## Usage

These documents are referenced by the command files during analysis:
- Phase 2 (Signal Collection) reads `signal-detection-patterns.md`
- Phase 3 (Scoring) reads `farley-properties-and-scoring.md`

## Attribution

- **Dave Farley** - 8 Properties of Good Tests framework
- **Andrea LaForgia** - Scoring methodology, signal detection patterns, tautology theatre analysis (from [test-design-reviewer](https://github.com/andlaf-ak/claude-code-agents/tree/main/test-design-reviewer))
