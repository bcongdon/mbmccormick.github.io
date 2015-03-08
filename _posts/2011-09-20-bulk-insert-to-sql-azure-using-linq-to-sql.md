---
layout: post
title: Bulk INSERT to SQL Azure using LINQ to SQL
date: 2011-09-20 00:00
comments: true
categories: []
---
<p>Recently I have been working on developing an API for real-time and scheduled public transit data. Currently, my API supports 173 transit agencies. Each of these transit agencies provides a <a href="http://code.google.com/transit/spec/transit_feed_specification.html" target="_blank">GTFS feed</a> of their scheduled transit data in CSV format. This data ranges anywhere from 25mb to 250mb in size, with some CSV files containing well over 750,000 records. In order to efficiently query this data, I download the scheduled data and insert it to a SQL Server database. My original method of inserting this data was to use <a href="http://msdn.microsoft.com/en-us/library/bb425822.aspx" target="_blank">LINQ to SQL</a> and insert the records one at a time. Consistently, LINQ to SQL would fail after about 10,000 records and rollback the transaction. This process took about 3 hours, multiply that by 50 and 150 hours was not going to cut it. I even tried batching my queries, eliminating the transaction, and increasing the timeout window, <a href="http://www.sidarok.com/web/blog/content/2008/05/02/10-tips-to-improve-your-linq-to-sql-application-performance.html" target="_blank">among other things</a>. This didn't work and I needed another solution.</p>

<p>Next I looked into using <a href="http://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlbulkcopy.aspx" target="_blank">SqlBulkCopy</a>, which was supposed to be <a href="http://www.sqlteam.com/article/use-sqlbulkcopy-to-quickly-load-data-from-your-client-to-sql-server" target="_blank">10 times faster</a> than standard LINQ to SQL queries. After about an hour of coding, an hour of debugging, and a quick Google search, I realized that SqlBulkCopy <a href="http://stackoverflow.com/questions/1802179/sqlbulkcopy-connection-errors-when-working-with-sql-azure" target="_blank">does not play nicely</a> with SQL Azure, my hosting provider. That was another failed effort.</p>

<p>Lastly I decided to try to pass the records to the database server as a serialized XML collection and then use a stored procedure to select the records from the XML data and insert them to the appropriate table. Not only did this work, I was able to insert over 500,000 records in just over 15 minutes. You can take a look at the code I used below.</p>

<p>Here's the stored procedure that I used to insert the serialized XML data:</p>

<script src="https://gist.github.com/1229762.js"> </script>


<p>And here's the LINQ to SQL statements I used to serialize the data and send it to SQL Server:</p>

<script src="https://gist.github.com/1229797.js"> </script>


<p>Like I said, I was able to insert over 500,000 records in just over 15 minutes, instead of 150 hours like LINQ to SQL would have taken, had it completed it's transaction. More information about the API that I am developing will be posted here soon. You really have to think differently about efficiency when you are handling massive amounts of data like this.</p>
