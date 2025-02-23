Sure! Below is an expanded **README.md** with more emphasis on the **data processing and transformation** while keeping the Power BI design aspects concise.

---

# 🎵 Music Trends Dashboard - Power BI

## 📌 Overview
The **Music Trends Dashboard** is an interactive Power BI visualization designed to explore **music trends, artist popularity, and sentiment analysis** based on song lyrics. The dataset includes metadata about songs, artists, and lyrical sentiment scores derived from **natural language processing (NLP)**.

This project involves significant **data processing**, including **cleaning, transformation, merging datasets, and sentiment analysis**, before visualization in Power BI.

---

## 🛠️ Data Processing Pipeline

### **1️⃣ Raw Datasets**
The project integrates multiple datasets:
- **`dataset.csv`** – Contains general song metadata (artist, song name, genre, popularity, etc.).
- **`song_lyrics.csv`** – Lyrics of songs extracted from external sources.
- **`lyrics_with_sentiment.csv`** – Lyrics processed through sentiment analysis.
- **`artist_nodes.csv` & `artist_edges.csv`** – Graph-based artist collaboration data.

### **2️⃣ Data Cleaning & Standardization**
Performed using **Pandas & NumPy** in Python:
- **Removed Duplicates**: Ensured no duplicate songs exist per artist.
- **Fixed Missing Values**:
  - **Empty Genre fields** replaced with `"Other"`.
  - **Followers & Popularity** converted to numeric and missing values filled with `0`.
  - **Lyrics** with `NA` values dropped from analysis.
- **Standardized Text Fields**:
  - Converted all artist names, song names, and genres to lowercase for uniformity.
  - Trimmed extra spaces for consistency.

### **3️⃣ Genre Formatting**
Genres were stored as lists (e.g., `["pop", "dance pop"]`). The **first genre** was extracted for simplicity using:
```python
import ast
def extract_first_genre(genre):
    if pd.isna(genre) or genre == "[]":
        return "Other"
    try:
        genre_list = ast.literal_eval(genre)
        return genre_list[0] if isinstance(genre_list, list) else genre
    except (ValueError, SyntaxError):
        return genre
df["Genre"] = df["Genre"].apply(extract_first_genre)
```

### **4️⃣ Sentiment Analysis on Lyrics**
- Used **TextBlob** for **polarity-based sentiment classification**:
  - **Polarity > 0** → `"Positive"`
  - **Polarity < 0** → `"Negative"`
  - **Polarity = 0** → `"Neutral"`
- Cleaned lyrics using **regular expressions** to remove special characters and noise.
- Final dataset stored in `lyrics_with_sentiment.csv`:
```python
from textblob import TextBlob
import re
def clean_text(text):
    text = re.sub(r"[^a-zA-Z\s]", "", text)
    return text.lower().strip()

def get_sentiment(text):
    polarity = TextBlob(str(text)).sentiment.polarity
    return "Positive" if polarity > 0 else "Negative" if polarity < 0 else "Neutral"

df_lyrics["clean_lyrics"] = df_lyrics["lyrics"].apply(clean_text)
df_lyrics["Sentiment"] = df_lyrics["clean_lyrics"].apply(get_sentiment)
```

### **5️⃣ Merging Data Sources**
- **Merged lyrics sentiment** with the main dataset on `Artist` and `Song`:
```python
df_final = df_main.merge(df_lyrics[["Artist", "Song", "Sentiment", "lyrics"]], on=["Artist", "Song"], how="left")
```
- **Merged artist collaborations** using `artist_nodes.csv` and `artist_edges.csv`.

### **6️⃣ Exporting Final Dataset**
The cleaned and merged dataset was saved as:
```
powerbi_dataset_final_with_lyrics.csv
```

---

## 📊 Dashboard Structure

### **1️⃣ Summary KPIs**
- **Count of Artists, Songs, and Genres** (Displayed as **card visuals** in Power BI).

### **2️⃣ Sentiment & Genre Analysis**
- **Line Chart** → Popularity trends segmented by **sentiment (Positive/Neutral/Negative)**.
- **Table View** → Number of songs per **genre**, segmented by sentiment type.

### **3️⃣ Artist Popularity**
- **Bar Chart** → Ranks **top artists** by song popularity.

### **4️⃣ Lyrics Sentiment Gauge**
- **Gauge Chart** → Displays **percentage of positive, neutral, or negative songs**.
- Uses **DAX measure** to dynamically calculate sentiment percentages.

### **5️⃣ Interactive Filters**
- **Sentiment Slicer** → Filters dashboard based on **Positive/Neutral/Negative** sentiment.
- **Genre Slicer** → Filters popularity trends by genre.

---

## 🖥️ Power BI Setup & Customization

### **1️⃣ Setup Instructions**
1. **Load the dataset** (`powerbi_dataset_final_with_lyrics.csv`) into Power BI.
2. **Import visuals**:
   - `Gauge Chart`
   - `Table`
   - `Clustered Bar Chart`
   - `Line Chart`
3. **Apply formatting**:
   - **Dark mode theme** (`#000000` background, Spotify-like green `#1DB954` for highlights).
   - **Rounded corners & shadows** for a modern aesthetic.

### **2️⃣ Design Enhancements**
- **Smooth UI Elements**: Soft edges and glow effects.
- **Drill-Through Interactivity**:
  - Clicking on a **genre** filters top artists in that genre.
  - Clicking on an **artist** shows their top songs.

---

## 📂 Files Included

| File Name                           | Description |
|--------------------------------------|-------------|
| `powerbi_dataset_final_with_lyrics.csv` | Final cleaned dataset used in Power BI |
| `Music Trends Dashboard.pbix`       | Power BI dashboard file |
| `data_cleaning.py`                   | Python script for preprocessing |
| `lyrics_with_sentiment.csv`          | Lyrics dataset with sentiment analysis |
| `artist_nodes.csv` & `artist_edges.csv` | Artist collaboration datasets |

---

## 🔮 Future Improvements
- **Drill-through Artist Pages**: Clicking an artist to see **top songs & collaborations**.
- **Spotify Integration**: Embedding **Spotify song previews** into the dashboard.
- **Genre-Specific Sentiment Analysis**: How lyrics differ across **hip-hop vs. pop vs. rock**.

---

## 💡 Final Thoughts
This dashboard effectively analyzes **music trends, sentiment patterns, and artist rankings** in an engaging, **data-driven** way. With **interactive filtering**, a **custom dark UI**, and **rich visual storytelling**, it serves as a **showcase of data visualization & analytics skills**.
