# Amazon bestselling books and other datasets

Dataset for use as part of the DSCI 320 final visualization project. University of British Columbia, 2023. 

Please see the `data/` folder to download the following files: 
- [`amazon_conlit_goodreads_nyt.csv`](https://github.com/shlrley/amazon_bestsellers/blob/main/data/amazon_conlit_goodreads_nyt.csv)
- [`amazon_conlit_goodreads_nyt.pkl`](https://github.com/shlrley/amazon_bestsellers/blob/main/data/amazon_conlit_goodreads_nyt.pkl)

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
| 9. `conlit_pubdate` | Original publication date of the book | Conlit | `Pubdate` | 
| 10. `conlit_author_gender` | Gender of the author (M/F/O) (str) | Conlit | `Author_Gender` | 
| 11. `conlit_author_nationality` | Nationality of the author (str) | Conlit | `Author_Nationality` | 
| 12. `conlit_total_ratings` | Total number of ratings of the book on Goodreads as of May 23, 2022 (int) | Conlit | `total_ratings` | 
| 13. `goodreads_rating` | Global Goodreads rating (float) | Goodreads | `rating` | 
| 14. `goodreads_series` | Series name (str) | Goodreads | `series` | 
| 15. `goodreads_genres` | Genre(s) of the book (list[str]) | Goodreads | `genres` | 
| 16. `goodreads_edition` | Type of edition (str) | Goodreads | `edition` | 
| 17. `goodreads_publisher` | Publisher of book (str) | Goodreads | `publisher` | 
| 18. `goodreads_publish_date` | Publication date | Goodreads | `publishDate` | 
| 19. `goodreads_first_publish_date` | Publication date of first edition | Goodreads | `firstPublishDate` | 
| 20. `goodreads_awards` | List of awards received by the book (list[str]) | Goodreads | `awards` | 
| 21. `goodreads_num_ratings` | Number of total ratings on Goodreads (int) | Goodreads | `numRatings` | 
| 22. `goodreads_likedPercent` | Percent of ratings over 2 stars on Goodreads (float) | Goodreads | `likedPercent` | 
| 23. `goodreads_price` | Price of the book (extracted from Iberibro) (float) | Goodreads | `price` | 
| 24. `nyt_published_date` | Date the list was published | NYT | `published_date` | 
| 25. `nyt_list_name_encoded` | Category of the list (str) | NYT | `list_name_encoded` | 
| 26. `nyt_price` | Price of the book (float) | NYT | `price` | 
| 27. `nyt_weeks_on_list` | Number of weeks the book was on the best sellers list (int) | NYT | `weeks_on_list` | 


### **Final Dataset Description**
- Rows: 366 
- Columns: 27 
- Unique books: 222 

---

### **Tips For Data Wrangling**

The columns `goodreads_genres` and `goodreads_awards` contain lists of strings, but unfortunately if you load the data from the .csv file the list will be of a string type. For example: 
- "['fantasy', 'science-fiction']" instead of 
- ['fantasy', 'science-fiction']

To fix this, you could try either of the following: 

1. Use `ast.literal_eval()` to convert columns with lists (but that are string type) to list type so that you can explode the dataframe (similar to what was done in assignmnent 5) 

```
df['goodreads_genres'] = df.goodreads_genres.apply(lambda s: list(ast.literal_eval(s)))
```

2. OR instead of tip 1, you can read the dataframe from the pickle file (i.e use `pd.read_pickle()` instead of `pd.read_csv()`) - this will convert the column type from a string to a list automatically 

```
df = pd.read_pickle('amazon_conlit_goodreads_nyt.pkl')
```

---

**This dataset is not perfect and there may be some incorrect matches (i.e the paperback version of a book in the amazon bestsellers may have been matched with a hardcover in the goodreads dataset etc., so be wary of columns such as price or publish date)

