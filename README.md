import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns# ipl_data.csv
#loading the ipl matches dataset
ipl = pd.read_csv('matches ipl.csv')
#having a glance at the first five records of the dataset
ipl.head()
#getting the frequency of most man of the match awards
ipl['player_of_match'].value_counts()
#getting the frequency of top 10 player win man of the match awards
ipl['player_of_match'].value_counts()[0:10]
#getting the frequency of top 5 player win man of the match awards
ipl['player_of_match'].value_counts()[0:5]
list(ipl['player_of_match'].value_counts()[0:5].keys())
#creating a bar plot
plt.figure(figsize = (7,5))
plt.bar(list(ipl['player_of_match'].value_counts()[0:5].keys()),list(ipl['player_of_match'].value_counts()[0:5]),color = "g")
plt.show()
#getting the frequency of result column
ipl['result'].value_counts()
#getting the frequency of toss winner column
ipl['toss_winner'].value_counts()
#team bating first an win the match
batting_first = ipl[ipl['win_by_runs']!=0]
#looking at the head
batting_first.head()
#making the histogram
plt.figure(figsize = (4,4))
plt.hist(batting_first['win_by_runs'])
plt.title("distribution of run")
plt.xlabel("runs")
plt.ylabel("frequency of batting first")
plt.show()
#find out the number of wins w.s.t each team batting first
batting_first['winner'].value_counts()
batting_first['winner'].value_counts()[0:3]
list(batting_first['winner'].value_counts()[0:3])
list(batting_first['winner'].value_counts()[0:3].keys())
#making a bar plot
plt.figure(figsize = (6,3))
plt.bar(list(batting_first['winner'].value_counts()[0:3].keys()),list(batting_first['winner'].value_counts()[0:3]),color = ["green","orange","yellow"])
plt.show()
#making a pie chart 
plt.figure(figsize = (7,7))
plt.pie(list(batting_first['winner'].value_counts()),labels=list(batting_first['winner'].value_counts().keys()),autopct='%0.1f%%')
plt.show()
#batting second and win the match
batting_second = ipl[ipl['win_by_wickets']!=0]
batting_second.head()
#creating a histogram plot for frequency of wins w.r.to number of wickets
plt.figure(figsize = (7,7))
plt.hist(batting_second['win_by_wickets'],bins = 30)
plt.show()
#finding out the frequency of number of w.r.t each time after batting second
batting_second['winner'].value_counts()
list(batting_second['winner'].value_counts()[0:3])
list(batting_second['winner'].value_counts()[0:3].keys())
#making a bar plot for top three team with most win after batting second
plt.figure(figsize = (7,7))
plt.bar(list(batting_second['winner'].value_counts()[0:3].keys()),(batting_second['winner'].value_counts()[0:3]),color = ['orange','blue','green'])
plt.show()
#making a pie chart for distribution of most wins after betting second
plt.figure(figsize = (7,7))
plt.pie(list(batting_second['winner'].value_counts()),labels=list(batting_second['winner'].value_counts().keys()),autopct='%0.1f%%')
plt.show()
#looking at number of matches played each season
ipl['season'].value_counts()
#looking at the number of matches played in each city
ipl['city'].value_counts()
#find out how many time a team won the match after the winning the toss
import numpy as np
np.sum(ipl['toss_winner'] == ipl['winner'])
393/735
