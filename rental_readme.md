# 🏘️ Rental Market Data Analysis

## 📋 Project Overview

A comprehensive data cleaning and analysis project examining rental market trends in census tract areas. This project demonstrates systematic data cleaning techniques, handling of messy real-world data, and preparation for visualization and statistical analysis.

**Project Status:** ✅ Complete  
**Last Updated:** October 2024

---

## 🎯 Objectives

- Clean and standardize 1,400+ records of rental market data
- Handle missing values, formatting inconsistencies, and data type issues
- Prepare data for visualization and statistical analysis
- Create a reproducible data cleaning pipeline

---

## 📊 Dataset Information

### Source
Census rental market data from 2018

### Specifications
- **Records:** 1,401 rows
- **Original Columns:** 11
- **Final Columns:** 7 (after cleaning)
- **Time Period:** 2018
- **Geographic Level:** Census Tract (CTUID)

### Column Descriptions

| Column Name | Data Type | Description |
|------------|-----------|-------------|
| `CTUID` | Float | Census Tract Unique Identifier (e.g., 1.01, 400.00) |
| `YEAR` | Integer | Year of data collection (2018) |
| `DWELLING TYPE` | Integer | Type of residential dwelling (1-5) |
| `BEDROOM TYPE` | Integer | Number of bedrooms (0-3+) |
| `RENTAL UNIT AMOUNT` | Integer | Total number of rental units in the census tract |
| `POPULATION AMOUNT` | Integer | Total population in the census tract |
| `AVERAGE RENT` | Integer | Average monthly rent amount in dollars |

### Data Quality Issues Addressed

**Before Cleaning:**
- ❌ Inconsistent column naming (mixed case, no spaces)
- ❌ Commas in numeric values (e.g., "1,089")
- ❌ Dashes representing missing/zero values ("-")
- ❌ String data types for numeric columns
- ❌ Extra whitespace in column names
- ❌ Unnecessary construction year columns

**After Cleaning:**
- ✅ Standardized uppercase column names with proper spacing
- ✅ Numeric values properly formatted
- ✅ Missing values replaced with 0
- ✅ Correct data types (int64, float64)
- ✅ Focused dataset with 7 essential columns
- ✅ Ready for analysis and visualization

---

## 🧹 Data Cleaning Process

### 1. **Initial Data Loading**
- Loaded CSV file with pandas
- Created independent copy to avoid view warnings
- Initial exploration: 1,401 rows × 11 columns

### 2. **Column Name Standardization**
```python
# Created custom function to:
- Convert all names to uppercase
- Add spaces between words (e.g., "DWELLINGTYPE" → "DWELLING TYPE")
- Replace abbreviations (e.g., "REFYEAR" → "YEAR")
```

### 3. **Column Selection**
- Dropped 4 construction year columns (not needed for analysis)
- Retained 7 core columns for rental market analysis

### 4. **Numeric Data Cleaning**

For each numeric column (`RENTAL UNIT AMOUNT`, `POPULATION AMOUNT`, `AVERAGE RENT`):
- Removed thousands separators (commas)
- Replaced dashes ("-") with 0 to handle missing/suppressed data
- Converted from string (object) to integer type

**Example:**
```
Before: "1,089" (string)
After:  1089 (integer)

Before: "-" (string)  
After:  0 (integer)
```

### 5. **Data Validation**
- Verified no missing values (NaN)
- Checked data types are correct
- Validated numeric ranges are reasonable
- Confirmed no duplicate rows

---

## 🛠️ Technologies & Tools

**Programming Language:**
- Python 3.13.5

**Libraries:**
- `pandas` - Data manipulation and cleaning
- `numpy` - Numerical operations
- `re` - Regular expressions for text processing

**Development Environment:**
- Jupyter Notebook - Interactive development
- VS Code - Code editing
- Git/GitHub - Version control

---

## 📁 Project Structure

```
RENTAL/
├── README.md                           # Project documentation (this file)
├── Rental.ipynb                        # Main Jupyter notebook
├── RentalMarketData_Open.csv          # Original raw data
├── Cleaned_Data.csv                   # Cleaned data (CSV format)
├── Excel_cleaned_data.xlsx            # Cleaned data (Excel format)
└── .gitignore                         # Git ignore file
```

