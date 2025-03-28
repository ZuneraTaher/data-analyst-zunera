# data-analyst-zunera
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
data = pd.read_csv("parks_dataset.csv", skip_blank_lines=True)

# Preview the dataset
print("Original Data:")
print(data.head())

# Clean the data
# Drop unnecessary columns like 'Column1' and malformed 'Geom'
data = data.drop(columns=["Column1", "Geom"], errors="ignore")

# Handle missing values (drop rows with missing PARK_NAME or AREA_HA)
cleaned_data = data.dropna(subset=["PARK_NAME", "AREA_HA"])

# Convert AREA_HA to numeric (in case of unexpected characters)
cleaned_data["AREA_HA"] = pd.to_numeric(cleaned_data["AREA_HA"], errors="coerce")

# Drop rows with invalid AREA_HA (e.g., NaN values after conversion)
cleaned_data = cleaned_data.dropna(subset=["AREA_HA"])

# Basic Statistics
print("\nDescriptive Statistics for Park Sizes:")
print(cleaned_data["AREA_HA"].describe())

# Largest and Smallest Parks
largest_park = cleaned_data.loc[cleaned_data["AREA_HA"].idxmax()]
smallest_park = cleaned_data.loc[cleaned_data["AREA_HA"].idxmin()]
print("\nLargest Park:")
print(largest_park)
print("\nSmallest Park:")
print(smallest_park)

# Categorize parks into size groups
size_bins = [0, 1, 10, 50, 500]  # Define size categories
size_labels = ["Small", "Medium", "Large", "Very Large"]
cleaned_data["Size_Category"] = pd.cut(cleaned_data["AREA_HA"], bins=size_bins, labels=size_labels, include_lowest=True)

# Count parks in each size category
size_counts = cleaned_data["Size_Category"].value_counts()

# Visualization: Park Size Distribution
plt.figure(figsize=(10, 6))
sns.histplot(cleaned_data["AREA_HA"], bins=30, kde=True, color='blue')
plt.title("Distribution of Park Sizes")
plt.xlabel("Area (ha)")
plt.ylabel("Frequency")
plt.show()

# Bar plot for size categories
plt.figure(figsize=(8, 5))
sns.barplot(x=size_counts.index, y=size_counts.values, palette="viridis")
plt.title("Park Size Categories")
plt.xlabel("Category")
plt.ylabel("Count")
plt.show()
