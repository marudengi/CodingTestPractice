
|ID|NAME|HOST_ID|
|-|-|-|
|4431977|BOUTIQUE STAYS - Somerset Terrace, Pet Friendly|760849|
|5194998|	BOUTIQUE STAYS - Elwood Beaches 3, Pet Friendly	|760849|
|16045624	|Urban Jungle in the Heart of Melbourne|	30900122|
|17810814|	Stylish Bayside Retreat with a Luscious Garden	|760849|
|22740286|	FREE PARKING - The Velvet Lux in Melbourne CBD	|30900122|
|22868779|	★ Fresh Fitzroy Pad with City Views! ★	|21058208|

> 760849번 유저는 공간을 3개 등록했으므로 이 유저는 헤비유저입니다.<br>
30900122번 유저는 공간을 2개 등록했으므로 이 유저는 헤비유저입니다.<br>
21058208번 유저는 공간을 1개 등록했으므로 이 유저는 헤비유저가 아닙니다.<br>

> 따라서 SQL 문을 실행하면 다음과 같이 나와야 합니다.

|ID|	NAME|	HOST_ID|
|-|-|-|
|4431977|	BOUTIQUE STAYS - Somerset Terrace, Pet Friendly	|760849|
|5194998|	BOUTIQUE STAYS - Elwood Beaches 3, Pet Friendly	|760849|
|16045624|	Urban Jungle in the Heart of Melbourne|	30900122|
|17810814|	Stylish Bayside Retreat with a Luscious Garden	|760849|
|22740286|	FREE PARKING - The Velvet Lux in Melbourne CBD	|30900122|


```sql
SELECT A.ID, A.NAME, A.HOST_ID
FROM PLACES AS A
RIGHT JOIN
(
    SELECT HOST_ID
    FROM PLACES
    GROUP BY HOST_ID
    HAVING COUNT(HOST_ID) > 1
) AS B
ON A.HOST_ID = B.HOST_ID
ORDER BY A.ID;
```