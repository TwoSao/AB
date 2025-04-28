# Andmebaas1

IndianCustomers ja UKCustomer select tabelid
![image](https://github.com/user-attachments/assets/65302077-484a-4e32-81f1-12ab36eff221)

select Id, Name, Email from IndianCustomers
union all
select Id, Name, Email from UKCustomers
![image](https://github.com/user-attachments/assets/c556528e-cb91-42ae-a42b-3caf34bec804)

select Id, Name, Email from IndianCustomers
union
select Id, Name, Email from UKCustomers
![image](https://github.com/user-attachments/assets/ea6d171e-5375-4525-9741-5667fc27d23d)

procedure spGetCustomers
![image](https://github.com/user-attachments/assets/b7c4134e-f825-4e5d-a59f-dc7ee5c69e16)

procedure spGetEmployeesByGenderAndDepartment
![image](https://github.com/user-attachments/assets/22fb9991-200a-46f3-8f22-8856ab62cc2c)

-- soov vaadata sp sisu ( содержимое процедуры ) !!
sp_helptext spGetEmployeesByGenderAndDepartment
![image](https://github.com/user-attachments/assets/da348979-d20b-4b40-84d6-5487a1668706)

--- kuidas muuta sp-d ja pane krüpteeringu peale, et keegi teine peale teid ei saaks muuta
alter proc spGetEmployeesByGenderAndDepartment
@Gender nvarchar(20),
@DepartmentId int
with encryption --krüpteerimine
as begin
	select Name, Gender, DepartmentId from Employees where Gender = @Gender
	and DepartmentId = @DepartmentId
end
--- ja vaata procedure !!
sp_helptext spGetEmployeesByGenderAndDepartmen
![image](https://github.com/user-attachments/assets/c74cf644-120e-4d2c-962b-3b91c1dc22aa)

procedure spGetEmployeeCountByGender
![image](https://github.com/user-attachments/assets/cdbb697f-a5e0-4194-9a23-731aa89ea48f)

-- kui soovid sp tektsi näha !!
sp_helptext spGetEmployeeCountByGender
![image](https://github.com/user-attachments/assets/05f42167-87d3-4934-9896-f1775504fad4)

-- vaatame , millest see sp sõltub !!
sp_depends spGetEmployeeCountByGender
-- vaatame tabelit !! 
sp_depends Employees
![image](https://github.com/user-attachments/assets/ccc078e8-3e32-4e21-ad03-e2d20cf6ae5b)
![image](https://github.com/user-attachments/assets/efebf209-177c-4d3c-a995-bd56153c052b)

procedure spGetNameById1

declare @FirstName nvarchar(50)
execute spGetNameById1 5, @FirstName output ( тут выбран 5 id )
print 'Name of the employee = ' + @FirstName
![image](https://github.com/user-attachments/assets/b4ee0931-bd8c-4132-bb6f-6b52536443bb)

--- sisseehitatud string funktsioonid
-- see konverteerib ASCII tähe väärtuse numbriks
select ascii('a')
-- kuvab A-tähe
select char (97)
![image](https://github.com/user-attachments/assets/8da4277f-d0d4-48a7-ab8b-eee395b36bd8)
![image](https://github.com/user-attachments/assets/b4f7aab1-00b6-412e-b41b-ce5aac5c2d16)

-- eemaldame tühjad kohad sulgudes
select ltrim('        Hello')
![image](https://github.com/user-attachments/assets/a5af6fa7-07e3-4858-b15b-524125869bf2)

-- tühikute eemaldamine veerust
select ltrim(Name) as FirstName from Employees
![image](https://github.com/user-attachments/assets/b4c1af69-bac3-4bf7-9bab-1ab1e13e2c4c)

--paremalt poolt tühjad stringid lõikab ära
select rtrim('      Hello          ')
![image](https://github.com/user-attachments/assets/d2b2987b-4e78-406b-8d10-b95ced70616f)

--keerab kooloni sees olevad andmed vastupidiseks
-- vastavalt upper ja lower-ga saan muuta märkide suurust
-- reverse funktsioon pöörab kõik ümber
select REVERSE(UPPER(ltrim(Name))) as FirstName, lower(Gender) as Gender,
rtrim(ltrim(Name)) + ' ' + Gender as FullInfo
from Employees
![image](https://github.com/user-attachments/assets/2ccc39c1-22ea-4b83-a42b-e22399e07125)

--näeb, mitu tähte on sõnal ja loeb tühikud sisse
select Name, len(Name) as [Total Characters] from Employees
![image](https://github.com/user-attachments/assets/3b7b1b3b-5ed5-4237-8160-7e2d236bbb6d)

--- näeb, mitu tähte on sõnal ja ei loe tyhikuid sisse
select Name, len(ltrim(Name)) as [Total Characters] from Employees
![image](https://github.com/user-attachments/assets/5381319a-665d-4757-8b7b-b75cba87317e)

updated tabel Emplooyes with Email
![image](https://github.com/user-attachments/assets/7caf0425-0b52-48c5-8ef5-251887c612aa)

--- lisame *-märgi alates teatud kohast
select Name,
	substring(Email, 1, 2) + REPLICATE('*', 5) + --peale teist tähemärki paneb viis tärni
	SUBSTRING(Email, CHARINDEX('@', Email), len(Email) - charindex('@', Email)+1) as Email
from Employees
![image](https://github.com/user-attachments/assets/b588eb89-2987-472a-968c-4d1c97a78bae)

--- kolm korda näitab stringis olevat väärtust
select replicate(Name, 3)
from Employees
![image](https://github.com/user-attachments/assets/ed6bbb51-751f-4a29-ae56-f6dd807a9129)

-- kuidas sisestada tyhikut kahe nime vahele
select space(5)
![image](https://github.com/user-attachments/assets/8f21f738-08fe-4334-a4a3-ed88acb959bc)

--Employees tabelist teed päringu kahe nime osas (Name ja Email)
--kahe nime vahel on 25 tühikut
select Name + space(25) + Email as FullInfo
from Employees
![image](https://github.com/user-attachments/assets/a45d9be6-5379-4bbb-996c-61a66fee6e79)
