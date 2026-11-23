# site-generator-speed

A faster drop-in for makefun-site 1.0.0 (make.fun's own static site
generator), written for the `site-generator-speed-01-run-20261122` bounty.

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
