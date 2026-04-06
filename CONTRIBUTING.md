# Contributing to Ducktape

## The One Rule

Keep it brief. This project is about eliminating unnecessary output — contributions should embody that philosophy.

## How to Contribute

1. Fork the repo
2. Create a branch (`git checkout -b my-change`)
3. Make your change
4. Test it by installing the skill locally and verifying behavior
5. Submit a PR

## What to Work On

- **`skills/ducktape/SKILL.md`** — the core skill definition. This is the product.
- **`README.md`** — documentation improvements.
- **Bug reports** — open an issue describing what ducktape said when it should've been silent (or vice versa).

## Guidelines

- Small focused changes > big rewrites
- The skill file should remain readable by a human in under 2 minutes
- Don't add complexity for edge cases that rarely occur
- Safety exceptions are sacred — don't remove them

## Testing Your Changes

1. Copy `skills/ducktape/SKILL.md` to your project's `.claude/skills/` directory
2. Start a Claude Code session
3. Say "ducktape mode"
4. Give it tasks and verify it stays silent (or appropriately speaks for safety)
5. Test all three levels: strip, wrap, mummy
