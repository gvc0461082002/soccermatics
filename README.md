soccermatics
=====

soccermatics provides tools to visualise spatial information from football (soccer) matches using x,y-coordinates of players. There are currently functions to visualise player trajectory paths, heatmaps showing player position frequency, flow fields showing player movement over the pitch, and average position of all players, and pitch lines can be drawn over all plots to provide context.

More functions are planned, but the biggest limitation at the moment is acquiring data. The sample x,y-coordinate data in `tromso` and `tromso_extra` are made available in a [publication by Pettersen et al. (2014)](http://home.ifi.uio.no/paalh/dataset/alfheim/), but I have yet to find any other publicly-available performance datasets - especially passing event, touch event, or shot event data - and access to these data is expensive. I may therefore add a function to simulate event data for the purposes of creating visualisations in the near future.

Use of the name 'soccermatics' kindly permitted by the eponymous book author, [David Sumpter](https://www.bloomsbury.com/uk/soccermatics-9781472924124/).

soccermatics is built on R v3.4.1.

---

#### Installation
You can install `soccermatics` from GitHub in R using [`devtools`](https://github.com/hadley/devtools):

```{r}
if (!require("devtools")) install.packages("devtools")
devtools::install_github("jogall/soccermatics")

library(soccermatics)
```

---

#### Usage and samples

Below are some sample visualisations produced by `soccermetrics`. See the [package manual pdf](https://github.com/JoGall/soccermatics/blob/master/soccermatics.pdf) or the individual help files for each function (e.g. `?soccerHeatmap`) for more information and example code.

<img src="https://user-images.githubusercontent.com/17113779/31055658-1bd30c2a-a6be-11e7-8669-37270197b124.png" width="500">

**Figure 1.** Player heatmap over 90 minutes (player #8; Tromsø IL vs. Anzhi, 2013-11-07). Bins are appromximately 5m x 5m; arrow shows direction of play. Made using `soccerHeatmap()` and `soccerDirection()`.

<img src="https://user-images.githubusercontent.com/17113779/30522405-4311a35c-9bc7-11e7-8d16-a5d5efe154e6.png" width="500">

**Figure 2.** Flow visualisation showing average player movement in different areas of the pitch (player #9; Tromsø IL vs. Strømsgodset, 2013-11-03). Made using `soccerFlow()`.

<img src="https://user-images.githubusercontent.com/17113779/30522404-43106fc8-9bc7-11e7-8f7a-4146aef7bcdc.png" width="500">

**Figure 3.** Average position of each player (Tromsø IL vs. Strømsgodset, 2013-11-03). Arrow shows direction of play. Made using `soccerPositions()` and `soccerDirection()`.

<img src="https://user-images.githubusercontent.com/17113779/31055659-1bd82eee-a6be-11e7-9a99-084e6116e926.png" width="500">

**Figure 4.** Spoke map of all movement events in each pitch bin (player #8; Tromsø IL vs. Anzhi, 2013-11-07). This figure uses a random sample of player movement, but this method is intended to visualise pass or shot event data which are not yet publicly available. Made using `soccerSpokes()`.

<img src="https://user-images.githubusercontent.com/17113779/31047494-a6139168-a603-11e7-9dac-d5a795aff193.png" width="500">

**Figure 5.** Movement path of one player over 120 seconds (player #9; Tromsø IL vs. Strømsgodset, 2013-11-03). Made using `soccerPath()`.

<img src="https://user-images.githubusercontent.com/17113779/31047495-a617407e-a603-11e7-9d41-8e79928175f8.png" width="500">

**Figure 6.** Movement path of 11 players over 60 seconds (Tromsø IL vs. Strømsgodset, 2013-11-03). Made using `soccerPath()`.

<img src="https://user-images.githubusercontent.com/17113779/31047496-a619f148-a603-11e7-8421-c43b13e44f7d.png" width="500">

**Bonus figure.** Jackson Pollock, Number 19. Made using `soccerPath()`.


#### Pitch dimensions
Many performance datasets (e.g. [WhoScored](https://www.whoscored.com/)) provide relative x,y-coordinates on a scale of 0-100. Real-life pitch dimensions (i.e. in metres) are therefore required in order to determine true distances (e.g. pass length, shot distance).

Pitch dimensions of all Premier League teams as listed on Wikipedia can be found in the [pitch_dimensions.csv](https://github.com/JoGall/soccermatics/blob/master/pitch_dimensions.csv) file. In most cases, pitch length and width is listed in both metres and yards, but a conversion has been used where only one unit of measurement has been provided. EPL teams are up-to-date as of the 2016-17 season. The `alt_name` column contains alternative teamname definitions (e.g. as they appear in http://football-data.co.uk). I'd like to expand this list with more teams and welcome any contributions.
