# amazon_bestsellers and other datasets


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

**Merged Datasets**

1. Amazon bestsellers ([link](https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019)) 
2. Conlit ([link](https://figshare.com/articles/dataset/CONLIT/21166171/1?file=37535605))
3. Goodreads best books ever ([link](https://zenodo.org/record/4265096#.ZAgSxOzMKvA))
4. New York Times (NYT) bestsellers ([link](https://www.kaggle.com/datasets/dhruvildave/new-york-times-best-sellers))

**Column Descriptions**


3. `amazon_rating`
4. `amazon_num_reviews`
5. `amazon_price` 
6. `amazon_year`
7. `amazon_genre`
8. `conlit_genre`
9. ``
10. ``
11. ``
12. ``
13. ``
14. ``
15. ``
16. ``
17. ``
18. ``
19. ``
20. ``
21. ``
22. ``
23. `` 

| Column      | Description | Dataset Source |
| ----------- | ----------- |  -----------   |
| 1. `title` | Title of the book (str) | Amazon |
| 2. `amazon_author` | ...        |                |


**Dataset Description**
- Rows: 366 
- Columns: 27 
- Unique books: 222 

---

**Tips For Data Wrangling**
1. Use `ast.literal_eval()` to convert columns with lists (but that are string type) to list type so that you can explode the dataframe (similar to what was done in assignmnent 5) 

```
df['goodreads_genres'] = df.goodreads_genres.apply(lambda s: list(ast.literal_eval(s)))
```

2. Instead of tip 1, read the dataframe from the pickle file (i.e use `pd.read_pickle()` instead of `pd.read_csv()`) - this will convert the column type from a string to a list automatically 

```
df = pd.read_pickle('amazon_conlit_goodreads_nyt.pkl')
```


---

** This dataset is not perfect and there may be some incorrect matches (i.e the paperback version of a book in the amazon bestsellers may have been matched with a hardcover in the goodreads dataset etc., so be wary of columns such as price or publish date)

