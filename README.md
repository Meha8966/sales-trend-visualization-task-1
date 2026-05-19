# Sales-trend-visualization-task-1
# NAME:MEHA MARY SAMUVEL
# DOMAIN:DATA ANALYTICS
# DURATION:4 WEEKS
# INTERN ID:CITS712
# PROJECT 1: sales-trend-visualization
# INTERN PERIOD: 17TH MAY-14JUNE

# OUTPUT
<img width="1129" height="693" alt="Image" src="https://github.com/user-attachments/assets/99c2d4e1-030e-4d1e-9176-f0e9c3a3473a" />
<img width="1111" height="646" alt="Image" src="https://github.com/user-attachments/assets/b212f323-9aa2-4cca-a994-90840c897e1b" />
<img width="794" height="295" alt="Image" src="https://github.com/user-attachments/assets/326967fb-766b-435e-bd49-59e002edc1e4" />
<img width="641" height="561" alt="Image" src="https://github.com/user-attachments/assets/a841b59d-92a4-4a48-b7b8-73a86844386a" />
<img width="782" height="331" alt="Image" src="https://github.com/user-attachments/assets/68a5434d-e6d4-4dcd-ae19-6a2bbaa22327" />
<img width="1137" height="700" alt="Image" src="https://github.com/user-attachments/assets/fe777439-aab2-43df-bd16-9174e7f71656" />
<img width="827" height="300" alt="Image" src="https://github.com/user-attachments/assets/84847cd8-a223-4043-a46a-ff1bb115f83c" />
<img width="1194" height="685" alt="Image" src="https://github.com/user-attachments/assets/e99f2acc-af80-4587-9b4b-8aada2096cc9" />
<img width="1086" height="293" alt="Image" src="https://github.com/user-attachments/assets/a086a3d5-7742-45d8-a52f-c599f82c1cfa" />
<img width="1176" height="644" alt="Image" src="https://github.com/user-attachments/assets/e06580c7-371a-46fc-8213-084e6cb9da70" />
<img width="1123" height="652" alt="Image" src="https://github.com/user-attachments/assets/65483f50-32ef-451a-b5f4-4dfe4c030777" />

# OBJECTIVE
The main objective of this project is to analyze and visualize sales data using data analytics techniques. The project helps in understanding sales performance, profit trends, regional sales distribution, and top-selling products through charts and dashboards. It also aims to improve decision-making using data visualization tools like Python and Power BI.

# SOURCE CODE
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
df = pd.read_csv("Sample - Superstore.csv", encoding='latin1')

# Show first rows
print(df.head())

# Dataset information
print(df.info())

# Check missing values
print(df.isnull().sum())

# Convert Order Date column
df['Order Date'] = pd.to_datetime(df['Order Date'])

# -------------------------------
# 1. Monthly Sales Trend
# -------------------------------

monthly_sales = df.groupby(df['Order Date'].dt.month)['Sales'].sum()

monthly_sales.plot(kind='bar')

plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales")

plt.show()

# -------------------------------
# 2. Region-wise Sales
# -------------------------------

region_sales = df.groupby('Region')['Sales'].sum()

region_sales.plot(kind='pie', autopct='%1.1f%%')

plt.title("Region-wise Sales")
plt.ylabel("")

plt.show()

# -------------------------------
# 3. Category-wise Comparison
# -------------------------------

category_sales = df.groupby('Category')['Sales'].sum()

category_sales.plot(kind='bar')

plt.title("Category-wise Sales")
plt.xlabel("Category")
plt.ylabel("Sales")

plt.show()

# -------------------------------
# 4. Profit Analysis
# -------------------------------

profit_analysis = df.groupby('Category')['Profit'].sum()

profit_analysis.plot(kind='bar')

plt.title("Profit Analysis by Category")
plt.xlabel("Category")
plt.ylabel("Profit")

plt.show()

# -------------------------------
# 5. Top Selling Products
# -------------------------------

top_products = df.groupby('Sub-Category')['Sales'].sum().sort_values(ascending=False).head(10)

top_products.plot(kind='bar')

plt.title("Top Selling Products")
plt.xlabel("Sub-Category")
plt.ylabel("Sales")

plt.show()
