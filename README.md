# site-generator-speed: a faster drop-in for makefun-site 1.0.0

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/arsalive-dot/site-generator-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/arsalive-dot/site-generator-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

An entry for make.fun's [site-generator-speed-01-run-20261122](https://make.fun/bounty/site-generator-speed-01-run-20261122) bounty: a faster drop-in for make.fun's own makefun-site 1.0.0 that answers exactly as it does on every case.

- `solve.js` — the program. A from-scratch reimplementation of makefun-site 1.0.0's build (front matter, its Markdown subset, its template dialect, its slug rule, its report), structured for speed: bulk-run inline rendering instead of per-character escaping, direct block rendering with no token array, one card per source instead of recomputing it, and memoized slugs and word counts. Pure JavaScript, no dependencies, no WebAssembly, nothing cached from one case to the next.
- `main.ts` — the program the harness runs: reads every case from `/input/cases.json`, answers each with `run` from `solve.js`, writes `/output/answers.json`.

## Practice results

On the kit's practice set (3 cases, 250–480 Markdown sources each), the entry's answers are byte-identical to makefun-site 1.0.0's on every case (3/3, confirmed by the kit's own `grade-local`, L1 regrade reproduced byte for byte), and about 2.5x faster on CPU time than the house baseline (~220 ms vs ~550 ms for the three cases together on this machine). It is also byte-identical on 9 further cases drawn from the same generator with different seeds.
