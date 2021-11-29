PHP JavaScript 农历公历干支历互转,万年历,四柱,六十甲子,属相,十二星座,二十四节气,支持从-1000到3000年间的八字排盘及大运推算,分析刑冲合害关系<br />

算法原理和JS源码完全来自: http://www.bieyu.com/<br />
真太阳时模块来自: http://www.nongli.net/sxwnl/<br />

此工具类包含:<br />
1,儒略日历<br />
以公元前4713年1月1日12时为起点,每天(每廿四小时)加一的历法;<br />
比如2020年1月1日12点的儒略日为2458850,2020年1月1日0点的儒略日为(2458850 - 0.5);<br />
这种历法方便各种计算,比如已知起点日为周一可求得任一日期的星期,已知起点日的干支可求得任一日期的干支<br />

2,公历(阳历,格里历,西历)<br />
以地球绕太阳公转计算的历法;<br />
用公式可直接求得两分两至(春分秋分夏至冬至);<br />
公转是椭圆轨道,把这个椭圆均分为24等分,可求得中国的二十四节气;12等分则为西方的十二星座;<br />
此工具计算出的时间点误差在20秒内;<br />
已知2020年春分点为3月20日11点49分57秒,则算法认为57秒前是双鱼座,57秒后是白羊座,是否按此计算请自行斟酌;<br />
每月两节不变更,最多相差一两天.上半年来六廿一,下半年是八廿三 这里的六廿一和八廿三说的是公历;<br />

3,阴阳历(农历,民间称阴历)<br />
严格地说,以月球绕地一周为一个月计算的历法为阴历;<br />
如果这样,阴历跟二十四节气的时间差就越来越大,我们可能要在夏季过大年初一;<br />
也许人们为了能固定在立春前后吃上年夜饭(May be...),引入闰月的概念,使之与公转齐平,所以农历考虑了月亮又考虑了太阳,为阴阳历;<br />
陰曆正月與置閏这一段很难理解,请参看 http://www.bieyu.com/<br />

4,干支历<br />
这种历法现在可能多用于命理学和历史研究领域,与二十四节气相关;<br />
由于一年只有12个月而不是60个月,一天只有12小时而不是60小时,所以合法的四柱并不是简单的排列组合;<br />
年柱跟月柱有固定的关系:甲己之年丙作首,乙庚之歲戊為頭,丙辛歲首尋庚起,丁壬壬位順行流,若言戊癸何方發,甲寅之上好追求.<br />
日柱跟时柱也有固定关系:甲己還加甲,乙庚丙作初,丙辛從戊起,丁壬庚子屬,戊癸何方發,壬子是真途;<br />
八字组合共有518400种,且一個八字出現後,至少要60年後才会再出現,最多要240年後才又出現;<br />
已知2020立春点为2月4日17时3分44秒,44秒前为己亥年,44秒后为庚子年;<br />
已知2020驚蟄为3月5日10时57分22秒,22秒前为戊寅月,22秒后为己卯月;<br />
是否按此计算请自行斟酌,尤其是要用在命理学上的时候;<br />

PHP与Javascript的方法是一致的,如下:<br />

公历转儒略日:<br />
p.Jdays(yy, mm, dd, hh, mt, ss);<br />

儒略日转公历:<br />
p.Jtime(jd);<br />

公历转农历:<br />
p.Solar2Lunar(yy, mm, dd);<br />

农历转公历:<br />
p.Lunar2Solar(yy, mm, dd, ry);<br />

公历转干支历:<br />
p.GetGZ(yy, mm, dd, hh, mt, ss);<br />

干支历转(搜索)公历:<br />
p.gz2gl(ygz, mgz, dgz, hgz, yeai, mx);<br />

根据公历进行八字排盘<br />
p.fatemaps(xb, yy, mm, dd, hh, mt, ss);<br />

//引申出来的方法<br />
p.ValidDate(yy, mm, dd);<br />
p.GetWeek(yy, mm, dd); //计算公历的某天是星期几<br />
p.GetSolarDays(yy, mm); //获取公历某个月有多少天<br />
p.GetLunarDays(yy, mm, ry); //获取农历某个月有多少天<br />
p.GetRunyue(yy); //获取农历某年的闰月,0为无闰月<br />
p.GetXZ(yy, mm, dd, hh, mt, ss); //根据公历年月日精确计算星座下标<br />
p.Get24JQ(yy); //求出含某公历年立春點開始的24节气的儒略日历时间<br />
p.MGZ(ygz); //根据年干支计算所有合法的月干支: 甲己之年丙作首...<br />
p.HGZ(dgz); //根据日干支计算所有合法的时干支: 甲己還加甲...<br />
p.GZ(tg, dz);<br />

//分析刑冲合害关系<br />
GetGX(tg, dz); //参看demo.html 及 docs/make_gx.php
