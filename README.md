# COVID-19 Data Visualization Project

## 📊 Overview
This project is a data-driven visualization of COVID-19 trends, built using **Power BI** for interactive dashboards and **SQL** for data extraction, transformation, and analysis.
The goal of this project is to showcase key insights into COVID-19 cases and deaths across different regions.

## 🛠 Tools & Technologies
- **SQL**: Used for data extraction, cleaning, and transformation.
- **Power BI**: Developed interactive visualizations and dashboards.
- **Data Source**: Kaggle.

## 📂 Dataset
- **COVID-19 Case Data**: Daily reported cases and deaths by country.
- **Population Data**: To calculate key metrics like infection rates and vaccination coverage.

## 📈 Key Insights & Visualizations

### 🏥 COVID-19 Cases & Deaths Analysis
![Cases and Deaths Analysis]![Screenshot 2025-03-23 132356](https://github.com/user-attachments/assets/b1d3b609-b740-4d54-ae17-5bbd38427471)
![Screenshot 2025-03-23 132252](https://github.com/user-attachments/assets/4dff103b-d46f-4e62-aeba-46b10108c910)
![Screenshot 2025-03-23 132152](https://github.com/user-attachments/assets/93fe2a18-233e-4989-a2fd-e31100c6ddc3)



### 🌍 Regional Comparisons
![Regional Comparisons]![Screenshot 2025-03-23 133153](https://github.com/user-attachments/assets/8881ce97-8d33-4ba1-8415-6ca3b6e2bfae)
![Screenshot 2025-03-23 132824](https://github.com/user-attachments/assets/5d87ddca-6bd5-44c7-8587-2c0fedd0ae75)
![Screenshot 2025-03-23 132742](https://github.com/user-attachments/assets/3f229d13-09f5-481c-ab4d-30bc679eb260)


## 📌 SQL Queries Used
Some of the SQL queries used in this project include:
```sql
-- --Total cases vs Total deaths

SELECT location, date, total_cases, total_deaths, (total_deaths/total_cases)*100 AS DeathPercentage
FROM Covid_deaths
ORDER BY 1,2;

--Likelihood of contracting covid in United States
SELECT location, date, total_cases, total_deaths, (total_deaths/total_cases)*100 AS DeathPercentage
FROM Covid_deaths
WHERE location LIKE '%states%'
ORDER BY 1,2;

--Percentage of population that got covid
SELECT location, date, population, total_cases, (total_cases/population)*100 AS PercentPopulationInfected
FROM Covid_deaths
WHERE location LIKE '%states%'
ORDER BY 1,2;

--Countries with the highest infection rate compared to population

SELECT location, population, MAX(total_cases) AS HighestInfectionRate, MAX((total_cases/population))*100 AS PercentPopulationInfected
FROM Covid_deaths
--WHERE location LIKE '%states%'
GROUP BY location, population
ORDER BY PercentPopulationInfected DESC;


--Countries with the highest death count per population

SELECT location, MAX(cast(total_deaths as int)) AS TotalDeathCount
FROM Covid_deaths
WHERE continent IS NULL
GROUP BY location
ORDER BY TotalDeathCount DESC;



-- By continent
---Continents with highest death count per population

 SELECT continent, MAX(cast(total_deaths as int)) AS TotalDeathCount
FROM Covid_deaths
WHERE continent IS NOT NULL
GROUP BY continent
ORDER BY TotalDeathCount DESC;


-- Global Numbers


SELECT date, SUM(new_cases) AS TotalCases, SUM(CAST(new_deaths AS INT)) AS TotalDeaths, 
SUM(CAST(new_deaths AS INT))/SUM(new_cases)*100 AS DeathPercentage
FROM Covid_deaths
WHERE continent IS NOT NULL
GROUP BY date
ORDER BY 1,2;


SELECT SUM(new_cases) AS TotalCases, SUM(CAST(new_deaths AS INT)) AS TotalDeaths, 
SUM(CAST(new_deaths AS INT))/SUM(new_cases)*100 AS DeathPercentage
FROM Covid_deaths
WHERE continent IS NOT NULL
ORDER BY 1,2;

```

## 🚀 Power BI Dashboard Features
- **Dynamic Filters**: Users can filter data by country, date range, and case status.
- **Interactive Visuals**: Line charts, bar charts, and maps for easy data exploration.
- **Key Metrics**: Total cases, new cases, deaths and infection rate.


## 🏆 Key Takeaways
- SQL is a powerful tool for handling large datasets and performing data analysis.
- Power BI enables effective storytelling through interactive visualizations.
- Understanding COVID-19 trends through data analysis helps in making informed decisions.

## 📌 Future Improvements
- Automate data refresh using APIs.
- Incorporate machine learning models for predictive analysis.
- Enhance the dashboard with more KPIs and real-time data updates.

## 🔗 Connect with Me
- **LinkedIn**: [Your LinkedIn Profile](https://www.linkedin.com/in/maryndanusa)
- **GitHub**: [Your GitHub Profile](https://github.com/maryndanusa)

---
📢 Feel free to contribute, raise issues, or provide feedback! 🚀

