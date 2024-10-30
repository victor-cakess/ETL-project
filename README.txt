# Residential Energy Consumption Data Pipeline

This repository contains a pipeline to process residential energy consumption data from raw extraction to final storage. The project uses a combination of web scraping, PySpark for processing, and Parquet for data storage, with the goal of analyzing energy consumption trends across different U.S. locations.

## Overview

The data used in this project is sourced from the National Renewable Energy Laboratory (NREL). It represents hourly energy consumption profiles for various residential buildings across the U.S. The project is divided into three main processing stages following the Medallion Architecture: 

1. Bronze Layer (Raw Data): Stores the raw data as extracted from the web. This layer retains the original structure, inconsistencies, and errors.
   
2. Silver Layer (Cleaned and Transformed Data): Cleans and standardizes the data, making it ready for further processing.
   
3. Gold Layer (Aggregated and Summarized Data): Aggregates and summarizes the data for analysis and visualization, ready for decision-making.

## Project Workflow

1. **Web Scraping**:
   The data is scraped from a public source using Python’s `requests` and `BeautifulSoup` libraries. The data is downloaded as a compressed ZIP file containing CSVs with detailed energy consumption profiles.

2. **Data Transformation**:
   The CSV files are read into a PySpark DataFrame, where additional information (e.g., state and city) is extracted from the filenames. Columns are cleaned, renamed, and transformed for consistency. The energy data is processed and aggregated by state and date.

3. **Data Storage**:
   The cleaned and aggregated data is stored in Parquet format, optimizing for fast read/write operations. Parquet is a columnar storage format that improves efficiency for future analyses.

## Data Details

The dataset consists of three categories:
- **Base**: General energy consumption data.
- **High**: Represents higher energy consumption, typically for buildings with poor insulation and less efficient systems.
- **Low**: Represents lower energy consumption for more energy-efficient buildings.

The data captures hourly consumption across different locations in the U.S., making it useful for energy efficiency studies and policy development.

## Libraries Used

- PySpark: For large-scale data processing.
- BeautifulSoup and requests: For web scraping.
- Matplotlib and Pandas: For data analysis and visualization.
- Parquet: For efficient data storage.

## How to Run the Project

### Prerequisites

- Python 3.x
- Jupyter Notebook
- PySpark
- BeautifulSoup

### Steps to Run

1. Clone the repository:
   ```
   git clone https://github.com/victorwinx/ETL-project.git
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Run the Jupyter notebook:
   ```
   jupyter notebook Load_analysis.ipynb
   ```

4. The notebook will guide you through the process of extracting, transforming, and storing the data.

## Data Insights

- **Seasonal Energy Trends**:
  Heating consumption increases significantly in the winter months, while cooling consumption peaks during the summer. The data provides insights into the energy efficiency of buildings with varying insulation and HVAC systems.

## Results

The processed data, stored in Parquet format, is ready for further analysis. This allows you to explore trends in energy consumption across different states, cities, and building types, providing a valuable tool for energy planning and sustainability efforts.

## Conclusion

This project demonstrates the power of PySpark and Parquet in handling large datasets, transforming raw energy data into meaningful insights. It showcases how modern data processing pipelines can be used to derive actionable insights from complex datasets.

Feel free to explore the dataset and modify the notebook to fit your analysis needs!
