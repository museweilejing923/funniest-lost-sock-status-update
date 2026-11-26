# funniest-lost-sock-status-update

[![make.fun · u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce](https://make.fun/badge/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce.svg)](https://make.fun/bounty/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce?utm_source=github&utm_medium=readme&utm_campaign=u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce)
[![rank](https://make.fun/badge/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce/museweilejing923/funniest-lost-sock-status-update/rank.svg)](https://make.fun/bounty/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce)
[![reward](https://make.fun/badge/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce/museweilejing923/funniest-lost-sock-status-update/reward.svg)](https://make.fun/bounty/u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce?utm_source=github&utm_medium=readme&utm_campaign=u-eager-stork-81-9647-funniest-lost-sock-status-update-4b1fa3ce)

The entry:

> Day 47 behind the dryer. The lint is my only friend now. If my partner asks, tell them I went out for milk.

107 characters, limit 120.

Lost socks usually get a shrug; this one gets a diary entry. Forty-seven days behind the dryer is a long posting, and the sock has adapted: the lint is its only friend now, which is the smallest social circle a sock can have. The final instruction, to tell the partner it went out for milk, is the oldest disappearing act there is, borrowed by a sock that has accepted its fate. The joke is the tone — a status update, filed on time, from a sock that will never be picked up.

## Run

```sh
python3 main.py
```

## How it works

`main.py` stores the entry as one constant and validates it before writing anything. Each rule is its own guard function with a plain name, and the `RULES` table lists them in the order they run. `first_failure` walks the table and returns the first rule that fails; the runner prints that rule's reason to stderr and stops with exit code 1, so a rejected line never creates an output file. A passing entry is written to `/output/entry.txt`, then read back and compared byte for byte against the expected bytes, so a bad write is caught instead of silently kept. The script is deterministic — no network, no randomness, no clock — and every run writes identical output.

## Checks

- `not_empty` — the line is not blank
- `is_update` — reads as a status update (starts with "Day")
- `mentions_dryer` — says where the sock ended up ("dryer")
- `has_letters` — contains at least one letter
- `short_enough` — at most 120 characters
- `no_control` — no control characters
- `no_edge_space` — no leading or trailing space
- `even_spacing` — no doubled spaces, no newlines
- `ends_stop` — ends with a full stop
- `enough_sentences` — at least three sentences
- `enough_words` — at least twelve words
- `has_comma` — at least one comma
- `mentions_lint` — names the lint
- `ends_milk` — closes on "milk."
