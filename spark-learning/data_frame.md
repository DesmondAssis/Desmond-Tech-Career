# DataFrame
## group by
* table
tb_a

| id | name | age |
|:----:|:--:|:--:|
|1 |lilei|28|

tb_b

|id|name|class|
|:--:|:--:|:--:|
|1|lilei|NO.2|

```sql
select a.id,a.name,a.age,b.class from tb_a a inner join
tb_b b on a.id=b.id and a.name=b.name
```

* 转成用dataframe实现

```java
	DataFrame df1 = ....,
	DataFrame df2 = ....;
	
	DataFrame df = df1.join(df2, df1.col("id").equalTo(df2.col("id")
		.and(df1.col("name").equalTo(df2.col("name"))), "inner")
		.where df1.col("id").gt(100);
	df.select(df1.col("id"), df1.col("name"), df2.col("class"))
	.toJavaRDD()
	.map(...);
```