# Pandas Tutorial

## Quick Tips

### Basics

Dimensions
```buildoutcfg
df.shape
```

Column Types
```buildoutcfg
df.dtype
```

### Statistics

Simple Descreptive Statistics
```buildoutcfg
df.describe()
```

Normalize Values
```
df.column.value_counts(normalize=True)
```

Unique Values
```
df.genre.nunique()
```

Cross Table
```
pd.Crosstab(df.column1, df.column2)
```
---
### Filter
Filter rows by column values

```buildoutcfg
movies.loc[movies.duration >= 200, 'genre']
```

Multiple Criteria
```buildoutcfg
df[(condition1) & (condition2)]
```
isin
```buildoutcfg
df[df.genre.isin(['Crime', 'Drama', 'Action')]
```

Filter by Value Counts

```
df.groupby("grupo").filter(lambda df: len(df) > 31)
```
---

### List all columns of a df

```
cols = df.columns.tolist()
```

---

### Correlations
```buildoutcfg
corr = df.corr(method='choose_method')
```
Select Important Correlations

```buildoutcfg
corr_triu = corr.where(~np.tril(np.ones(corr.shape)).astype(np.bool))
corr_triu = corr_triu.stack()
corr_above_9 = corr_triu[corr_triu > 0.9]
```
---

### String Methods

```buildoutcfg
df.column.str.method()
```
---

### Change Data Type

```buildoutcfg
df.column.astype(type)
```

categorical ordinal variables

```buildoutcfg
df.column_name.astype('category'), catergories=['good', ' very good'], ordered = True)
```

### Plots

Histograma
```buildoutcfg
df.column.plot(kind='hist')
```

Barras
```buildoutcfg
df.column.value_counts().plot(kind='bar')
```

### Indexing

loc (selecting by label)
```
loc[rows,columns]
```

```buildoutcfg
df.loc[df.column == 'something', :]
```
iloc (integer position)

```buildoutcfg
df.iloc[0:3, 0:2]
```

### Change Display Options 

```buildoutcfg
pd.get_options('display.max_rows', None)
```

```buildoutcfg
pd.set_option('display.max_rows', 1000)
```

```buildoutcfg
pd.reset_option('display.max_rows', None)
```

```buildoutcfg
pd.describe_option()
```

search for options in rows
```buildoutcfg
pd.describe_option('rows')
```

reset all options
```buildoutcfg
pd.reset_option('all')
```

### Drop Columns

Drop columns different from col1 e col2
```buildoutcfg
df.drop(df.columns.difference(['col1', 'col2']), 1, inplace=True)

```

### Easy Categorization

```
df_serasa['consult_time'] = pd.cut(df_serasa['VTpUlt_ConsTCO_5a'], bins=[-2, -1.5, -1, 0, 132],
                                   labels=['-2', '-1', '0', '>0'], include_lowest=True).astype('object')\
                                .fillna('nan')
```








