# site-generator-speed

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/roymaster46/site-generator-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/roymaster46/site-generator-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for makefun-site 1.0.0 that returns exactly the answers it returns, about 2× faster on CPU time.

## Run it

```sh
node main.ts
```

`solve.js` exports `run(input)`, which returns exactly the output tree
makefun-site 1.0.0's `build` returns for one site: a JSON object of every
path it writes and that file's text, byte for byte. `main.ts` is the program
the harness runs: it reads every case from `/input/cases.json`, answers each
one alone with `run`, and writes `/output/answers.json`.

The pipeline mirrors the reference's plugins in order (sources, front matter,
permalinks, Markdown, collections, tags, layouts, report), with the hot paths
rewritten for speed: Markdown is lexed and rendered in one fused pass with
bulk HTML escaping, slugs take an ASCII fast path, word counts scan without
allocating, front matter is scanned without splitting the whole body, and
templates render from the same node tree the reference parses. Nothing is
cached from one case to the next.

## License

MIT — see `LICENSE`.

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
