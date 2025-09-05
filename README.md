# One Piece Character Episodes Scraper

A Python web scraping tool that extracts character appearances from One Piece episodes using the One Piece Fandom Wiki. This project creates a dataset of which characters appear in which episodes.

## 🎯 Features

- Scrapes character data from One Piece Fandom Wiki
- Extracts "Characters in Order of Appearance" from each episode
- Handles rate limiting with built-in delays
- Cleans and processes character names (removes annotations like flashbacks)
- Exports data to CSV format for further analysis
- Configurable episode range (currently supports up to episode 1141+)

## 📋 Requirements

- Python 
- Internet connection for web scraping
- Required packages (requirements.txt)

## 🚀 Installation

1. Clone this repository:
```bash
git clone https://github.com/Fth87/scrapping-one-piece-character.git
cd onepiece-character-scraper
```
Or if you using SSH

```bash
git clone git@github.com:Fth87/scrapping-one-piece-character.git
cd onepiece-character-scraper
```



2. Create a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

## 💻 Usage

### Using Jupyter Notebook

1. Start Jupyter Notebook:
```bash
jupyter notebook
```

2. Open `onepiece.ipynb` and run the cells sequentially

3. Modify the `max_episodes` variable to set how many episodes you want to scrape:
```python
max_episodes = 100  # Change this number as needed
```

### Running as Python Script

You can also convert the notebook cells to a standalone Python script:

```python
import requests
from bs4 import BeautifulSoup
import time
from collections import defaultdict
import csv

# Run the scraping process
# (Copy the code from notebook cells)
```

## 📊 Output

The scraper generates a CSV file (`onepiece_characters.csv`) with the following structure:

| Character | Episodes |
|-----------|----------|
| Monkey D. Luffy | 1,2,3,4,5,... |
| Roronoa Zoro | 2,3,4,5,... |
| Nami | 1,8,9,10,... |

## ⚙️ Configuration

### Episode Range
Modify the `max_episodes` variable to control how many episodes to scrape:
```python
max_episodes = 1141  # Current maximum available episodes
```

### Rate Limiting
The scraper includes a 1-second delay between requests to be respectful to the server:
```python
time.sleep(1)  # Adjust if needed
```

### Headers
Custom headers are used to avoid blocking:
```python
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36"
}
```

## 🛠️ How It Works

1. **Episode URL Generation**: Constructs URLs for each One Piece episode on Fandom Wiki
2. **HTML Parsing**: Uses BeautifulSoup to parse the episode pages
3. **Character Extraction**: Finds the "Characters in Order of Appearance" section
4. **Data Cleaning**: Removes annotations and cleans character names
5. **Data Aggregation**: Collects all episodes where each character appears
6. **CSV Export**: Saves the final dataset in CSV format

## 📝 Data Structure

The scraper creates a dictionary structure:
```python
character_episodes = {
    "Monkey D. Luffy": [1, 2, 3, 4, 5, ...],
    "Roronoa Zoro": [2, 3, 4, 5, ...],
    "Nami": [1, 8, 9, 10, ...]
}
```

## 🔧 Troubleshooting

### Common Issues

1. **Network Errors**: Check your internet connection and try again
2. **Missing Data**: Some episodes might not have the expected HTML structure
3. **Rate Limiting**: If you get blocked, increase the delay between requests

### Error Messages

- `"No 'Characters in Order of Appearance' section found"`: Episode page structure might be different
- `"No character list found"`: The HTML structure has changed or is missing
- `"Error fetching Episode X"`: Network or HTTP error occurred

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📞 Support

If you encounter any issues or have questions, please:
1. Check the troubleshooting section
2. Review the code comments
3. Open an issue on GitHub

---

**Note**: This scraper is designed for research and educational purposes. Please be respectful when using it and follow the website's robots.txt and terms of service.