from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("PySparkPractice") \
    .master("local[*]") \
    .getOrCreate()

data = [
    (1, "Tejas", 50000),
    (2, "Rahul", 60000),
    (3, "Amit", 70000)
]

columns = ["id", "name", "salary"]

df = spark.createDataFrame(data, columns)

df.show()

spark.stop()
