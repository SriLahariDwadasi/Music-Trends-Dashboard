# Music Trends Dashboard

An interactive Power BI project that explores the emotional tone, genre trends, and artist popularity in music by analyzing a dataset of over 21,000 songs. This dashboard leverages sentiment analysis and music metadata to uncover patterns in genre positivity, lyrical sentiment, and artist performance across the industry.

## Overview

This project visualizes trends in musical sentiment and genre popularity using a clean, interactive Power BI dashboard. Using sentiment scores derived from song lyrics and enriched metadata on genres and artists, we aim to:

- **Understand Positivity in Music**: Analyze how sentiment varies across genres.
- **Track Genre & Artist Trends**: Identify the most positive and popular categories.
- **Enable Quick Exploration**: Allow dynamic filtering and slicing by artist, genre, and sentiment.

## Features

- **Summary KPIs**:
  - 541 unique artists  
  - 21,040 total songs  
  - 95 distinct genres

- **Genre-Level Sentiment Breakdown**  
  A matrix showing counts of negative, neutral, and positive songs by genre.

- **Popularity by Artist**  
  Bar chart ranking top artists, including Drake, Taylor Swift, and The Weeknd.

- **Sentiment by Genre Chart**  
  Line chart correlating sentiment with genre popularity.

- **Interactive Filters**  
  Slicers for artist and genre to dynamically adjust all visuals.

- **Positive Sentiment Gauge**  
  Radial visualization showing 68.87% of songs in the dataset have positive sentiment.

## Installation & Setup

### Prerequisites

- [Power BI Desktop](https://powerbi.microsoft.com/)
- Python 3.7+ (for preprocessing and sentiment analysis, not required for dashboard viewing)

### Steps to Set Up the Project

1. Clone the repository:

```bash
git clone https://github.com/SriLahariDwadasi/Music-Trends-Dashboard.git
cd Music-Trends-Dashboard
```

2. Open the dashboard:

- Navigate to: `dashboard/Music Trends Dashboard.pbix`
- Open it using Power BI Desktop


## Usage

The dashboard supports both macro and micro exploration of sentiment in music.

- **Overview Page**: Get a snapshot of genre and artist metrics.
- **Drill-Down**: Use slicers to filter by genre (e.g., "dance pop") or artist (e.g., "Johnny Cash").
- **Gauge Chart**: Evaluate the dataset’s positivity score at a glance.
- **Visual Trends**: Analyze sentiment evolution and popularity patterns across genres.

## Data Files

- `powerbi_dataset_final_with_lyrics.csv`: Final merged dataset with sentiment, genre, artist, and popularity info.
- `dashboard/Music Trends Dashboard.pbix`: Power BI file for visualization.
- `notebooks/FinalDataCleaning.ipynb`: Python notebook for preprocessing and sentiment scoring (TextBlob).

## File Structure

```
Music-Trends-Dashboard/
├── data/
│   └── powerbi_dataset_final_with_lyrics.csv
├── notebooks/
│   └── FinalDataCleaning.ipynb
├── dashboard/
│   ├── Music Trends Dashboard.pbix
│   └── PowerBI dashboard.png
├── README.md
└── .gitignore
```

## Dependencies

This project is primarily Power BI-based, but the preprocessing phase used the following:

### Python Packages

- `pandas`
- `textblob`
- `jupyter`

Install via:

```bash
pip install pandas textblob jupyter
```

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch:

```bash
git checkout -b feature-your-feature
```

3. Make your changes and commit:

```bash
git commit -m "Add your feature"
```

4. Push to your branch:

```bash
git push origin feature-your-feature
```

5. Open a Pull Request


## Acknowledgments

- **TextBlob** – for sentiment analysis  
- **Power BI** – for interactive dashboard development  
- **Spotify & Genius Datasets** – for music metadata and lyrics  
- **UC Berkeley** – for academic guidance and feedback

##  About Me

**Sri Lahari Dwadasi**  
Master’s in Analytics @ UC Berkeley | Ex-Novartis | Data Science & Optimization Enthusiast  
📫 [LinkedIn](https://www.linkedin.com/in/sri-lahari-dwadasi) | dwadasi179@gmail.com
