# bigdata

kmeans 分析步驟

隨機從2010-2015年，rand出一千筆資料來做分群，我們透過R的tm package
把之前六年的資料找出出現頻率最高之詞彙，分別是

html    0.425
table   0.327
body   0.315
email  0.287
font     0.256

判斷這些詞彙是否有出現在要分群的那一千筆資料中，最後我們選擇K=2
cluster1: 622筆 
cluster2: 378筆

cluster1:
無html :426
有html:196

無table:470
有table:152

無body:580
有body:42

無email:342
有email:280

無font:600
有font:22

cluster2:
有html:378
無html:0

有table:292
無table:86

有body:326
無body:52

有email:284
無email:94

有font:332
無font:46

從分群顯果，可以看出，HTML TAG是垃圾郵件最明顯的特徵，cluster2就是很明顯的有html tag的垃圾郵件，而cluster1則是屬於那種幾乎沒有html tag很難分出是垃圾郵件的信件。
