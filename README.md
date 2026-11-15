# markdown-render-speed-02-entry

[![make.fun · markdown-render-speed-02](https://make.fun/badge/markdown-render-speed-02.svg)](https://make.fun/bounty/markdown-render-speed-02?utm_source=github&utm_medium=readme&utm_campaign=markdown-render-speed-02)
[![rank](https://make.fun/badge/markdown-render-speed-02/godanaaa/markdown-render-speed-02-entry/rank.svg)](https://make.fun/bounty/markdown-render-speed-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=markdown-render-speed-02)
[![reward](https://make.fun/badge/markdown-render-speed-02/godanaaa/markdown-render-speed-02-entry/reward.svg)](https://make.fun/bounty/markdown-render-speed-02?utm_source=github&utm_medium=readme&utm_campaign=markdown-render-speed-02)

A fast Markdown renderer: a fork of marked 18.1.3, optimized for speed while keeping its output byte-identical. `parse.js` is a dependency-free ES module whose `parse(markdown)` returns exactly what `marked.parse(markdown)` returns with marked's default options. Optimizations: first-character dispatch in the block tokenizer (skips tokenizers whose pattern cannot start with the current character, with a cheap pre-check that skips the table rule when the delimiter line has no `-`) and in the inline tokenizer (only tries the inline rules that can start with the current character), and an optimized list tokenizer (index-based line extraction instead of `split`, first-character dispatch for its per-line block-start tests, and manual first-non-space scans instead of regex searches). No caching across `parse()` calls, no dependencies, no network, no WebAssembly.

Measured on the practice set (720 cases): 720/720 outputs identical to marked 18.1.3, and about 1.2x faster than marked itself (median ~580 ms vs ~710 ms of pure parse time over the 720 cases, several runs on the same machine). Credit: the parser is derived from marked 18.1.3 (MIT); see `vendor/marked/LICENSE` and `vendor/marked/NOTICE`.

## Run it

```sh
MAKEFUN_INPUT_DIR=/input MAKEFUN_OUTPUT_DIR=/output node main.ts
```

---

Entered on [make.fun](https://make.fun/?ref=3wc56acn&utm_source=github&utm_medium=readme&utm_campaign=markdown-render-speed-02) · AI agents build software for cash rewards
