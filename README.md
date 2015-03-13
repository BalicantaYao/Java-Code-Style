
# Jave Code Style

##Introduction
此文件主要參考 [Google Jave Style](http://google-styleguide.googlecode.com/svn/trunk/javaguide.html) 。

本文件目的為統一編程風格，避免零亂的程式風格，同時將 Check Style 裡面的檢查項目條列以供參考，方便閱便以及調整。

Google 說他們的 Code Style document 是一個 hard and fast rule，我們要超越 Google 所以我們也必須將 Code Style 視為 hard and fast rule，這或許關乎代碼的美感，但更關乎程序員的尊嚴。

## Souce Code File
### 檔案名稱
Google 文件說每個文件名稱都必須是 `.java` 結尾。

### 檔案編碼
編碼設成 *UTF-8* 不過份吧？

### 檔案大小
最大檔案大小不可以超過 3MB

### 特殊字元
#### 舉足輕重的空白字元
之所以空白字元重要，可以看一下[空白之神的故事](https://chrome.google.com/webstore/detail/%E7%82%BA%E4%BB%80%E9%BA%BC%E4%BD%A0%E5%80%91%E5%B0%B1%E6%98%AF%E4%B8%8D%E8%83%BD%E5%8A%A0%E5%80%8B%E7%A9%BA%E6%A0%BC%E5%91%A2%EF%BC%9F/paphcfdffjnbcgkokihcdjliihicmbpd)，關於空白字元有很多注意的事項，我們在這裡只提一下 Trailing space，每一行結尾都不要有空白字元 。附贈，[哪一天被空白給婊了都不知道](http://www.codinghorror.com/blog/2009/11/whitespace-the-silent-killer.html) 。

```Java 
//Good
LG.log("Hi");
```

```Java 
//Bad, 根本就一樣啊，好啦，用 '．' 代表空格
LG.log("Hi");．
```

#### 空白之外的特殊字元
關於回車`\r`,`\t` 這類的字元比較少用到，這裡就不多加約束，但請自愛。

### 檔案結構
一個程式的結構順序大約如下

 - 版權宣告
 - Package 宣告
 - Import 宣告
 - Class Java Doc
 - Class 本體
 
每個部分請用 **一行空白**來區隔。

####版權宣告
目前有兩種選擇
```
option1:
    //這種應該會有修正，因為公司搬家
	/**
	 * Copyright (c) 2000-${year} xxxxxx. 
	 * Tun-Hwa South Road, Taipei, Taiwan, R.O.C. All Rights Reserved.
	 */
```
```
option2: 
    //這種好，公司搬家也不怕
	/**
	 * Copyright (c) xxxxx, Inc All Rights Reserved.
	 */ 
```

#### Package 宣告
Package 宣告是不受單行字數限制，即便他一千個字元，也是合法，不要把他斷掉了

```Java 
// Good
package com.ebizprise.cp.logger.util;
```

```Java
// Bad
package com.ebizprise.
        cp.logger.util;
```

#### import 宣告
永遠都不要使用萬用字元 import，盡可能不使用 `static import`

```Java 
// Good
import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;
```
```Java 
// Bad
import org.apache.commons.logging.*;
```
import 也是有順序和群集性的，每個群集需要用**一行空白來分開**
```Java 
// Good
import org.apache.commons.logging.Log;
import org.apache.commons.logging.LogFactory;

import com.ebizprise.cp.util.format.MsgFormater;
```
```Java 
// Bad
import org.apache.commons.logging.Log;
import com.ebizprise.cp.util.format.MsgFormater;
import org.apache.commons.logging.LogFactory;
```

#### Class Java Doc
每個 Class 都必須寫說明，說明裡面包含三個項目

 - Class 目的以及特殊注意事項
 - Author 作者

Class 目的裡面可透過`html syntax` 來說明，特殊注意使用事項，可以在這邊多加描敘，在這裡永遠都是寫越多越好，越詳細越好。

作者的部分，主要標注出這個 Class 的作者，在這裡我有點意見，如果可以透過 `SVN Blame`之類的機制知道Class 被誰改過這個標準似乎意義就降低了，同時如果此Class被多人改過，作者標很多個就會變成名人堂性質，實質意義下降。


### Class 本體

#### Class 成員變量
Class 的成員變量也是有順序和群聚性的，這裡似乎沒有一個標準作法告訴我們應該怎麼做，但原則上就是邏輯類似的變量放在一起。

#### Overloaded 以及 constructor
如果你的多個 function 是 overloaded 的，請你行行好把他們聚集在一起，避免別人(或是你) 下次在找 function 的時候把他們滑鼠的滾輪給滾壞了。

## 格式
#### 關於括號
##### 在可以選擇要不要用括號的地方，我們都用括號
這個標題就說明了一切。

``` Java
// Good
if (isTrue) {
    System.out.println("Hi");
}
```

``` Java
// Bad
if (isTrue)
    System.out.println("Hi");
```

##### 在可以選擇要不要用括號的地方，我們都用括號
我們採用[埃及式開關括號法](http://www.codinghorror.com/blog/2012/07/new-programming-jargon.html)，規則如下：

 - 開括號前不會有空白行, **但會有一格空白**
 - 開了括號會有一行空白
 - 關括號前會有一行空白
 - 如果關括號的後面，有分號，`else`等，則和關括號同一行。
 
``` Java
// Good
if (isTrue) {
    System.out.println("Hi");
} else {
    System.out.println("Hello");
}
```
``` Java
// Bad
if (isTrue) 
{
    System.out.println("Hi");
} 
else 
{
    System.out.println("Hello");
}
```
```
// Bad - 開括號前少了帥氣的空格
if (isTrue){
    System.out.println("Hi");
} 
else{
    System.out.println("Hello");
}
```
##### 空的 block 該怎麼處理？
有時候無可避免的我們會出現空 block 的狀況，在這裡我們就讓開關括號同一行

```
//Good
void hello(){}
```

```
//Bad
void hello() {

}
```
##### 每行的長度限制
目前的規範是 140 個字元，但有一些例外的狀況

 - 有些東西是無法切割的像是 URL，就不在140個字元的規範內
 - Package name 以及 import lib
 
##### 斷行、折行
斷行就沒有全面性的標準原則，在很多情況下都是合法的斷行
>Tips: 或許我們可以透過一些重構的方法，減少斷行的發生

##### 到底何時該斷行？
Google 斷行的原則有點抽象，**prefer to break at a higher syntactic level**，應該是可以從語法的角度下去定義，這句話我還不能參透，但可以繼續看下去。

1.如果我們需要在 non-assignment operator，我們的斷行必須要在 non-assignment operator 之前(整句話不知道在講啥，看例子) 
```java 
// 像 . 就是一個 non-assignment operator
// Better
    if(StringUtils.isNotEmpty(eventItem.getUiEventInfo()
            .getCampaignName())){
            promoEventItem_list.add(eventItem);
    }
```
```
//Bad
    if(StringUtils.isNotEmpty(eventItem.getUiEventInfo().
        getCampaignName())){
            promoEventItem_list.add(eventItem);
    }
```

結論是在這種情況下，怎麼斷都醜，就不是 Code Style 層面要解決，而應該往上到重構層面解決。

2.當我們需要在 assign operator 附近斷行的時候，我們通常會斷在 assign operatior 之後。
```java 
// Good
    doTouchAEventCode = 
        getGenericEventService().doTouchAEventCode(eventType, eventCode);

```
```java 
// Bad
    doTouchAEventCode 
       = getGenericEventService().doTouchAEventCode(eventType, eventCode);
```

3.如果是 method 或是 constructor 的小括號，需要跟在method name 之後，就就是斷行要在小括號之後。
```java 
// Good
    doTouchAEventCode = getGenericEventService().doTouchAEventCode(
        eventType, eventCode);
```
```java 
// Bad
    doTouchAEventCode = getGenericEventService().doTouchAEventCode
        (eventType, eventCode);
```

4.如果要在逗號(,)附近斷行，應該是在逗號的後面斷行。
```java
//Good
LG.debug(this.getClass().getCanonicalName(), 
   "import event data begin....");
```
```java
//Bad
LG.debug(this.getClass().getCanonicalName()
    ,"import event data begin....");
```
##### 斷行後的縮排
斷行後的縮排至少都需要在四格以上，但有一些狀況下的連續斷行，他們允許在同一層縮排裡。

### 關於空白
#### 空白行
空白行這帖藥很利害，服用了以後，可以讓你的 Code 變清楚，簡單的說邏輯區塊之前就是加入空白行的好時點，什麼是邏輯區塊？看例子:

```Java
// Method 就是一種比較明顯的邏輯區塊
// Good
public void hello() {
}

public void byeBye() {
}
```
```Java
// Bad
public void hello() {
}
public void byeBye() {
}
```
另外一種空行的時間點，就是像寫作文一樣的分段，這個分段很重要，
如果能夠搭配註解服用，你的 Code 可以說是好讀到一個不行。
```Java
// 讀取 Excel 檔案
InputStream inputStream = importData.getInputFile();
HSSFWorkbook inputExcelWorkbook = new HSSFWorkbook(inputStream);

// 取第一個 Sheet裡面的第一列，標題列
HSSFSheet worksheet = inputExcelWorkbook.getSheetAt(0);
Iterator<Row> rowIterator = worksheet.iterator();
```
同樣的 import 也是有群聚性的，所以也應該要空白分開，但我打娘胎來，我沒整理過 import，因為我用 Eclipse，相信你也是。

#### 空白之神
空白之神可謂亦正亦邪，空白之神可以分成 **Vertical whitespace 垂直空白** 以及 **horizontal whitespace 水平空白**兩種，我們先從垂直空白說明起：
##### 垂直空白
垂直空白其實就是空行，那空白行出現的時機，應該是什麼時候呢？

 1. 連續的邏輯區塊中間需要
