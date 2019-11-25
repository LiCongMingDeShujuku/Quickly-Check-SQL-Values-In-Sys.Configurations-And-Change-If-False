![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 快速检查Sys.Configurations中的值，如果是False，则进行改正
#### Quickly Check SQL Values In Sys.Configurations And Change If False
**发布-日期: 2015年9月24日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
下面是一些非常简单的sql逻辑（logic），它会检查配置是否已启用，如果未启用，则对这些值进行更改。
注意：如果你曾想使用<> for NOT EQUAL TO，你做的是正确的。另一种方法是使用这个！=，但这不是便携式的。尽可能使用ANSI。SQL Server解释说这两个不会完全相同地进行构造。 在这个例子中，我只是用了EQUAL（=）。


## English
Here’s some very simplified sql logic that checks to see if a configuration is enabled, and subsequently changes those values if they are not enabled.
Note: If you ever want to use <> for NOT EQUAL TO then you’re doing the right thing. The alternative is to use this !=, but this is not portable. Use ANSI whenever possible. SQL Server interprets these two ‘not equal to’ constructs the same. In this example I’m simply usinge EQUAL (=)


---
## Logic
```SQL
use master;
set nocount on
 
declare
@sao    int = (select cast([value] as int) from master.sys.configurations where [name] = 'show advanced options')
,   @bcd    int = (select cast([value] as int) from master.sys.configurations where [name] = 'backup compression default')
,   @xpc    int = (select cast([value] as int) from master.sys.configurations where [name] = 'xp_cmdshell')
 
if  @sao = 0    begin exec  master..sp_configure 'show advanced options', 1 reconfigure end
if  @bcd = 0    begin exec  master..sp_configure 'backup compression default', 1    reconfigure end
if  @xpc = 0    begin exec  master..sp_configure 'xp_cmdshell', 1 reconfigure end


```

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

