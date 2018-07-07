# spark-basics

## Code

```
from pyspark import SparkContext, SparkConf

if __name__ == "__main__":
    conf = SparkConf().setAppName("word count").setMaster("local[3]")
    sc = SparkContext(conf = conf)

    lines = sc.textFile("shakespeare-cleaned.txt")

    words = lines.flatMap(lambda line: line.split(" "))

    wordCounts = words.countByValue()

    sortedWordCounts = sorted(wordCounts.items(), key=lambda kv: kv[1], reverse=True)

    for word, count in enumerate(sortedWordCounts[:24], start=1):
        print("{} : {}".format(word, count))
```

## Result

![result](https://github.com/marbirk/spark-basics/blob/master/result.png?raw=true)

=> The #24 most used word in the shakespeare text is "u'he". It has a word count of 4546.

