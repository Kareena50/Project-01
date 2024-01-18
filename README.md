# Project-01

The database in excel can be found [here]([MillenniumManufacturing2024Budget.xlsx](https://github.com/llamacorn118/Project-01/files/13974381/MillenniumManufacturing2024Budget.xlsx))

#1.	Find regions that have most per-person donation (take the current database, treat the "Salary" column as "Donation")

`SELECT Region, SUM(Salary) AS TotalDonation, COUNT(*) AS NumOfDonars_EachRegion, AVG (Salary) AS AvgPerRegion
FROM MillenMfg
GROUP BY Region 
ORDER BY SUM(Salary) DESC;`

![01](https://github.com/llamacorn118/Project-01/assets/153336914/33c5744d-07c8-41f5-bd15-e3c7b359a03b)

#2. Which departments have the largest number of employees whose bonus% are higher than average (overall average)?

`SELECT Department, COUNT(*) AS NumOfEmployees, ROUND((SELECT AVG([Bonus%]) FROM MillenMfg),2) AS OverallAvgBonus
FROM MillenMfg
WHERE [Bonus%] > (SELECT AVG([Bonus%]) FROM MillenMfg)
GROUP BY Department
ORDER BY COUNT(*) DESC
`

![02](https://github.com/llamacorn118/Project-01/assets/153336914/865c5c30-28b0-4d2c-8776-656926198d77)

##3. Find out managers that has the largest number of subordinates whose Bonus% are higher than average of their region (Most interesting;
involving self join and correlated subquery)

`SELECT E.MgrID, M.[First Name], M.[Last Name], COUNT(*) AS No_Emp_GreaterBonus
FROM MillenMfg AS M
INNER JOIN MillenMfg AS E
ON M.EmpID= E.MgrID
WHERE E.[Bonus%] > 
(SELECT AVG ([Bonus%]) FROM MillenMfg WHERE Region = E.Region 
GROUP BY Region)
GROUP BY E.MgrID, M.[First Name], M.[Last Name], M.[Last Name]
ORDER BY COUNT(*) DESC
`

![03](https://github.com/llamacorn118/Project-01/assets/153336914/b49c8ecc-7fe4-48b4-a0a3-0a10f4d1dd52)
