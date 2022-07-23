# In This project will descripe how to scrape movie's information of top 250 movies on IMDB website:

## Extracted Information:
This code will extract the below information using Python Code and will save the output in CSV file:
1. Movie Name
2. Movie Rating
3. Year
4. Link
	
## load needed libraries

	import requests
	from bs4 import BeautifulSoup
	import pandas as pd

## Link of IMDB website:
https://www.imdb.com/chart/top/

## Make a request to a web page, to get the HTML content
	url = requests.get('https://www.imdb.com/chart/top/')

## Parse HTML Code With Beautiful Soup
	soup = BeautifulSoup(url.content,'html.parser')

## Finding needed information by inspecting its HTML tag/ID:
## Creating empty DataFrame Headers:
	df = pd.DataFrame(columns=['movie_name','rating','year','link'])

## Creating For Loop to iterate over each movie's content and scrape the needed info. and save it in a list.
	for movie in movies:
	    movie_name = movie.find('td',class_="titleColumn").find('a').text
	    rating = movie.find('td',class_="ratingColumn imdbRating").text.strip()
	    year = movie.find('td',class_="titleColumn").find('span',class_="secondaryInfo").text.replace('(','').replace(')','')
	    link = 'http://imdb.com'+(movie.find('a').get('href'))
    
## append the extracted information to the created dataframe
	df = df.append({'movie_name':movie_name,'rating':rating,'year':year,'link':link},ignore_index=True)

## Save the output to CSV file in your local machine path:
	df.to_csv('your local machine path/csv file name',index=False)

## Output
### DataFrame output:
![image](https://user-images.githubusercontent.com/109844538/180596413-6d74d6b1-75a9-4412-b5e5-edbbf1574c44.png)

### Newly Ceated CSV file:
![image](https://user-images.githubusercontent.com/109844538/180596463-dc354b3a-feaa-47d6-9088-7a59337a6184.png)

