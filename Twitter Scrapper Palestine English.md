## Scraping Twitter English Data 

Palestine Media Data


```python
import pandas as pd 
import snscrape.modules.twitter as sntwitter
import csv
```


```python
Query  = "(Palestine OR Gaza) min_faves:10 lang:en until:2022-08-31 since:2022-01-01 -filter:replies"
```


```python
Palestine_A = []
for i,tweet in enumerate(sntwitter.TwitterSearchScraper(Query).get_items()):
    if i>1000000:
        break
    Palestine_A.append([tweet.id, tweet.date,tweet.place,tweet.source,tweet.user.username,tweet.content,tweet.hashtags,tweet.likeCount,tweet.quoteCount,tweet.replyCount,tweet.retweetCount])
    
# Creating a dataframe from the tweets list above
Palestine_Ar = pd.DataFrame(Palestine_A, columns=['Tweet Id', 'DateTime', 'Place', 'Source','Username','Content','hashtags','Likes Number','Quote Number','Reply Number','Retweets Number'])
```


```python
Palestine_Ar.shape
```




    (71693, 11)




```python
Palestine_Ar
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tweet Id</th>
      <th>DateTime</th>
      <th>Place</th>
      <th>Source</th>
      <th>Username</th>
      <th>Content</th>
      <th>hashtags</th>
      <th>Likes Number</th>
      <th>Quote Number</th>
      <th>Reply Number</th>
      <th>Retweets Number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1564764335079137280</td>
      <td>2022-08-30 23:57:44+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>CrazyNormie</td>
      <td>Why does every Corbyn cracker rightly believe ...</td>
      <td>None</td>
      <td>19</td>
      <td>0</td>
      <td>8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1564762949134196737</td>
      <td>2022-08-30 23:52:13+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>aidanaustria</td>
      <td>i’m having a nice time with my friends :) http...</td>
      <td>None</td>
      <td>11</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1564762561865814016</td>
      <td>2022-08-30 23:50:41+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>New_Pal_Golf</td>
      <td>County Champs! Zoe Nelson, Katie Kelley and Ka...</td>
      <td>[NewPalProud]</td>
      <td>45</td>
      <td>1</td>
      <td>0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1564761054680387584</td>
      <td>2022-08-30 23:44:41+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>HonestReporting</td>
      <td>No Jews, No News: The Deadly Gaza Explosion Me...</td>
      <td>None</td>
      <td>28</td>
      <td>3</td>
      <td>1</td>
      <td>17</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1564759653405319173</td>
      <td>2022-08-30 23:39:07+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>NPHSDragons</td>
      <td>Golf:  NP wins county golf title shooting 187,...</td>
      <td>None</td>
      <td>44</td>
      <td>0</td>
      <td>1</td>
      <td>6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>71688</th>
      <td>1477076437651935233</td>
      <td>2022-01-01 00:37:20+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>shathawho</td>
      <td>a photo from 2021 that will always ground me a...</td>
      <td>None</td>
      <td>216</td>
      <td>0</td>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th>71689</th>
      <td>1477073720875311106</td>
      <td>2022-01-01 00:26:32+00:00</td>
      <td>None</td>
      <td>&lt;a href="https://mobile.twitter.com" rel="nofo...</td>
      <td>ninalahoud4paix</td>
      <td>My 2022 wish: for world to embrace the incredi...</td>
      <td>None</td>
      <td>14</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>71690</th>
      <td>1477070281596407808</td>
      <td>2022-01-01 00:12:52+00:00</td>
      <td>None</td>
      <td>&lt;a href="https://mobile.twitter.com" rel="nofo...</td>
      <td>StanleyCohenLaw</td>
      <td>I for one have never bought into the internati...</td>
      <td>None</td>
      <td>197</td>
      <td>4</td>
      <td>12</td>
      <td>59</td>
    </tr>
    <tr>
      <th>71691</th>
      <td>1477069177764544513</td>
      <td>2022-01-01 00:08:29+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>PalmTreesnGz</td>
      <td>I forgot to say that partner and kid made me a...</td>
      <td>[LASD]</td>
      <td>15</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>71692</th>
      <td>1477067807644921862</td>
      <td>2022-01-01 00:03:02+00:00</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>ipsc48</td>
      <td>Happy New Year friends. All we want for 2022 i...</td>
      <td>None</td>
      <td>241</td>
      <td>3</td>
      <td>6</td>
      <td>41</td>
    </tr>
  </tbody>
</table>
<p>71693 rows × 11 columns</p>
</div>




```python
Palestine_Ar['DateTime'] = Palestine_Ar['DateTime'].dt.tz_localize(None)
```


```python
Palestine_Ar
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tweet Id</th>
      <th>DateTime</th>
      <th>Place</th>
      <th>Source</th>
      <th>Username</th>
      <th>Content</th>
      <th>hashtags</th>
      <th>Likes Number</th>
      <th>Quote Number</th>
      <th>Reply Number</th>
      <th>Retweets Number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1564764335079137280</td>
      <td>2022-08-30 23:57:44</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>CrazyNormie</td>
      <td>Why does every Corbyn cracker rightly believe ...</td>
      <td>None</td>
      <td>19</td>
      <td>0</td>
      <td>8</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1564762949134196737</td>
      <td>2022-08-30 23:52:13</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>aidanaustria</td>
      <td>i’m having a nice time with my friends :) http...</td>
      <td>None</td>
      <td>11</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1564762561865814016</td>
      <td>2022-08-30 23:50:41</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>New_Pal_Golf</td>
      <td>County Champs! Zoe Nelson, Katie Kelley and Ka...</td>
      <td>[NewPalProud]</td>
      <td>45</td>
      <td>1</td>
      <td>0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1564761054680387584</td>
      <td>2022-08-30 23:44:41</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>HonestReporting</td>
      <td>No Jews, No News: The Deadly Gaza Explosion Me...</td>
      <td>None</td>
      <td>28</td>
      <td>3</td>
      <td>1</td>
      <td>17</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1564759653405319173</td>
      <td>2022-08-30 23:39:07</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>NPHSDragons</td>
      <td>Golf:  NP wins county golf title shooting 187,...</td>
      <td>None</td>
      <td>44</td>
      <td>0</td>
      <td>1</td>
      <td>6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>71688</th>
      <td>1477076437651935233</td>
      <td>2022-01-01 00:37:20</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>shathawho</td>
      <td>a photo from 2021 that will always ground me a...</td>
      <td>None</td>
      <td>216</td>
      <td>0</td>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th>71689</th>
      <td>1477073720875311106</td>
      <td>2022-01-01 00:26:32</td>
      <td>None</td>
      <td>&lt;a href="https://mobile.twitter.com" rel="nofo...</td>
      <td>ninalahoud4paix</td>
      <td>My 2022 wish: for world to embrace the incredi...</td>
      <td>None</td>
      <td>14</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>71690</th>
      <td>1477070281596407808</td>
      <td>2022-01-01 00:12:52</td>
      <td>None</td>
      <td>&lt;a href="https://mobile.twitter.com" rel="nofo...</td>
      <td>StanleyCohenLaw</td>
      <td>I for one have never bought into the internati...</td>
      <td>None</td>
      <td>197</td>
      <td>4</td>
      <td>12</td>
      <td>59</td>
    </tr>
    <tr>
      <th>71691</th>
      <td>1477069177764544513</td>
      <td>2022-01-01 00:08:29</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/iphone" r...</td>
      <td>PalmTreesnGz</td>
      <td>I forgot to say that partner and kid made me a...</td>
      <td>[LASD]</td>
      <td>15</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>71692</th>
      <td>1477067807644921862</td>
      <td>2022-01-01 00:03:02</td>
      <td>None</td>
      <td>&lt;a href="http://twitter.com/download/android" ...</td>
      <td>ipsc48</td>
      <td>Happy New Year friends. All we want for 2022 i...</td>
      <td>None</td>
      <td>241</td>
      <td>3</td>
      <td>6</td>
      <td>41</td>
    </tr>
  </tbody>
</table>
<p>71693 rows × 11 columns</p>
</div>




```python
Palestine_Ar.to_excel("E:\\Work\\Data Analysis Projects\\Palestinian Project\\Twitter Scraped Data\\Palestine_Ar Data1.xlsx",index=False)
```

### By :
Madjid Erroukrma
### Contact : 
madjidmain@gmail.com
