# Football Match Prediction - English Premier League

This project predicts the winner of football matches in the English Premier League (EPL) using machine learning.

## Project Overview

In this project, we:
- Scrape match data from FBref using requests, BeautifulSoup, and pandas
- Clean the data and prepare it for machine learning
- Make predictions about who will win a match using scikit-learn
- Use rolling averages to improve model accuracy

## Files in This Repository

- `scraping.ipynb` - Web scraping notebook to collect EPL match data from FBref
- `prediction.ipynb` - Machine learning notebook to predict match winners
- `matches.csv` - Scraped match data (generated after running scraping.ipynb)
- `README.md` - This file

## Requirements

```
python>=3.8
pandas
requests
beautifulsoup4
scikit-learn
jupyter
```

## Installation

```bash
pip install pandas requests beautifulsoup4 scikit-learn jupyter
```

## Usage

### Step 1: Scrape the Data

Run the `scraping.ipynb` notebook to collect match data from FBref. This will create a `matches.csv` file with EPL match statistics.

**Note**: Web scraping may take some time and should be done responsibly. Consider rate limiting and checking the website's terms of service.

### Step 2: Train and Test the Model

Run the `prediction.ipynb` notebook to:
- Load and clean the scraped data
- Create features for machine learning
- Train a Random Forest model
- Make predictions on match winners
- Evaluate model accuracy using precision score

## Project Structure

### Data Collection (scraping.ipynb)
- Scrapes Premier League standings data
- Collects shooting statistics and match data for each team
- Combines data across multiple seasons
- Saves to CSV for model training

### Prediction Model (prediction.ipynb)
- Loads match data
- Creates target variable (win/loss)
- Engineers features including:
  - Basic match statistics (goals, shots, possession, etc.)
  - Rolling averages over past matches
- Trains Random Forest Classifier
- Evaluates model performance
- Makes predictions and compares with actual results

## Model Performance

The model achieves approximately 60% precision in predicting match winners. This is improved by:
- Using rolling averages of team statistics
- Combining home and away team predictions
- Feature engineering from historical data

## Acknowledgments

This project is based on the Dataquest tutorial for predicting EPL match winners.

## License

This project is for educational purposes.
