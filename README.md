# amazon_bestsellers


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
- `title` 
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
