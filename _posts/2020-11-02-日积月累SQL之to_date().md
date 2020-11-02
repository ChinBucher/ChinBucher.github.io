---
layout: post
title:  "日积月累SQL之to_date()"
date:   2020-11-02 20:25:00
categories: SQL
---

#### SQL中关于日期的知识   

`SELECT TO_DATE('2020-11-01 19:25:34', 'YYYY-MM-DD HH24:MI:SS') FROM DUAL`  
`SELECT TO_DATE('2020-11-01 19:25', 'YYYY-MM-DD HH24:MI') FROM DUAL`  
`SELECT TO_DATE('2020-11-01 19', 'YYYY-MM-DD HH24') FROM DUAL`  
`SELECT TO_DATE('2020-11-01', 'YYYY-MM-DD') FROM DUAL`  
`SELECT TO_DATE('2020-11', 'YYYY-MM') FROM DUAL`  
`SELECT TO_DATE('2020', 'YYYY') FROM DUAL`  

日期说明：  
当省略HH、MI和SS对应的输入参数时，Oracle使用0作为DEFAULT值。  
如果输入的日期数据忽略时间部分，Oracle会将时、分、秒部分都置为0，也就是说会取整到日。  
同样，忽略了DD参数，Oracle会采用1作为日的默认值，也就是说会取整到月。  
**但是，如果忽略MM参数，Oracle并不会取整到年，取整到当前月。**  

>注意：  
>1.在使用Oracle的to_date函数来做日期转换时，采用“yyyy-MM-dd HH:mm:ss”的格式作为格式进行转换，在Oracle中会引起错误：“ORA 01810 格式代码出现两次”。如：  
>`select to_date('2005-01-01 13:14:20','yyyy-MM-dd HH24:mm:ss') from dual;`  
>原因是SQL中不区分大小写，MM和mm被认为是相同的格式代码，所以Oracle的SQL采用了**mi代替分钟**。  
>`select to_date('2005-01-01 13:14:20','yyyy-MM-dd HH24:mi:ss') from dual;`  
>2.另要以24小时的形式显示出来要用**HH24**  
>`select to_char(sysdate,'yyyy-MM-dd HH24:mi:ss') from dual;`//mi是分钟(日期转化为字符串)  
>`select to_char(sysdate,'yyyy-MM-dd HH24:mm:ss') from dual;`//mm会显示月份  
>3.两个日期间的天数
>`select floor(sysdate - to_date('20020405','yyyymmdd')) from dual; `
>4.日期间隔 **between and**    
>`select * from table where date between TO_DATE('2020-11-01', 'YYYY-MM-DD') AND TO_DATE('2020-11-01', 'YYYY-MM-DD')`    
>>(sql 中使用 between and 查询日期时左右闭合的问题，   
>>`select * from TABLE where date between '2020-11-01' and '2020-11-01'` =>结果查不到。  
>>短日期类型默认Time为00:00:00，所以当使用between and作限制条件时，  
>>就相当于 between '2020-11-01 00:00:00' and '2020-11-01 00:00:00'，因此就查不出数据)  


>>**TO_CHAR** 是把日期或数字转换为字符串；
>>**TO_DATE** 是把字符串转换为数据库中得日期类型转换函数；
>>**TO_NUMBER** 将字符转化为数字；
>>
>>一、TO_CHAR   
>>使用TO_CHAR函数处理数字   
>>TO_CHAR(number,  '格式' )   
>>TO_CHAR(salary,’$99,999.99’);   
>>使用TO_CHAR函数处理日期   
>>TO_CHAR( date ,’格式’);  
>>二、TO_NUMBER   
>>使用TO_NUMBER函数将字符转换为数字   
>>TO_NUMBER( char [,  '格式' ])  
>>三、TO_DATE   
>>使用TO_DATE函数将字符转换为日期   
>>TO_DATE( char [,  '格式' ])  