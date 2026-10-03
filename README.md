# PakWheels used car listings, September 2026

Analysis of used car adverts scraped from PakWheels on 28 September 2026: make, model, variant, year, asking price, mileage, fuel type, transmission, engine size and city.

Source: https://www.kaggle.com/datasets/danishjmeo/pakistan-used-cars-dataset-prices-and-specs-2026

Prices are asking prices from adverts, not sale prices.

## Headline numbers

- 10,589 adverts and 17 columns in the original file; 10,586 adverts after cleaning. 60 makes, 295 models, 191 cities.
- Median advert: a 2017 car with 89,000 km asking 3.43 million PKR. Half of all prices are between 2.18 and 5.5 million.
- Toyota, Suzuki and Honda are 74.7% of listings. Lahore, Karachi and Islamabad are 66.3%.
- 66.0% of cars are automatic and 86.4% are petrol.
- Asking prices fall by roughly 4% to 9% per year of age for most common models (Civic 8.0%, Corolla 6.8%, Alto 5.1%, City 4.3%).
- Within the same model and year: mileage moves the price by about 2% either way, the big cities differ by about 4% to 5%, and automatics ask about 11% more than manuals.

## Highest / lowest / most

Rankings use a minimum of 30 listings for makes and models and 50 for cities.

- Most expensive advert: 2023 Lexus LX 600 Ultra Luxury, Islamabad, 108 million PKR. 44 adverts ask 50 million or more.
- Cheapest advert: 1984 Suzuki FX, Islamabad, 150,000 PKR. 812 adverts ask under 1 million.
- Most listed model: Toyota Corolla (1,241), then Honda Civic (960) and Honda City (831).
- Most listed make: Toyota (3,109). Most listed city: Lahore (2,989).
- Highest median price by model: Toyota Land Cruiser, 28.55 million. Lowest: Suzuki Khyber, 0.5 million.
- Highest median price by make: Tank, 22.4 million (30 listings, nearly all 2026 cars). Lowest: Suzuki, 1.75 million.
- Highest raw median by city: Gujranwala, 3.8 million, with Lahore and Islamabad at 3.75 million. Lowest: Wah Cantt, 2.19 million.
- Like for like, Karachi asks 4.3% less than the national figure for the same model and year; Peshawar 5.6% more.
- Highest median by fuel type: plug-in hybrid, 11.8 million. Lowest (30+ listings): CNG, 1.05 million.
- Oldest model year: 1961 (Willys M38). Most common model year: 2021 (961 listings).
- Highest mileage that passed the checks: 491,000 km, a 1984 Toyota Corona.
- Automatic share by model year: 35% for 2000, 94% for 2026.

## Caveats

- Asking prices only. Nothing shows what buyers paid or whether a car sold.
- One day, one website. No time trend, and not a sample of all cars in Pakistan.
- "Price by age" compares different model years on one day, so it mixes generation and new-price changes with ageing.
- Year, mileage and engine size are typed by sellers. About two thirds of mileages are round thousands. A few years do not match the model (a "1973 Nissan 350Z") and were left in.
- The file is named "clean" and has no duplicates, but 3 prices were off by a factor of ten (dropped), 197 mileages were not believable (blanked) and 6 engine sizes were impossible (blanked). The mileage rules are judgement calls: 500,000 km or more, more than 60,000 km per year of age, or under 1,000 km on a 2023 or older car.
- The original `price_outlier_flag` simply marks every advert at 10.5 million PKR or above (774 rows). These are real expensive cars and were kept.
- No information on condition, accident history, registration, import status or seller type.
- 145 of 191 cities have fewer than 10 adverts.

## Folder layout

```
pakwheels_used_cars_2026_clean.csv   original file from Kaggle, untouched
used_cars_cleaned.csv                cleaned data (10,586 rows, adds age_years)
used_cars_analysis.ipynb             notebook with outputs
used_cars_report.pdf                 written report
README.md
charts/                              PNG charts saved by the notebook
```

## How to run

From this folder, with pandas, numpy, matplotlib, seaborn and jupyter available:

```
jupyter nbconvert --to notebook --execute --inplace used_cars_analysis.ipynb
```

or open the notebook and run all cells. It reads the original CSV with a relative path and rewrites `used_cars_cleaned.csv` and everything in `charts/`.
