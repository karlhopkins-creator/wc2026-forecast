# World Cup 2026 — Living Forecast

A single-page Monte Carlo model for the 2026 FIFA World Cup. Enter real results and every team's probability of advancing and winning updates live. It handles the 48-team format, including the eight best third-placed qualifiers and the official Round-of-32 slotting.

## Files

- `index.html` — the app. Open it or host it.
- `results.json` — the live results. Edit this as matches finish; the page reads it on load.

## Updating results during the tournament

Edit `results.json` in GitHub (open the file, click the pencil, commit). GitHub Pages redeploys in about a minute and every visitor sees the new odds. No need to touch `index.html`.

### Group games

Add a line under `"groups"` using the fixture name exactly as listed below, with the score as `"home-away"`:

```json
{
  "groups": {
    "Mexico v South Africa": "2-1",
    "Spain v Cape Verde": "3-0"
  },
  "knockout": {}
}
```

Leave a fixture out and the model simulates it. Mind the commas: every line except the last inside the block needs a trailing comma.

### Exact group fixture keys (72)

**Group A**
```
Mexico v South Africa
South Korea v Czechia
Czechia v South Africa
Mexico v South Korea
Czechia v Mexico
South Africa v South Korea
```

**Group B**
```
Canada v Bosnia-Herzegovina
Qatar v Switzerland
Switzerland v Bosnia-Herzegovina
Canada v Qatar
Switzerland v Canada
Bosnia-Herzegovina v Qatar
```

**Group C**
```
Brazil v Morocco
Haiti v Scotland
Scotland v Morocco
Brazil v Haiti
Scotland v Brazil
Morocco v Haiti
```

**Group D**
```
USA v Paraguay
Australia v Turkey
USA v Australia
Turkey v Paraguay
Turkey v USA
Paraguay v Australia
```

**Group E**
```
Germany v Curacao
Ivory Coast v Ecuador
Germany v Ivory Coast
Ecuador v Curacao
Ecuador v Germany
Curacao v Ivory Coast
```

**Group F**
```
Netherlands v Japan
Sweden v Tunisia
Netherlands v Sweden
Tunisia v Japan
Japan v Sweden
Tunisia v Netherlands
```

**Group G**
```
Iran v New Zealand
Belgium v Egypt
Belgium v Iran
New Zealand v Egypt
Egypt v Iran
New Zealand v Belgium
```

**Group H**
```
Spain v Cape Verde
Saudi Arabia v Uruguay
Spain v Saudi Arabia
Uruguay v Cape Verde
Cape Verde v Saudi Arabia
Uruguay v Spain
```

**Group I**
```
France v Senegal
Iraq v Norway
France v Iraq
Norway v Senegal
Norway v France
Senegal v Iraq
```

**Group J**
```
Argentina v Algeria
Austria v Jordan
Argentina v Austria
Jordan v Algeria
Algeria v Austria
Jordan v Argentina
```

**Group K**
```
Portugal v DR Congo
Uzbekistan v Colombia
Portugal v Uzbekistan
Colombia v DR Congo
Colombia v Portugal
DR Congo v Uzbekistan
```

**Group L**
```
England v Croatia
Ghana v Panama
England v Ghana
Panama v Croatia
Panama v England
Croatia v Ghana
```

### Knockout games

Knockout fixtures aren't known until the groups finish, so these are keyed by match number (shown as M73, M74… in the app). Put the **winning team's name** as the value:

```json
{
  "groups": { ... all 72 entered ... },
  "knockout": {
    "73": "Switzerland",
    "89": "Spain",
    "104": "France"
  }
}
```

Match numbers: R32 = M73–M88 · R16 = M89–M96 · Quarter-finals = M97–M100 · Semi-finals = M101–M102 · Final = M104. The app shows each tie's number, so read it off there.

## Before launch

Refresh the 48 Elo ratings inside `index.html` (the `TEAMS` object near the top of the script) from eloratings.net. Ratings are the input that drives the forecast.
