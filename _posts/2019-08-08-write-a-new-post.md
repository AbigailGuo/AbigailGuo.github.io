---
title: Pandas的基础操作
author: Abigail
date: 2020-09-09 15:52:00 +0800
categories: [Blogging, Tutorial]
tags: [不学无术的眼泪]
---

#### 读文件

```python
file_read = pd.read_csv("data/"+file_name, index_col=0)
```

#### 选择

**注意**：Both `loc` and `iloc` are row-first, column-second. This is the opposite of what we do in native Python, which is column-first, row-second.

```python
# 第0行
reviews.iloc[0]
# 第0列
reviews.iloc[:, 0]
# 前三行，第0列
reviews.iloc[:3, 0]
# 第1-3行，第0列
reviews.iloc[1:3, 0]
# 选取特定的行
reviews.iloc[[0, 1, 2], 0]
# 选取最后五行
reviews.iloc[-5:]
# 第0行, 某一列的值
reviews.loc[0, 'country']
# 带有判断条件的
reviews.loc[reviews.country == 'Italy']
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
reviews.loc[(reviews.country == 'Italy') | (reviews.points >= 90)]
reviews.loc[reviews.country.isin(['Italy', 'France'])]
```

#### 和

```python
# points是一个列名，describe会显示出这一列的count，mean等值
reviews.points.describe()
# mean
reviews.points.mean()
# 某一列不重复的值的列表
reviews.taster_name.unique()
# 某一列不重复的值出现的次数
reviews.taster_name.value_counts()

```

#### 映射



```python
review_points_mean = reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean)
```



