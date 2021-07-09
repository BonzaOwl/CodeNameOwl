---
title: SQL Server Getting Beginning Of Previous Week
date: 2021-08-02T09:00:00+01:00
author: Rich
layout: post
permalink: /sql-server-start-of-previous-week
categories:
  - sqlserver
tags:
  - SQL
---

In my new job one of the things I often find myself doing is needing to get the start of the previous week and can never remember how to do it. 
So here is the code that you can use to get the start of the previous week based on GETDATE()

<pre>
  <code class="sql">
    DATEADD(day,-6,DATEADD(wk,DATEDIFF(wk,6,GETDATE()),6))
  </code>
</pre>

I have also created a scalar function that can be used, this function allows you to pass in any date and get the start of the previous week. 

<pre>
  <code class="sql">
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE FUNCTION fn_StartOfPreviousWeek
    (
      @Date DATETIME
    )
    RETURNS DATETIME
    AS
    BEGIN
      DECLARE @WeekStart DATETIME

      SELECT @WeekStart = (SELECT DATEADD(day,-6,DATEADD(wk,DATEDIFF(wk,6,@Date),6)))

      RETURN @WeekStart

    END
  </code>
</pre>

Which can then be called like this 

<pre>
  <code class="sql">
    SELECT dbo.fn_StartOfPreviousWeek(GETDATE())
  </code>
</pre>