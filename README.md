from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("MyFirstPySpark") \
    .master("local[*]") \
    .getOrCreate()

print("PySpark Started Successfully")

spark.stop()
