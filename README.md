# amazon_bestsellers and other datasets

Dataset for use as part of the DSCI 320 final visualization project. University of British Columbia, 2023. 

---

### **Merged Datasets**

1. [Amazon bestsellers](https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019) 
   - "Dataset on Amazon's Top 50 bestselling books from 2009 to 2019. Contains 550 books, data has been categorized into fiction and non-fiction using Goodreads."  
2. [Conlit](https://figshare.com/articles/dataset/CONLIT/21166171/1?file=37535605)
   - "This dataset includes derived data on a collection of ca. 2,700 books in English published between 2001-2021 and spanning twelve different genres."
3. [Goodreads best books ever](https://zenodo.org/record/4265096#.ZAgSxOzMKvA)
   - "The dataset contains 25 variables and 52478 records corresponding to books on the GoodReads Best Books Ever list (the larges list on the site)."
4. [New York Times (NYT) bestsellers](https://www.kaggle.com/datasets/dhruvildave/new-york-times-best-sellers)
   - "The data contains Best Sellers List published by The New York Times every Sunday. The temporal range is from 03-Jan-2010 to 29-Dec-2019 which makes it a whole decade of data. Each week, 5 books are named as best sellers for each category."

### **Column Descriptions**

| Column      | Description | Dataset Source | Column Name in Original Dataset |
| ----------- | ----------- |  -----------   |  -----------   |
| 1. `title` | Title of the book (str) | Amazon | `Name` | 
| 2. `amazon_author` | Author (first and last name) of the book (str) | Amazon | `Author` | 
| 3. `amazon_rating` | Rating of the book given by Amazon user on a scale of 1 to 5 (float) | Amazon | `User Rating` | 
| 4. `amazon_num_reviews` | Number of written reviews of the book given on Amazon (int) | Amazon | `Reviews` | 
| 5. `amazon_price`  | Price of the book as of October 13, 2020 (int) | Amazon | `Price` | 
| 6. `amazon_year` | Year the book was ranked on the bestsellers list | Amazon | `Year` | 
| 7. `amazon_genre` | Whether the book is fiction or non-fiction (str) | Amazon | `Genre` | 
| 8. `conlit_genre` | Genre of the book, lists 1 genre out of 12 categories (str) | Conlit | `Genre` | 
| 9. `conlit_pubdate` |  | Conlit | `Pubdate` | 
| 10. `conlit_author_gender` |  | Conlit | `Author_Gender` | 
| 11. `conlit_author_nationality` |  | Conlit | `Author_Nationality` | 
| 12. `conlit_total_ratings` |  | Conlit | `total_ratings` | 
| 13. `goodreads_rating` |  | Goodreads | `rating` | 
| 14. `goodreads_series` |  | Goodreads | `series` | 
| 15. `goodreads_genres` |  | Goodreads | `genres` | 
| 16. `goodreads_edition` |  | Goodreads | `edition` | 
| 17. `goodreads_publisher` |  | Goodreads | `publisher` | 
| 18. `goodreads_publish_date` |  | Goodreads | `publishDate` | 
| 19. `goodreads_first_publish_date` |  | Goodreads | `firstPublishDate` | 
| 20. `goodreads_awards` |  | Goodreads | `awards` | 
| 21. `goodreads_num_ratings` |  | Goodreads | `numRatings` | 
| 22. `goodreads_likedPercent` |  | Goodreads | `likedPercent` | 
| 23. `goodreads_price` |  | Goodreads | `price` | 
| 24. `nyt_published_date` |  | NYT | `published_date` | 
| 25. `nyt_list_name_encoded` |  | NYT | `list_name_encoded` | 
| 26. `nyt_price` |  | NYT | `price` | 
| 27. `nyt_weeks_on_list` |  | NYT | `weeks_on_list` | 


### **Final Dataset Description**
- Rows: 366 
- Columns: 27 
- Unique books: 222 

---

### **Tips For Data Wrangling**
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

