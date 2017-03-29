長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
PTTNBA<-"https://www.ptt.cc/bbs/NBA/index.html"
for(n in 1:6){
  pttContent<-read_html(PTTNBA)
  pageup <- pttContent %>% html_nodes(".btn-group a") %>% html_attr("href")
  post_title <- pttContent %>% html_nodes(".title") %>% html_text()
  post_push <- pttContent %>% html_nodes(".nrec") %>% html_text()
  post_author <- pttContent %>% html_nodes(".author") %>% html_text()
  PttNBA_posts <- data.frame(Title = post_title,
                               PushNum = post_push,
                               Author = post_author)
  PTTNBA <- paste("https://www.ptt.cc",pageup[4], sep="")
  nam <- paste("PttNBA_posts",n,sep="")
  assign(nam, PttNBA_posts)
}

PttNBA_posts_All <- rbind(PttNBA_posts1,PttNBA_posts2,PttNBA_posts3,PttNBA_posts4,PttNBA_posts5,PttNBA_posts6)
```

爬蟲結果呈現
------------

``` r
knitr::kable(
  PttNBA_posts_All[c("Title", "PushNum", "Author")]
)
```

| Title                                             | PushNum | Author       |
|:--------------------------------------------------|:--------|:-------------|
| \[討論\] Curry VS CP3 選誰?                       | 99      | MrSatan      |
| Re: \[討論\] Rose是不是偷了Lebron的MVP啊          | 21      | FeiWenKing   |
| \[討論\] 勇迷會希望KD早早回歸嗎?                  | 16      | omare        |
| \[情報\] Dennis Smith Jr, Harry Giles 投入選秀會  | 30      | thnlkj0665   |
| \[討論\] 哪些球星算是自帶系統的球星？             | 57      | wmigrant     |
| \[公告\]昨日判罰疑問                              | 67      | namie810303  |
| Re: \[討論\] Curry VS CP3 選誰?                   | 43      | yokann       |
| Re: \[情報\] NBA Standings(2017.03.29)            | 3       | sasolala     |
| \[公告\]水桶 改判 以及增加                        | 42      | namie810303  |
| \[花邊\] LeBron James是最難防守的球員? Jimmy Bu   | 26      | hector30618  |
| \[討論\] 現役球隊中，哪一隊打起來最毛躁？         | 28      | fxxk         |
| Re: \[討論\] 現役球隊中，哪一隊打起來最毛躁？     | 24      | carotyao     |
| Re: \[討論\] Curry VS CP3 選誰?                   | 13      | zxc25678     |
| \[情報\] ★今日排名(2017.03.29)★                   | 2       | Rambo        |
| (本文已被刪除) \[Hachiko\]                        | 1       | -            |
| \[新聞\] Marion造訪中興大學 有信心打敗勇士        | 24      | iam168888888 |
| \[情報\] Harden談傷勢                             | 58      | dragon803    |
| (本文已被刪除) \[Turtle100\]                      | 1       | -            |
| \[情報\] 溜馬將裁掉Rodney Stuckey                 | 36      | jc0209       |
| \[外絮\] 塞爾提克 將舉辦2008年總冠軍十週年的聚會  | 5       | thnlkj0665   |
| \[公告\] 板規6.1                                  |         | kadasaki     |
| \[公告\] 違規檢舉區                               | 爆      | kadasaki     |
| \[情報\] 2016-2017 例行賽 (3/27 - 4/3)            | 71      | gap6060      |
| \[公告\] 2017 板主選舉                            | 25      | kadasaki     |
| \[BOX \] Nuggets 113:122 Blazers 數據             | 80      | Rambo        |
| \[BOX \] Wizards 119:108 Lakers 數據              | 59      | Rambo        |
| Re: \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩    | X2      | c1236        |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 29      | Price        |
| Re: \[討論\] 留KD或Curry？                        | 爆      | arbcs        |
| \[情報\] ESPN:馬刺4：0擊敗去年東西冠軍            | 46      | Yui5         |
| \[新聞\] 諾克奇33分轟前東家金塊　拓荒者老8之爭    | 26      | JAL96        |
| \[情報\] NBA Standings(2017.03.29)                | 爆      | kadasaki     |
| \[公告\] NBA 板 開始舉辦樂透!                     | 7       | kadasaki     |
| \[外絮\] Is it time to sit James Harden?          | 40      | djviva       |
| \[新聞\] 史上第一人！哈登總得分與助攻得分破2000   | 21      | adam7148     |
| \[討論\] D.Russell是不是骰子型球員?               | 75      | tiffanycute  |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 17      | hayuyang     |
| \[新聞\] 尼克如何變強？ 何總：補進更好的防守者    | 19      | pttpepe      |
| Re: \[討論\] NBA球員有拿過大滿貫的?               |         | nogoodlaugh  |
| \[討論\] 為什麼雙基奇搭配不起來？                 | 19      | eatk         |
| \[討論\] 浪花勇士是否是哈登永遠的痛?              | 26      | yenyu73      |
| (本文已被刪除) \[knic52976\]                      |         | -            |
| \[討論\] Rose是不是偷了Lebron的MVP啊              | X6      | knic52976    |
| \[新聞\] 勇士連3年60勝 公牛王朝後首見             | 52      | lovea        |
| \[Live\] 勇士 @ 火箭                              | 96      | Rambo        |
| \[新聞\] 年度教練競爭激烈 柯爾力挺丹東尼          | 30      | pneumo       |
| \[討論\] 籃網RHJ這個球員......                    | 23      | ronharper    |
| \[BOX \] Bucks 118:108 Hornets 數據               | 37      | Rambo        |
| \[Live\] 金塊 @ 拓荒者                            | 44      | Rambo        |
| \[BOX \] Timberwolves 115:114 Pacers 數據         | 51      | Rambo        |
| \[BOX \] Sixers 106:101 Nets 數據                 | 91      | Rambo        |
| \[BOX \] Suns 91:95 Hawks 數據                    | 20      | Rambo        |
| \[新聞\] 上場時間決定MVP？　哈登：我從未缺席比    | 27      | zzyyxx77     |
| \[BOX \] Heat 97:96 Pistons 數據                  | 21      | Rambo        |
| \[Live\] 巫師 @ 湖人                              | 34      | Rambo        |
| \[新聞\] 林書豪關鍵走步失誤　籃網惜敗76人         | 29      | jhemezuo     |
| \[BOX \] Warriors 113:106 Rockets 數據            | 爆      | Rambo        |
| \[新聞\] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗   | 34      | zzzz8931     |
| \[討論\] 沒KD 勇士還是不可小看                    | 13      | feyako       |
| Re: \[討論\] 去年快艇如何守哈登買飯集錦           | 17      | bluestaral   |
| \[情報\] Kerr fastest coach in American sports    | 72      | Angel0724    |
| \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩        | 2       | lcall        |
| \[討論\] 留KD或Curry？                            | 爆      | star1739456  |
| \[討論\] 穩進季後賽的火箭，仍然最多一輪           | X3      | sunnycello   |
| \[討論\]John Wall 算東區第一控了嗎？              | 99      | h1212123tw   |
| Re: \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥   | 2       | tadshift2    |
| (本文已被刪除) \[MrSatan\]                        | 1       | -            |
| \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳     | 69      | zzzz8931     |
| \[新聞\] NBA／尼克將改變策略？ 何納塞克：下季將   | 28      | iam168888888 |
| \[新聞\] 馬刺大勝騎士 雷納德：沒有任何意義        | 59      | ccps970915   |
| \[情報\] 微笑刺客：若Rose最終去了馬刺不會讓我感   | 爆      | tmacor1      |
| Re: \[討論\] 之前有球隊刻意輸比賽 控制對手嗎      | 1       | BBDurant     |
| \[新聞\] 女性總教練？ 主席席佛：希望快點出現      | 45      | Gotham       |
| \[公告\]多人水桶                                  | 爆      | namie810303  |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 1       | Jachu        |
| \[情報\] 火箭差8顆三分打破單季三分進球數紀錄      | 38      | Wall62       |
| \[討論\] 球員綽號                                 | 20      | ZaneTrout    |
| Re: \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳 | 16      | steveparker  |
| \[Live\] 公鹿 @ 黃蜂                              | 4       | Rambo        |
| \[Live\] 灰狼 @ 溜馬                              | 16      | Rambo        |
| \[Live\] 七六人 @ 籃網                            | 爆      | Rambo        |
| \[Live\] 太陽 @ 老鷹                              | 1       | Rambo        |
| \[Live\] 熱火 @ 活塞                              | 12      | Rambo        |
| (已被kadasaki刪除) <HANASUCIA> OP                 | X5      | -            |
| Re: \[討論\] 如果騎士在西區                       | X1      | Turtle100    |
| \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥       | 57      | Yui5         |
| Re: \[討論\] Lebron被大衛李尻背部受傷???          | 18      | iammatrix    |
| Re: \[情報\] NBA Standings(2017.03.28)            | 19      | cric335      |
| \[討論\] NBA球員有拿過大滿貫的?                   | 28      | chchang0820  |
| \[討論\] 東西勝場差～這些年的西強東弱             | 78      | liusim       |
| \[新聞\] 騎士近況低迷 詹姆斯：得找出解決方法      | 61      | adam7148     |
| \[專欄\] 死豬不怕開水燙 尼克丟臉已成習慣          | 19      | zzyyxx77     |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 19      | monmo        |
| \[情報\] Kobe：Booker有我想傳承給下一代球員的     | 50      | lovea        |
| (已被namie810303刪除) <OGC789456123>引戰          | X3      | -            |
| Re: \[討論\] 東西勝場差～這些年的西強東弱         | 25      | MK12         |
| (已被kadasaki刪除) <knic52976> 1-2                | X1      | -            |
| (本文已被刪除) \[goodbad\]                        | 15      | -            |
| \[新聞\] 隊友藥檢未 甜瓜：我都呷中藥顧健康        | 56      | royhsu425    |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 29      | Myosotis     |
| \[花邊\] Steve Francis, Joe Smith 加入BIG3聯賽    | 23      | thnlkj0665   |
| (本文已被刪除) \[hawoo\]                          |         | -            |
| \[花邊\] Kyrie Irving賽後獨自加練                 | 80      | KyrieIrving1 |
| \[情報\] 控衛防守哪家強？ “Wall”成聯盟第一        | 76      | tmac0818     |
| (已被namie810303刪除) <a102203028>引戰退          |         | -            |
| Re: \[討論\] 騎士東區第一的位置是不是不保了       | 4       | j5826497110  |
| \[討論\] 這場結束之後 是不是確定了西強東弱？      | 爆      | tiffanycute  |
| \[討論\] 騎士球隊CP值                             | 21      | t13thbc      |
| \[新聞\] 老大拒絕輪休 卻認為詹皇是例外            | 75      | pttpepe      |
| \[新聞\] 林書豪教得好 隊友會用中文說贏球          | 37      | Assisi       |
| \[討論\] 騎士是不是為了避開熱火或公牛？           | 17      | Max11        |
| \[新聞\] 球迷為搏版面出狠招 不惜拿兒子祭旗        | 14      | abc7360393   |
| \[新聞\] 騎士慘敗給馬刺　跌下東區龍頭寶座         | 26      | JAL96        |
| (本文已被刪除) <AsakuraYume>                      | 18      | -            |
| Re: \[新聞\] 老大拒絕輪休 卻認為詹皇是例外        |         | ICHIKOnice   |
| \[BOX \] Pelicans 100:108 Jazz 數據               | 25      | Rambo        |
| \[新聞\] 衛少第37次大三元 致勝一擊逆轉小牛        | 30      | MLbaseball   |
| \[BOX \] Grizzlies 90:91 Kings 數據               | 39      | hungys       |
| \[新聞\] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難    | 31      | dameontree   |
| \[討論\] 之前有球隊刻意輸比賽 控制對手嗎          | 22      | peace9527    |
| \[情報\] 詹姆斯：我想讓我們能打得更好些           | 32      | knic52976    |
| \[情報\] Kawhi Leonard連續100場得分雙位數         | 37      | jimmy5680    |
| \[討論\] Lebron被大衛李尻背部受傷???              | 99      | chouvincent  |
| Re: \[情報\] NBA Standings(2017.03.28)            | 爆      | kadasaki     |

解釋爬蟲結果
------------

``` r
str(PttNBA_posts_All)
```

    ## 'data.frame':    124 obs. of  3 variables:
    ##  $ Title  : Factor w/ 117 levels "\n\t\t\t\n\t\t\t\t(本文已被刪除) [Hachiko]\n\t\t\t\n\t\t\t",..: 10 21 11 16 12 7 20 23 6 9 ...
    ##  $ PushNum: Factor w/ 64 levels "","1","13","16",..: 21 6 4 12 17 19 15 11 14 9 ...
    ##  $ Author : Factor w/ 78 levels "-","carotyao",..: 11 4 13 16 17 12 18 15 12 7 ...

``` r
table(PttNBA_posts_All$Author)
```

    ## 
    ##            -     carotyao    dragon803   FeiWenKing         fxxk 
    ##           11            1            1            1            1 
    ##      gap6060  hector30618 iam168888888       jc0209     kadasaki 
    ##            1            1            2            1            6 
    ##      MrSatan  namie810303        omare        Rambo     sasolala 
    ##            1            3            1           18            1 
    ##   thnlkj0665     wmigrant       yokann     zxc25678     adam7148 
    ##            3            1            1            1            2 
    ##        arbcs        c1236       djviva         eatk     hayuyang 
    ##            1            1            1            1            1 
    ##        JAL96    knic52976        lovea  nogoodlaugh        Price 
    ##            2            2            2            1            1 
    ##      pttpepe  tiffanycute      yenyu73         Yui5    Angel0724 
    ##            2            2            1            2            1 
    ##   bluestaral       feyako     jhemezuo        lcall       pneumo 
    ##            1            1            1            1            1 
    ##    ronharper  star1739456   sunnycello     zzyyxx77     zzzz8931 
    ##            1            1            1            2            2 
    ##     BBDurant   ccps970915       Gotham   h1212123tw        Jachu 
    ##            1            1            1            1            1 
    ##  steveparker    tadshift2      tmacor1       Wall62    ZaneTrout 
    ##            1            1            1            1            1 
    ##  chchang0820      cric335    iammatrix KyrieIrving1       liusim 
    ##            1            1            1            1            1 
    ##         MK12        monmo     Myosotis    royhsu425     tmac0818 
    ##            1            1            1            1            1 
    ##    Turtle100   abc7360393       Assisi  chouvincent   dameontree 
    ##            1            1            1            1            1 
    ##       hungys   ICHIKOnice  j5826497110    jimmy5680        Max11 
    ##            1            1            1            1            1 
    ##   MLbaseball    peace9527      t13thbc 
    ##            1            1            1

總共117篇文章 名字為Rombo的總共發了18篇是最多文章的作者

``` r
table(PttNBA_posts_All$Title)
```

    ## 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [Hachiko]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [Turtle100]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                            \n\t\t\t\n\t\t\t\t[公告] 2017 板主選舉\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                                  \n\t\t\t\n\t\t\t\t[公告] 板規6.1\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                               \n\t\t\t\n\t\t\t\t[公告] 違規檢舉區\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                        \n\t\t\t\n\t\t\t\t[公告]水桶 改判 以及增加\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                             \n\t\t\t\n\t\t\t\t[公告]昨日判罰疑問 \n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##  \n\t\t\t\n\t\t\t\t[外絮] 塞爾提克 將舉辦2008年總冠軍十週年的聚會\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[花邊] LeBron James是最難防守的球員? Jimmy Bu\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                       \n\t\t\t\n\t\t\t\t[討論] Curry VS CP3 選誰?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                  \n\t\t\t\n\t\t\t\t[討論] 勇迷會希望KD早早回歸嗎?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##             \n\t\t\t\n\t\t\t\t[討論] 哪些球星算是自帶系統的球星？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\t[討論] 現役球隊中，哪一隊打起來最毛躁？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                   \n\t\t\t\n\t\t\t\t[情報] ★今日排名(2017.03.29)★\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\t[情報] 2016-2017 例行賽 (3/27 - 4/3)\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##  \n\t\t\t\n\t\t\t\t[情報] Dennis Smith Jr, Harry Giles 投入選秀會\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                             \n\t\t\t\n\t\t\t\t[情報] Harden談傷勢\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                 \n\t\t\t\n\t\t\t\t[情報] 溜馬將裁掉Rodney Stuckey\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] Marion造訪中興大學 有信心打敗勇士\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                   \n\t\t\t\n\t\t\t\tRe: [討論] Curry VS CP3 選誰?\n\t\t\t\n\t\t\t 
    ##                                                                                 2 
    ##          \n\t\t\t\n\t\t\t\tRe: [討論] Rose是不是偷了Lebron的MVP啊\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##     \n\t\t\t\n\t\t\t\tRe: [討論] 現役球隊中，哪一隊打起來最毛躁？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.29)\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [knic52976]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##             \n\t\t\t\n\t\t\t\t[BOX ] Nuggets 113:122 Blazers 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t[BOX ] Wizards 119:108 Lakers 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                     \n\t\t\t\n\t\t\t\t[公告] NBA 板 開始舉辦樂透!\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\t[外絮] Is it time to sit James Harden?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\t[討論] D.Russell是不是骰子型球員?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t[討論] Rose是不是偷了Lebron的MVP啊\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                 \n\t\t\t\n\t\t\t\t[討論] 為什麼雙基奇搭配不起來？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t[討論] 浪花勇士是否是哈登永遠的痛?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\t[情報] ESPN:馬刺4：0擊敗去年東西冠軍\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                \n\t\t\t\n\t\t\t\t[情報] NBA Standings(2017.03.29)\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[新聞] 史上第一人！哈登總得分與助攻得分破2000\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\t[新聞] 尼克如何變強？ 何總：補進更好的防守者\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##             \n\t\t\t\n\t\t\t\t[新聞] 勇士連3年60勝 公牛王朝後首見\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\t[新聞] 諾克奇33分轟前東家金塊　拓荒者老8之爭\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t 
    ##                                                                                 6 
    ##                        \n\t\t\t\n\t\t\t\tRe: [討論] 留KD或Curry？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\tRe: [新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\t[BOX ] Bucks 118:108 Hornets 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                  \n\t\t\t\n\t\t\t\t[BOX ] Heat 97:96 Pistons 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                 \n\t\t\t\n\t\t\t\t[BOX ] Sixers 106:101 Nets 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                    \n\t\t\t\n\t\t\t\t[BOX ] Suns 91:95 Hawks 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\t[BOX ] Timberwolves 115:114 Pacers 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\t[BOX ] Warriors 113:106 Rockets 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 巫師 @ 湖人\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                            \n\t\t\t\n\t\t\t\t[Live] 金塊 @ 拓荒者\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 勇士 @ 火箭\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                    \n\t\t\t\n\t\t\t\t[討論] 沒KD 勇士還是不可小看\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                            \n\t\t\t\n\t\t\t\t[討論] 留KD或Curry？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##           \n\t\t\t\n\t\t\t\t[討論] 穩進季後賽的火箭，仍然最多一輪\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                    \n\t\t\t\n\t\t\t\t[討論] 籃網RHJ這個球員......\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[情報] Kerr fastest coach in American sports \n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\t[新聞] 上場時間決定MVP？　哈登：我從未缺席比\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\t[新聞] 年度教練競爭激烈 柯爾力挺丹東尼\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\t[新聞] 林書豪關鍵走步失誤　籃網惜敗76人\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[新聞] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##           \n\t\t\t\n\t\t\t\tRe: [討論] 去年快艇如何守哈登買飯集錦\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <HANASUCIA> OP\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [MrSatan]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                            \n\t\t\t\n\t\t\t\t[Live] 七六人 @ 籃網\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 公鹿 @ 黃蜂\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 太陽 @ 老鷹\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 灰狼 @ 溜馬\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                              \n\t\t\t\n\t\t\t\t[Live] 熱火 @ 活塞\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                                 \n\t\t\t\n\t\t\t\t[公告]多人水桶 \n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                                 \n\t\t\t\n\t\t\t\t[討論] 球員綽號\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t[討論]John Wall 算東區第一控了嗎？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##      \n\t\t\t\n\t\t\t\t[情報] 火箭差8顆三分打破單季三分進球數紀錄\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[情報] 微笑刺客：若Rose最終去了馬刺不會讓我感\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\t[新聞] NBA／尼克將改變策略？ 何納塞克：下季將\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##      \n\t\t\t\n\t\t\t\t[新聞] 女性總教練？ 主席席佛：希望快點出現\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##     \n\t\t\t\n\t\t\t\t[新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] 馬刺大勝騎士 雷納德：沒有任何意義\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##      \n\t\t\t\n\t\t\t\tRe: [討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##   \n\t\t\t\n\t\t\t\tRe: [情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ## \n\t\t\t\n\t\t\t\tRe: [新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <knic52976> 1-2\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <OGC789456123>引戰\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                        \n\t\t\t\n\t\t\t\t(本文已被刪除) [goodbad]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                          \n\t\t\t\n\t\t\t\t(本文已被刪除) [hawoo]\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                 \n\t\t\t\n\t\t\t\t[花邊] Kyrie Irving賽後獨自加練\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\t[花邊] Steve Francis, Joe Smith 加入BIG3聯賽\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                   \n\t\t\t\n\t\t\t\t[討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##             \n\t\t\t\n\t\t\t\t[討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\t[專欄] 死豬不怕開水燙 尼克丟臉已成習慣\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##     \n\t\t\t\n\t\t\t\t[情報] Kobe：Booker有我想傳承給下一代球員的\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[情報] 控衛防守哪家強？ “Wall”成聯盟第一\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##       \n\t\t\t\n\t\t\t\t[情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] 隊友藥檢未 甜瓜：我都呷中藥顧健康\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##      \n\t\t\t\n\t\t\t\t[新聞] 騎士近況低迷 詹姆斯：得找出解決方法\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\tRe: [討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                       \n\t\t\t\n\t\t\t\tRe: [討論] 如果騎士在西區\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\tRe: [討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t 
    ##                                                                                 2 
    ##        \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <a102203028>引戰退\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                    \n\t\t\t\n\t\t\t\t(本文已被刪除) <AsakuraYume>\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\t[BOX ] Grizzlies 90:91 Kings 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##               \n\t\t\t\n\t\t\t\t[BOX ] Pelicans 100:108 Jazz 數據\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##              \n\t\t\t\n\t\t\t\t[討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\t[討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##      \n\t\t\t\n\t\t\t\t[討論] 這場結束之後 是不是確定了西強東弱？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##           \n\t\t\t\n\t\t\t\t[討論] 騎士是不是為了避開熱火或公牛？\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##                             \n\t\t\t\n\t\t\t\t[討論] 騎士球隊CP值\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\t[情報] Kawhi Leonard連續100場得分雙位數\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##           \n\t\t\t\n\t\t\t\t[情報] 詹姆斯：我想讓我們能打得更好些\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##            \n\t\t\t\n\t\t\t\t[新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##    \n\t\t\t\n\t\t\t\t[新聞] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##          \n\t\t\t\n\t\t\t\t[新聞] 林書豪教得好 隊友會用中文說贏球\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] 球迷為搏版面出狠招 不惜拿兒子祭旗\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\t[新聞] 衛少第37次大三元 致勝一擊逆轉小牛\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##         \n\t\t\t\n\t\t\t\t[新聞] 騎士慘敗給馬刺　跌下東區龍頭寶座\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##       \n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t 
    ##                                                                                 1 
    ##        \n\t\t\t\n\t\t\t\tRe: [新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t 
    ##                                                                                 1

按照標題看起來，目前大多數的文章討論比賽的比數或狀況 最常被討論的球星是詹姆士
