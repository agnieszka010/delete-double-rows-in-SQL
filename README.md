# delete-double-rows-in-SQL

SELECT distinct a, b FROM Tab


#########################################

SELECT 
  a,
  b,
  count(*)
FROM tab
GROUP BY a, b
HAVING count(*)>1


##########################################

WITH T as
(SELECT 
	a,
	b,
	ROW_NUMBER() OVER (PARTITION BY a, b ORDER BY (SELECT 1)) POZ
	FROM Tab)
  
#########################################

SELECT * FROM T WHERE POZ>1

#########################################

DELETE FROM T WHERE POZ>1
