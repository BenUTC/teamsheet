# Teamsheet

Football match and player predictions on your phone. Data comes free from ESPN's public football feed (no key needed). API-Football is still supported if you ever get a paid key.

- **Match**: pick a fixture (or any two teams) and get win/draw/loss, goals, both teams to score, corners, cards, keeper saves, shots and fouls probabilities, plus per-player chances of committing fouls, being fouled, shots, shots on target, a card and scoring. Each player's last 10 matches, each team's last 10 matches and the last 10 head-to-heads are shown.
- **Best bets** (75% to 90% by default; near-certainties with no worthwhile price are left out), **Longshots** (50% to 74%) and **Feeling lucky** (3 best bets plus 1 or 2 longshots, chosen so no two legs measure the same thing).
- **Day**: pick a date and competitions and get the day's best bets, longshots and a one-leg-per-match Feeling lucky. Pick a past date to see how the picks did.
- When the confirmed team sheets are published (usually about an hour before kick-off), only those players are used.
- **Live matches**: scores and minutes in the fixture list. Opening a live match shows Live stats (shots, shots on target, corners, fouls, cards, saves, possession against the pre-match expectation, plus goals, cards and substitutions) and Live players (fouls, times fouled, shots, shots on target, cards, saves), refreshed every minute, with in-play chances for the next lines.
- **Fractional odds** next to every chance: bookmaker prices where available, otherwise the model's fair odds.
- **Bet slip**: tap + (or a player's chance) to add it. Type in Sky Bet, Paddy Power or Betfair odds to see the value of each leg and the combined price.
- **Acca**: pick the number of teams, the odds you want (for example 5/1) and 1 to 4 days. The app finds the teams to win whose combined odds reach your target with the highest chance of all winning, one team per match, with a reason for each pick. **Acca Freeze** mode (Sky Bet, match result accas of 5 legs or more) picks the freeze team: the least likely winner in the acca, a bigger price that still has a real chance of being in front at some point, so you can freeze it the moment it goes ahead and have it settled as a winner. The other 4 to 6 teams are the strongest favourites. It shows the chance of the acca landing with and without the freeze. The chance of leading at some point was checked against 1,752 matches from 2025/26 and scaled down slightly for underdogs, as prices overrate them a little. Add the whole acca to the bet slip in one tap.
- **Builder**: pick one match or up to 6, the odds you want and the minimum chance for each selection. The app builds two bet builders that reach those odds: Builder 1 has the highest chance of every selection landing, Builder 2 uses different selections. Selections cover result, goals, both teams to score, corners, cards, shots, shots on target and player fouls, times fouled, shots, shots on target, goals, cards and keeper saves, each with its chance, price and recent record. Under **Always include one of each** you tick the types every builder must contain (total goals, team or match corners, team or match cards, player shots, player shots on target, player fouls, player fouled, keeper saves; all ticked by default). The most likely selection of each ticked type goes in first, then more are added to reach your odds. If no selection of a type reaches your minimum chance, the best one from 50% up is used and marked. Once team sheets are out only the starting XI is used; before that, only players at least 80% likely to start. Selections from the same match are priced together from a simulation of the whole match (20,000 runs), so linked selections such as a keeper's saves and the other side's shots on target, or a striker's shots and his team's shots, are not treated as unrelated. The links were measured on 3,057 matches. Checked on 425 finished matches from 20 September to 24 November 2026 (3,039 builders, using only what was known before kick-off and the confirmed team sheets), the builders were expected to land 367 times and landed 376 times; the 21,284 single selections in them were shown at 73.7% and landed 73.6% of the time. Builders of 10 or more selections landed slightly more often than shown. Alongside Builder 1 and Builder 2 there is a **Best chance** builder that ignores the ticked types: fewer selections, less bookmaker margin, a higher chance at the same odds. **Show what each type costs** works out how likely Builder 1 would be without each ticked type's selection, and **Drop it** applies that. Selections that tend to land together are marked **Linked**.
- **Price check**: on every builder and accumulator, type in Sky Bet's price. The app compares it with the fair odds from its own chance and says whether it is value, about fair, the usual bookmaker margin or a poor price, with roughly what it returns per £1 staked over time. The price you type is filled in when you log the bet. Tap Swap on any selection to see alternatives and what the whole builder becomes, then add it to the bet slip.
- **Bets**: log a bet from the bet slip with your stake, odds and bookmaker. The app settles it from the result (void player legs are removed), and shows profit and loss, return on stakes and how often the model's chances came in, by chance band and market. Bets are kept on your phone only; use Copy backup or Download spreadsheet now and then.
- With confirmed line-ups, each player's fouls are nudged by his direct opponent's habits (for example a full-back facing a winger who is fouled a lot).
- Where ESPN carries odds (DraftKings match result and total goals), picks show the price and a Value flag when the model's probability beats it.

## Put it on your Android phone (GitHub Pages, free)

1. On your phone, sign in to github.com (create a free account if needed).
2. Tap **+**, then **New repository**. Name it `teamsheet`, set it to **Public**, tick **Add a README file**, then **Create repository**.
3. In the repository tap **Add file**, then **Upload files**, and choose `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png` and `icon-512.png`. Tap **Commit changes**.
4. Open the repository's **Settings**, then **Pages**. Under **Branch** choose `main` and `/ (root)`, then **Save**.
5. After a minute or two the site is live at `https://YOUR-USERNAME.github.io/teamsheet/`. Open it in Chrome, tap the menu, then **Add to Home screen**.
6. Open the app. It starts on ESPN data straight away; there is nothing to set up.

## Data use

Finished matches are saved on the phone, so each is downloaded once (about 36 KB each). The first analysis in a competition downloads this season and last season, around 15 to 20 MB for the Premier League. A first full-day scan across all 12 competitions is around 170 MB, so do it on Wi-Fi. After that only new matches are fetched.

What stays on the phone is much smaller than what is downloaded: about 1.3 MB for two Premier League seasons, so roughly 15 to 20 MB for all 12 competitions. Settings, then **Storage on this phone**, shows how much is saved and has buttons to remove older seasons or clear everything. Matches more than two seasons old are removed automatically.

ESPN has no referee names or injury lists. Before the team sheets come out (usually an hour before kick-off), predicted line-ups come from recent matches only, so check team news before backing a player.

ESPN does not offer this feed as an official service and could change it without notice. If the app stops loading data, tell Claude what the error says.

## How the models were tested

- Team models: walk-forward backtest on 9,130 Premier League, La Liga, Bundesliga, Serie A and Ligue 1 matches (2021/22 to 2025/26), refitting each week on data available before kick-off. Every market beat the league-average baseline and was well calibrated, including the untouched 2025/26 hold-out season.
- Player models: walk-forward backtest on 1,517 matches of player-level data (StatsBomb open data, 2015/16), again well calibrated.
- Start probabilities for unconfirmed line-ups were recalibrated on the same data.
- Live check on ESPN data: seven match days in October and November 2026, predicted using only data from before each kick-off. 240 best bets were expected to win 89% of the time and won 90%; 180 longshots were expected to win 75% and won 76%.

- Against bookmakers: on 1,752 matches from 2025/26, bookmaker prices predicted match results and over/under 2.5 goals better than the model alone, and the model's apparent value bets on those markets lost 22% of stakes. Goal and result chances are therefore anchored to the prices whenever ESPN has them. Corners, cards, shots, saves, fouls and player markets could not be compared with bookmakers, because no prices were available.

Probabilities are estimates, not guarantees. Help with gambling: BeGambleAware.org, National Gambling Helpline 0808 8020 133.
