# Project-01
##1.	Find regions that have most per-person donation (take the current database, treat the "Salary" column as "Donation")

`SELECT Region, SUM(Salary) AS TotalDonation, COUNT(*) AS NumOfDonars_EachRegion, AVG (Salary) AS AvgPerRegion
FROM MillenMfg
GROUP BY Region 
ORDER BY SUM(Salary) DESC;`

![01](https://github.com/llamacorn118/Project-01/assets/153336914/33c5744d-07c8-41f5-bd15-e3c7b359a03b)

##2. Which departments have the largest number of employees whose bonus% are higher than average (overall average)?

`SELECT Department, COUNT(*) AS NumOfEmployees, ROUND((SELECT AVG([Bonus%]) FROM MillenMfg),2) AS OverallAvgBonus
FROM MillenMfg
WHERE [Bonus%] > (SELECT AVG([Bonus%]) FROM MillenMfg)
GROUP BY Department
ORDER BY COUNT(*) DESC
`
