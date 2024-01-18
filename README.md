# Project-01
##1.	Find regions that have most per-person donation (take the current database, treat the "Salary" column as "Donation")

`SELECT Region, SUM(Salary) AS TotalDonation, COUNT(*) AS NumOfDonars_EachRegion, AVG (Salary) AS AvgPerRegion
FROM MillenMfg
GROUP BY Region 
ORDER BY SUM(Salary) DESC;`

![alt text](image01.jpg)
