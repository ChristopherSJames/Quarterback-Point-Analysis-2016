# QB point analysis
## by Christopher James


## Dataset

This dataset contains statistics of NFL quarterbacks (qbs) from the 2016 season. It also contains a dataset with statistics on rushing during the same games.

pass-2016-wrangle
The gather phase of the project was done in the following steps: I loaded the csv file 'pass-2016.csv' into a dataframe called df_original. I then made a copy called df for wrangling purposes. 
The cleaning portion of the project was done in the following steps: I found that there was extra data in the 'Player' column that appeared to be some sort of id. I also found asterisks in some of the rows as well, with no discernable meaning. In both cases, I removed the data from the column. I found that there were multilpe data points in the column 'QBrec'. I out each of these data points into their own column, the three being called 'QBwin',  'QBlose', and 'QBtie'. I found that there was data in the 'Pos' column that contained the same data in both lowercase and uppercase form. I converted the entire column to uppercase for consistency.
Finally, I put the cleaned dataframe into a csv file called 'pass-2016-master'. During the analysis portion, I did additional cleaning. I started by removing all rows that were not qbs and also had less than 100 pass attempts in a season.
I then created a row that contains the ratio of wins to losses per qb. Finally, I added rushing stats from the other dataset (more on that below).

run-2016-wrangle
The gather phase of the project was done in the following steps: I loaded the csv file 'Career_Stats_Rushing.csv'into a dataframe called df_original. I then made a copy called df for wrangling purposes. 
The cleaning portion of the project was done in the following steps: I found that the symbol '--' was used to indicate missing data. I changed this to NaN. I found that The columns 'Rushing Attempts', 'Rushing Yards', 'Yards Per Carry', 'Rushing Yards Per Game', 'Rushing TDs', 'Longest Rushing Run', 'Rushing First Downs', 'Percentage of Rushing First Downs', 'Rushing More Than 20 Yards', 'Rushing More Than 40 Yards', and 'Fumbles' were of the data type 'object'. I changed this to float through the to_numeric function. I found that all of the colum names that had multiple words also had spaces. I changed all of the spaces to underscores.  I found that one row had a value in the column  'Percentage of Rushing First Downs' was greater than 100. Since this is a percentage column, this was in error. I went to ESPN's website (linked on page), and found that the error was commited there too. Since I could not validate any of the data for this player, I deleted the entire row.
Finally, I put the cleaned dataframe into a csv file called 'Career_Stats_Rushing_master.csv'. During the analysis portion, I did additional cleaning. I started removing all rows that were of years other than 2016.
I then changed all the team names to match the symbols in the other dataset. Finally, I grouped all the player statistics into team statistics in preperation for moving the select data to the other dataset.



## Summary of Findings

Univariate Findings

The distribution of completion percentage ranges from 52% to 72%. A majority of the players tend to fall to the center of the distribution. The distribution of average yards per attempt ranges from 5.25 to 9.25, with the majority of the players falling to the center of the distribution. Almost half of all players are in the 7.0 and 7.75 bins. The distribution of average yards per catch ranges from 9.5 to 13.5. The majority of players range from 10.5 to 12.75. The distribution of average yards per game ranges from 145 to 334. The majority of players range from 224 to 284. The distribution of quarterback rating ranges from 16 to 76. The majority of players range on the higher end from 46 to 66. The distribution of quarterback win percentage ranges from 0% to 100%. The majority of players range from 20% to 70%.

Bivariate Findings

There appears to be a moderate positive coorelation between touchdown percentage and completion percentage. This coorelation weakens at moderate levels before climbing again, suggesting that there are several quarterbacks who have high completion percentages yet fail to score many touchdowns. There is a strong positive coorelation between touchdown percantage and yards per pass attempt. Note the groups of quarterbacks who have very similar stats. There is a moderate positive coorelation between touchdown percentage and yards per catch. An interesting find is the small groups of quarterbacks that have similar stats. There is a strong positive coorelation between touchdown percentage and yards per game. It could be that quarterbacks who are higher skilled are allowed to throw the ball more. There is a strong positive coorelation between touchdown percentage and quarterback rating. Note that quarterback rating is a more complete rating that encompasses everything a quarterback does. Things like foot work, throwing receivers open, etc. There is a moderate positive coorelation between touchdown percentage and quarterback win percentage. This is not surprising given that there are many ways to score a touchdown.

Univariate Findings

There is a strong positive coorelation between touchdown percentage, completion percentage, and yards per pass attempt. At first glance, it might seem surprising that quarterbacks with longer average yards per attempt would also have a higher completion percentage, because it would seem that shorter passes are easier to complete. It is important to note, however, that yards per attempt includes the amount of yards gained after the catch as well as the pass length. So, higher yards per attempt does not necessarily mean longer passes. There is little coorelation between touchdown percentage, completion percentage, and yards per catch. The coorelation between touchdown percentage and completion percentage is strong, but yards per catch is all over the place. There is a strong coorelation between touchdown percentage, completion percentage, and yards per game. This once againa rouses the suspicion that quarterbacks that are higher skilled get to throw more passes. There is a strong coorelation between touchdown percentage, yards per pass attempt, and yards per catch. This is an unsurprising finding, given the direct connection between the last 2 stats. There appears to be a moderate coorelation between yards per game and yards per pass attempt. This indicates that throwing more passes that are less productive does not lead to a greater percentage of such passes being touchdowns. It also does not lead to more yards per game. That could be becuase less successful quarterbacks are not called upon to throw as much. There is a moderate coorelation between touchdown percentage, completion percentage, and quarterback win percentage. There are teams that do not have the flashy plays that can score as many points as those who do. That translates into quarterbacks not needing to have as many throws be touchdowns. This is often aided by a top running game.