# Setup and Usage Guide

## Quick Start

Follow these steps to set up and run the Football Match Predictor project:

### 1. Clone or Download the Repository

```bash
git clone <your-repo-url>
cd football_match_predictor
```

### 2. Install Dependencies

Make sure you have Python 3.8 or higher installed, then:

```bash
pip install -r requirements.txt
```

Or install packages individually:
```bash
pip install pandas requests beautifulsoup4 scikit-learn jupyter lxml html5lib
```

### 3. Collect Data (Option A: Scrape Fresh Data)

**Important Notes:**
- Web scraping takes time (2-4 hours depending on seasons)
- Be respectful of FBref's servers - the code includes delays
- Consider FBref's terms of service
- The website structure may change, requiring code updates

Run the scraping notebook:
```bash
jupyter notebook scraping.ipynb
```

Run all cells to scrape data from FBref. This will create `matches.csv`.

### 3. Collect Data (Option B: Use Sample Data)

If you have issues with scraping or want to test quickly, you can:
1. Download the original matches.csv from the GitHub repository
2. Or use data from football-data.co.uk (requires format adjustments)

### 4. Train and Test the Model

Once you have `matches.csv`, open the prediction notebook:
```bash
jupyter notebook prediction.ipynb
```

Run all cells to:
- Load and clean the data
- Train the Random Forest model
- Make predictions
- Evaluate accuracy and precision

## Troubleshooting

### Web Scraping Issues

**Problem:** Getting 403 Forbidden or blocked by website
**Solution:** 
- Add longer delays between requests (increase `time.sleep()`)
- Use a User-Agent header in your requests
- Consider using the website's API if available

**Problem:** Tables not found or parsing errors
**Solution:**
- The website HTML structure may have changed
- Inspect the webpage and update the selectors
- Check if table IDs or classes have changed

### Data Issues

**Problem:** Missing or NaN values in the data
**Solution:**
- The rolling averages code handles this with `dropna()`
- Check which columns have missing data: `matches.isnull().sum()`
- You may need to fill or drop missing values

**Problem:** Different team names between sources
**Solution:**
- Use the `map_values` dictionary in the prediction notebook
- Add more team name mappings as needed

### Model Performance

**Problem:** Low precision scores
**Solution:**
- Try different train/test split dates
- Adjust Random Forest parameters (n_estimators, min_samples_split)
- Add more features or adjust rolling window size
- Collect more seasons of data

## Project Structure

```
football_match_predictor/
│
├── README.md              # Project overview
├── SETUP_GUIDE.md        # This file
├── requirements.txt      # Python dependencies
├── .gitignore           # Git ignore rules
│
├── scraping.ipynb       # Data collection notebook
├── prediction.ipynb     # ML model notebook
│
└── matches.csv          # Scraped data (generated after scraping)
```

## Tips for Success

1. **Start with Recent Data**: Scrape 2-3 recent seasons first to test
2. **Monitor Your Scraping**: Watch for errors during the scraping process
3. **Save Intermediate Results**: Consider saving data after each season
4. **Experiment with Features**: Try adding new rolling averages or features
5. **Version Control**: Commit your code to GitHub regularly

## Next Steps After Basic Setup

Once you have the basic project working:

1. **Improve the Model**:
   - Add more features (possession, passes, corners, etc.)
   - Try different ML algorithms (Gradient Boosting, XGBoost)
   - Tune hyperparameters using GridSearch

2. **Enhance Visualizations**:
   - Add plots showing prediction accuracy over time
   - Visualize feature importance
   - Create confusion matrices

3. **Deploy the Model**:
   - Create a simple web interface with Flask/Streamlit
   - Set up automated predictions for upcoming matches
   - Schedule regular data updates

4. **Portfolio Enhancement**:
   - Write a detailed blog post about your process
   - Add visualizations and insights to your README
   - Document challenges you overcame

## Resources

- [FBref](https://fbref.com/) - Source for football statistics
- [Scikit-learn Documentation](https://scikit-learn.org/) - ML library docs
- [Pandas Documentation](https://pandas.pydata.org/) - Data manipulation
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - Web scraping

## Getting Help

If you encounter issues:
1. Check the error message carefully
2. Search for similar issues on Stack Overflow
3. Review the Dataquest tutorial video
4. Check if FBref's website structure has changed

## License

This project is for educational purposes. Please respect FBref's terms of service when scraping data.
