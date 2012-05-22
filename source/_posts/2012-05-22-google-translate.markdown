---
layout: post
title: "Google Translate"
date: 2012-05-22 15:32
comments: true
categories: google translate command line
---
差不多是去年的這個時候(2011/05/26)，google宣佈要停掉google translate API，  
原因大概是很多其它網站濫用他們的服務之類的。  
不過在之後google擬好收費方案後translate API又復活啦~~

如果是付費的使用者就可以透過api key繼續存取google的API，  
如果不想付費的話也可以考慮別家翻譯API，像微軟也有推出Translator的服務。  

可是不管，我就是要用google翻譯嘛~  
那就...來吧！

先編好本地端的語言偵測、放到該放的位置

1. hg clone https://code.google.com/p/chromium-compact-language-detector
1. cd chromium-compact-language-detector
1. source ./build.sh
1. download https://gist.github.com/2767340 to replace example.cc
1. g++ -DCLD_WINDOWS -I. -L. -o lang_detect example.cc -lcld -lstdc++
1. mv lang_detect somewhere_you_put_your_usr_bin_files

然後是ruby程式...
{% gist 2767395 %}

api_url是看google chrome的字典plugin拿的，應該可以撐很久吧？  

同場加映google發音

1. 先裝好mpg321: suodo apt-get install mpg321
1. 抓以下script..
{% gist 2767430 %}

usage:
    speak '鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝嗯～鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝嗯～鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝嗯～爛機車發不動～ 鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝鵝嗯～'