---

## 🚀 How to Run This Project

### Prerequisites
```bash
Python 3.7+
pandas
numpy
openpyxl (for Excel files)
jupyter
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/Gerno05/RENTAL.git
cd RENTAL
```

2. **Install dependencies**
```bash
pip install pandas numpy openpyxl jupyter
```

3. **Launch Jupyter Notebook**
```bash
jupyter notebook Rental.ipynb
```

4. **Run all cells**
- In Jupyter: `Kernel → Restart & Run All`

---

## 📈 Key Insights from Cleaned Data

### Summary Statistics

- **Total Rental Units:** 349,893 units across all census tracts
- **Total Population:** 741,534 people in rental housing
- **Average Rent Range:** $0 - $1,691 per month
- **Census Tracts Analyzed:** 1,401 unique tracts
- **Dwelling Types:** 5 categories
- **Bedroom Types:** 4 categories (0-3+)

### Data Distribution

**Average Rent:**
- Minimum: $0 (likely data suppression)
- Maximum: $1,691
- Most common range: $700 - $1,300

**Rental Unit Amounts:**
- Range: 0 to 815 units per census tract
- Many tracts with small rental markets

---

## 🔮 Future Enhancements

### Analysis & Visualization
- [ ] Create Tableau dashboard for interactive exploration
- [ ] Analyze rent trends by dwelling type
- [ ] Compare rental costs across bedroom types
- [ ] Map rental density by census tract
- [ ] Identify high-cost vs. affordable areas

### Advanced Analytics
- [ ] Statistical analysis of rent distribution
- [ ] Correlation between population and rent
- [ ] Outlier detection and analysis
- [ ] Time series analysis (if multi-year data available)

### Data Expansion
- [ ] Integrate 2019-2024 data for trend analysis
- [ ] Add geographic coordinates for mapping
- [ ] Include neighborhood/city names
- [ ] Merge with demographic data

---

## 🎓 Learning Outcomes

Through this project, I developed and demonstrated:

✅ **Data Cleaning Skills**
- Handling messy real-world data
- String manipulation and regex
- Data type conversions
- Dealing with missing/suppressed values

✅ **Python Programming**
- Pandas DataFrame operations
- Custom functions for repetitive tasks
- Best practices (using `.copy()`, `.loc[]`)
- Code documentation

✅ **Data Quality Management**
- Systematic validation checks
- Before/after comparisons
- Data integrity verification

✅ **Professional Practices**
- Version control with Git/GitHub
- Project documentation
- Reproducible analysis pipeline
- Multiple export formats for different use cases

---

## 💡 Challenges & Solutions

### Challenge 1: SettingWithCopyWarning
**Problem:** Pandas warnings when modifying DataFrame columns  
**Solution:** Used `.copy()` immediately after loading data and `.loc[]` for column assignments

### Challenge 2: Mixed Data Types
**Problem:** Numeric columns stored as strings with commas and dashes  
**Solution:** Systematic string cleaning before type conversion

### Challenge 3: Column Naming Inconsistencies
**Problem:** Original columns had no spaces, mixed case, abbreviations  
**Solution:** Created custom regex-based function to standardize all column names

### Challenge 4: Missing Value Representation
**Problem:** Dashes ("-") used instead of NaN or 0  
**Solution:** Replaced all dashes with 0 after consulting data documentation

---

## 📚 References & Resources

- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Data Cleaning Best Practices](https://www.kaggle.com/learn/data-cleaning)
- [Census Tract Information](https://open.ottawa.ca/datasets/23a8fa1918d9447aa51c2e9a26953e23/explore)

---

## 👤 Author

**George Alaneme**  
IT Student at Carleton University  
Passionate about data analysis, web development, and tech innovation

[![GitHub](https://github.com/Gerno05)


---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to check the [issues page](https://github.com/Gerno05/RENTAL/issues).

---

## ⭐ Show Your Support

Give a ⭐️ if this project helped you learn about data cleaning!

---

## 📧 Contact

Have questions or suggestions? Feel free to reach out!

- GitHub: [@Gerno05](https://github.com/Gerno05)
- Email: geoalams@gmail.com

---

**Note:** This project was created as part of my data analysis portfolio to demonstrate practical data cleaning skills for real-world datasets.
