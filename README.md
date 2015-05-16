# bigdata
logstash 資料前處理  <br />
使用R將每一封垃圾信件，讀到同一個data.frame的格式中，並移除所有換行字元 <br />

kmeans 分析步驟

隨機從2010-2015年，rand出一千筆資料來做分群，我們透過R的tm package <br />
把之前六年的資料找出出現頻率最高之詞彙，分別是

html    0.425<br />
table   0.327<br />
body   0.315<br />
email  0.287<br />
font     0.256<br />

判斷這些詞彙是否有出現在要分群的那一千筆資料中，最後我們選擇K=2<br />
cluster1: 622筆 <br />
cluster2: 378筆<br />

cluster1:<br />
無html :426<br />
有html:196<br />

無table:470<br />
有table:152<br />

無body:580<br />
有body:42<br />

無email:342<br />
有email:280<br />

無font:600<br />
有font:22<br />

cluster2:<br />
有html:378<br />
無html:0<br />

有table:292<br />
無table:86<br />

有body:326<br />
無body:52<br />

有email:284<br />
無email:94<br />

有font:332<br />
無font:46<br />

從分群顯果，可以看出，HTML TAG是垃圾郵件最明顯的特徵，cluster2就是很明顯的有html<br /> tag的垃圾郵件，而cluster1則是屬於那種幾乎沒有html tag很難分出是垃圾郵件的信件。另外我們試了當K
為3-5，但是皆沒辦法看出每群明顯的差異。

![](https://www.google.com.tw/search?hl=zh-TW&site=imghp&tbm=isch&source=hp&biw=1147&bih=783&q=bus&oq=bus&gs_l=img.3.0.0l10.1227.4621.0.6330.4.4.0.0.0.0.38.133.4.4.0.msedr...0...1ac.1.64.img..0.4.131.6yrAnftWoys#imgrc=3gnLMOuuNO_LeM%253A%3BtxK4vpKdSUPVcM%3Bhttp%253A%252F%252Fupload.wikimedia.org%252Fwikipedia%252Fcommons%252Fa%252Fac%252FArriva_T6_nearside.JPG%3Bhttp%253A%252F%252Fen.wikipedia.org%252Fwiki%252FBus%3B1735%3B1732)
