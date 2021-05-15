# EDA (Explainatory Detailed Analysis

### Lower Left Triangle correlation matrix
```
corr = df.corr()
plt.figure(figsize=(20,10))
mask = np.zeros_like(corr,dtype=np.bool)
mask[np.triu_indices_from(mask)] = True
sns.heatmap(corr,mask=mask,annot=True)
plt.show()
```
![image](https://user-images.githubusercontent.com/33158202/118260197-9d95c400-b4cf-11eb-9cc9-608be998e462.png)

### Histogram for continuos variable
```
plt.figure(figsize=(12, 5))
plt.hist(train['windmill_generated_power(kW/h)'].values, bins=200)
plt.title('Histogram cat1 counts in train')
plt.xlabel('windmill_generated_power(kW/h)')
plt.ylabel('Count')
plt.show()
```
![image](https://user-images.githubusercontent.com/33158202/118260349-d59d0700-b4cf-11eb-8447-e95fa8444563.png)

### Box Plot for a single attribute
```
plt.figure(figsize=(10,5))
plt.xlim(0,20)
plt.ylabel('windmill_generated_power(kW/h)')
sns.boxplot(x=train['windmill_generated_power(kW/h)'])
plt.show()
```
![image](https://user-images.githubusercontent.com/33158202/118260417-ea799a80-b4cf-11eb-9756-56811e099429.png)

### Profile Report for Tabular Dataframe
```
from pandas_profiling import ProfileReport
profile = ProfileReport(train)
profile
```

### Density plots for different categorical values
```
temp = df_train.pivot(columns='cloud_level',
                     values='windmill_generated_power(kW/h)')
temp.columns = ['Null', 'Extremely Low', 'Low', 'Medium']
temp.plot.density()
```
Here, cloud_level is the categorical column and windmill_generated_power(kW/h) is the target column.

![image](https://user-images.githubusercontent.com/33158202/118375257-4fbbb180-b5de-11eb-9917-eac7e9f13b4a.png)