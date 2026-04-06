#<img width="512" height="512" alt="image" src="https://github.com/user-attachments/assets/65e1be6a-de37-421f-9962-079d0a1960d9" />
 ducttape

**Duct tape over Claude's mouth. Hands still free.**

> Caveman uses few words. Ducktape uses **none**.

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that cuts output tokens **~90%** by eliminating prose entirely. Claude communicates through **actions** — tool calls, code, and symbols — not sentences.

---

## Normal vs Caveman vs Ducktape

| Mode | Response to "Fix the auth bug" | ~Tokens |
|------|-------------------------------|---------|
| Normal | "I'll analyze the authentication middleware. The issue appears to be in the token expiry check where..." *(3 paragraphs + code)* | ~450 |
| [Caveman](https://github.com/JuliusBrussee/caveman) | "Bug in auth. Token check use `<` not `<=`. Fix:" *(+ code)* | ~120 |
| **Ducktape** | *[Edit tool call]* ✓ | ~15 |

---

## Install

```bash
npx skills add danpropagent/ducktape
```

Or manually: copy `skills/ducktape/SKILL.md` into your project's `.claude/skills/` directory.

## Activate

Say any of:
- `/ducktape`
- `"ducktape mode"`
- `"shut up and code"`
- `"no talking"`
- `"actions only"`

## Deactivate

- `"stop ducktape"`
- `"normal mode"`
- `"talk normally"`

---

## Levels

| Level | Name | What it does |
|-------|------|-------------|
| 1 | **strip** | One strip of tape. Max 1 sentence around actions. No filler. |
| 2 | **wrap** | Default. No prose. Tool calls + code only. Symbols when forced (✓ ✗ ⚠ → ?) |
| 3 | **mummy** | Total silence. Only tool calls. Zero text. |

Switch levels: `/ducktape strip`, `/ducktape wrap`, `/ducktape mummy`

---

## Examples

### Bug fix request

**Normal** (~180 tokens):
> I can see the issue! The problem is in your `useEffect` hook — it's missing the `userId` dependency, which means the effect doesn't re-run when the user changes. Let me fix that for you by adding it to the dependency array.

**Ducktape wrap** (~2 tokens):
> *[Edit tool call]* ✓

### "How does useCallback work?"

**Normal** (~250 tokens):
> `useCallback` is a React hook that memoizes a callback function. It returns a memoized version of the callback that only changes if one of the dependencies has changed. This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders...

**Ducktape strip** (~15 tokens):
> Memoizes callback. Re-creates only when deps change. Prevents child re-renders.

**Ducktape wrap** (~20 tokens):
> ```js
> const fn = useCallback(() => doThing(a), [a]) // stable ref until a changes
> ```

---

## Safety

Ducktape comes off for:
- **Security vulnerabilities** — explained clearly
- **Destructive operations** — confirmed before executing
- **Ambiguous requests** — clarified tersely

After safety text → immediately back to silence.

Say **"explain"** to temporarily remove tape for one response.

---

## Inspired By

[caveman](https://github.com/JuliusBrussee/caveman) — the OG token reducer. Ducktape stands on caveman's shoulders and takes the logical next step: why compress words when you can eliminate them?

---

## License

MIT
