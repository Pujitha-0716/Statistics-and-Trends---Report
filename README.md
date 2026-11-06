import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
# Read the uploaded CSV file
file_name = next(iter(uploaded))
students = pd.read_csv(file_name)

# Display the first few rows to understand the data
students.head()# Upload the student dataset from your computer
# Check how many rows and columns are in the dataset
print("Dataset size:", students.shape)

# Check whether there are any missing values
print("\nMissing values:")
print(students.isnull().sum())

# Remove any repeated rows, if there are any
students = students.drop_duplicates()

print("\nUpdated dataset size:", students.shape)
plt.figure(figsize=(8, 5))

sns.histplot(data=students, x="G3", bins=10, kde=True)

plt.title("Distribution of Students' Final Grades")
plt.xlabel("Final Grade")
plt.ylabel("Number of Students")

plt.show()
plt.figure(figsize=(8, 5))

sns.regplot(
    data=students,
    x="G2",
    y="G3",
    scatter_kws={"alpha": 0.6}
)

plt.title("Relationship Between Second-Period and Final Grades")
plt.xlabel("Second-Period Grade (G2)")
plt.ylabel("Final Grade (G3)")

plt.show()

# Calculate the correlation between the two grades
correlation = students["G2"].corr(students["G3"])

print("Correlation between G2 and G3:", round(correlation, 2))
# Choose the columns I want to compare
selected_columns = [
    "studytime",
    "absences",
    "failures",
    "G1",
    "G2",
    "G3"
]

# Calculate the relationships between the selected columns
correlation_matrix = students[selected_columns].corr()

plt.figure(figsize=(9, 6))

sns.heatmap(
    correlation_matrix,
    annot=True,
    cmap="coolwarm",
    fmt=".2f",
    linewidths=0.5
)

plt.title("Heatmap of Student Performance Factors")
plt.show()
