# bigdata

logstash 資料前處理  <br />
-----------------------------------------------------------------------------
使用R將每一封垃圾信件，讀到同一個data.frame的格式中，並移除所有換行字元 <br />

kmeans 分析步驟
-----------------------------------------------------------------------------
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

從分群顯果，可以看出，HTML TAG是垃圾郵件最明顯的特徵，cluster2就是很明顯的有html tag的垃圾郵件，而cluster1則是屬於那種幾乎沒有html tag很難分出是垃圾郵件的信件。另外我們試了當K
為3-5，但是皆沒辦法看出每群明顯的差異。
kibana分析
-----------------------------------------------------------------------------
利用logstash，抓出ip，並利用Geo-IP抓出各個IP的地理位置並畫出圖
![GitHub](https://cloud.githubusercontent.com/assets/12468475/7665356/0fad2f1e-fbe6-11e4-97b0-71d116531f08.jpg "GitHub,Social Coding")

由下圖我們可以看出亞洲為Spam的大宗來源
![](https://cloud.githubusercontent.com/assets/12468475/7665390/0e937484-fbe7-11e4-9a90-89368b217ca0.jpg)

圖下為前一百Spam IP來源，可發現多為同一個IP寄出
![](https://cloud.githubusercontent.com/assets/12468475/7665391/1eb60020-fbe7-11e4-8ab6-8aa1a2f061ca.jpg)
