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
