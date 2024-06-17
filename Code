import pandas as pd
import scipy.stats as stats
import matplotlib.pyplot as plt
import seaborn as sns

# Step 1: Read data from CSV
df = pd.read_csv('anova_data.csv')

# Step 2: Test for assumptions of ANOVA

# Normality test (Shapiro-Wilk test)
shapiro_results = {}
for col in df.columns:
    shapiro_results[col] = stats.shapiro(df[col])

# Homogeneity of variances test (Levene's test)
groups = [df[col] for col in df.columns]
levene_results = stats.levene(*groups)

# Step 3: Visualize outcomes

# Boxplot for visualizing distribution and outliers
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, palette="Set3")
plt.title('Boxplot of Data')
plt.xlabel('Groups')
plt.ylabel('Values')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Print results
print("Shapiro-Wilk test results:")
for col in df.columns:
    print(f"{col}: W-statistic = {shapiro_results[col][0]}, p-value = {shapiro_results[col][1]}")

print(f"\nLevene's test result:")
print(f"W-statistic = {levene_results.statistic}, p-value = {levene_results.pvalue}")
