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
