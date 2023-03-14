# amazon_bestsellers


----

`amazon_bestsellers_df`
**columns:**
- `Name` > `title`
- `Author` > `amazon_author`
- `User Rating` > `amazon_rating`
- `Reviews` > `amazon_num_reviews`
- `Price` > `amazon_price`
- `Year` > `amazon_year`
- `Genre` > `amazon_genre`
+ `title_id`

---

`conlit_meta_df`
**columns:** 
- `Work_Title` > `title_id`
- `Category` > `conlit_category`
- `Language` > `conlit_language`
- `Genre` > `conlit_genre1`
- `Genre2` > `conlit_genre2`
- `Pubdate` > `conlit_pubdate`
- `Author_Last` > `conlit_author_last`
- `Author_First` > `conlit_author_first`
- `Translation` > `conlit_translation`  
- `PubHouse` > `conlit_pubhouse`
- `Prize` > `conlit_prize`
- `WinnerShortlist` > `conlit_winnershortlist`
- `Author_Gender` > `conlit_author_gender`
- `Author_Nationality` > `conlit_author_nationality`
- `goodreads_avg` > `conlit_goodreads_avg`
- `total_ratings` > `conlit_total_ratings`

---

`goodreads_bestbooksever_df`
**columns:** 
- `title` > `title_2`
- `series` > `goodreads_series`
- `author` > `goodreads_author`
- `rating` > `goodreads_rating`
- `language` > `goodreads_language`
- `isbn` > `goodreads_isbn`
- `genres` > `goodreads_genres`
- `edition` > `goodreads_edition`
- `publisher` > `goodreads_publisher`
- `publishDate` > `goodreads_publish_date`
- `firstPublishDate` > `goodreads_first_publish_date`
- `awards` > `goodreads_awards`
- `numRatings` > `goodreads_num_ratings`
- `ratingsByStars` > `goodreads_ratings_by_stars`
- `likedPercent` > `goodreads_liked_percent`
- `price` > `goodreads_price`
+ `title_id`

---

** This dataset is not perfect and there may be some incorrect matches (i.e the paperback version of a book in the amazon bestsellers may have been matched with a hardcover in the goodreads dataset etc., so be wary of columns such as price or publish date)




---

**Merged Datasets**

1. Amazon bestsellers 
2. Conlit 
3. Goodreads 
4. NYT 

**Column Descriptions**
1. `title`
2. `amazon_author`
3. `amazon_rating`
4. `amazon_num_reviews`
5. `amazon_price` 


**Dataset Description**
- Rows: 366 
- Columns: 27 
- Unique books: 222 


**Tips For Data Wrangling**
1. Use `parse_dates=['col1', 'col2']` to convert columns with dates to date type, for example:
```
# read in the dataframe + parse date columns 
df = pd.read_csv('amazon_conlit_goodreads_nyt.csv', parse_dates=['amazon_year', 
                                                                'conlit_pubdate', 
                                                                'goodreads_publish_date', 
                                                                'goodreads_first_publish_date', 
                                                                'nyt_published_date'])
```

2. Use `ast.literal_eval()` to convert columns with lists (but that are string type) to list type so that you can explode the dataframe (similar to what was done in assignmnent 5) 
