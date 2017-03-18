# 安裝Julia紀錄

弄這個弄了兩天orz

## 1. 透過git clone官方庫然後make

我沒成功...到現在還是搞不清楚為甚麼？  

要求的依賴我都裝了說......  


## 2. 透過add-apt-repositor ppa安裝

我太天真了，docker居然沒有內建add-apt得自己安裝  

一下看了阿舍大大的介紹才知道  

[連結](http://www.arthurtoday.com/2010/09/ubuntu-add-apt-repository.html)  

需要安裝  

`$ sudo apt-get install python-software-properties`  

`$ sudo apt-get install software-properties-common `  

然後新增官方ppa  

`$ sudo add-apt-repository ppa:staticfloat/julia-deps`  
`$ sudo apt-get update`  
`$ sudo apt-get install julia`

## 3. 直接pull建好的docker 映像檔

[Julia官方庫](https://hub.docker.com/r/library/julia/)  

`$ sudo docker pull library/julia:0.5.1` 

:後面的看你要哪種版本

直接使用

`$ docker run -it --rm julia:0.5.1` 

> 沒有-ti無法看到輸出，--rm讓你退出容器後立刻刪除資料，讓你想要rmi就rmi不用先rm

或是

`$ sudo run -it --rm julia:0.5.1 /bin/bash`



掛載資料夾

先在home創建一個Julia資料夾

接著

`$ sudo docker run -it --rm -v /home/你的名字/julia:/usr/myapp julia:0.5.1 /bin/bash`

> -v /home/你的名字/julia:/usr/myapp

這一段是把自己的julia資料夾掛到docker裏面的/usr/myapp 

想掛home也可以

# Hello,World

裝好了當然要來個經典Hello,world

在/home/你的名字/julia下新增檔案hello.jl
裏面打好`println("hello,world")`
然後進去容器

`$ sudo docker run -it --rm -v /home/你的名字/julia:/usr/myapp julia:0.5.1 /bin/bash`

`$ cd /user/myapp` 
`$ ls `

應該可以看到有個hello.jl檔案

然後下
`$ julia hello.jl`


> Hello,world

