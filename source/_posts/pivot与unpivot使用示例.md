title: pivot与unpivot使用示例
categories: sql
password: cqjy2016.
date: 2018-04-13 18:54:17
tags:
---
一.下面sql创建一个视图
	 
     sql
      
     sql
       
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
     
     不给你们看 哈哈
    
     不给你们看 哈哈
        
``` sql
CREATE OR REPLACE VIEW TJ_XQ_NL
AS
        SELECT
                "NF"   ,
                "ZM"   ,
                "ZMMC" ,
                "FIV"  ,
                "SIX"  ,
                "SEVEN",
                "EIGHT",
                "NIGHT",
                "QT"
        FROM
                (
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2017'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201712'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                        
                        UNION ALL
                        
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2016'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201612'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                        
                        UNION ALL
                        
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2015'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201512'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                        
                        UNION ALL
                        
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2014'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201412'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                        
                        UNION ALL
                        
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2013'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201312'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                        
                        UNION ALL
                        
                        SELECT
                                *
                        FROM
                                (
                                        SELECT
                                                '2012'                                                      AS NF   ,
                                                "LEFT"(C.ZM, 1)                                             AS ZM   ,
                                                MAX(J.MC)                                                   AS ZMMC ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 5 THEN 1 ELSE 0 END ) AS FIV  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 6 THEN 1 ELSE 0 END ) AS SIX  ,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 7 THEN 1 ELSE 0 END ) AS SEVEN,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 8 THEN 1 ELSE 0 END ) AS EIGHT,
                                                SUM( CASE WHEN SUBSTR(C.CSRQ, 3, 1)       = 9 THEN 1 ELSE 0 END ) AS NIGHT,
                                                SUM( CASE WHEN NOT (SUBSTR(C.CSRQ, 3, 1) IN ('5', '6', '7', '8', '9')
                                                                        ) THEN 1 ELSE 0 END ) AS QT
                                        FROM
                                                GY_DA_JBXX AS C
                                        LEFT JOIN GY_XT_ZD AS J
                                        ON
                                                (
                                                        "LEFT"(C.ZM, 1) = J.BM
                                                    AND J.LB            = '1A'
                                                )
                                        WHERE
                                                EXISTS
                                                (
                                                        SELECT
                                                                1
                                                        FROM
                                                                RP_DA_QMZC AS Q
                                                        WHERE
                                                                (
                                                                        C.SN = Q.ZFSN
                                                                    AND TJNY = '201212'
                                                                    AND ZYBZ = '1'
                                                                )
                                                )
                                        GROUP BY
                                                "LEFT"(C.ZM, 1)
                                        ORDER BY
                                                "LEFT"(C.ZM, 1) ASC
                                )
                );
```

二.unpivot示范

``` sql
select
        分类  ,
        年龄    ,
        年份2012,
        年份2013,
        年份2014,
        年份2015,
        年份2016,
        年份2017
from
        (
                select
                        zm                                                      ,
                        zmmc                                           as 分类    ,
                        ln                                             as 年龄    ,
                        sum(case when nf = '2012' then num else 0 end) as 年份2012,
                        sum(case when nf = '2013' then num else 0 end) as 年份2013,
                        sum(case when nf = '2014' then num else 0 end) as 年份2014,
                        sum(case when nf = '2015' then num else 0 end) as 年份2015,
                        sum(case when nf = '2016' then num else 0 end) as 年份2016,
                        sum(case when nf = '2017' then num else 0 end) as 年份2017
                from
                        (
                                select
                                        zm  ,
                                        zmmc,
                                        nf  ,
                                        ln  ,
                                        num
                                from
                                        (
                                                select * from tj_xq_nl
                                        )
                                        xq
                                        unpivot(num for ln in(fiv as '50后', six as '60后', seven as '70后', eight as '80后', night as '90后', qt as '其它')) l
                                where
                                        zmmc is not null
                        )
                group by
                        zm  ,
                        zmmc,
                        ln
                order by
                        zm,
                        ln
        )
```