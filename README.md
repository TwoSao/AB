-- Otsime emailidest aadresse, kus esineb '@aaa.com'
select Email, PATINDEX('%@aaa.com', Email) as FirstOccurence
from Employees
where PATINDEX('%@aaa.com', Email) > 0
-- pilt: https://github.com/user-attachments/assets/b1a56586-36dc-4731-85dc-b31bdfc856af

-- Asendame emailides '.com' lõpud '.net' lõpuga
select Email, REPLACE(Email, '.com', '.net') as ConvertedEmail
from Employees
-- pilt: https://github.com/user-attachments/assets/0b47c6f4-1241-46da-b25a-2d5821db4a17

-- Peidame emaili teise kuni neljanda tähemärgi asemel tärnid
select Name, Email,
	stuff(Email, 2, 3, '*****') as StuffedEmail
from Employees
-- pilt: https://github.com/user-attachments/assets/15a1579c-906b-4ebf-9681-7077ccbcd1be

-- Kuvame hetke kuupäeva ja kellaaja
select GETDATE(), 'GETDATE()'
-- pilt: https://github.com/user-attachments/assets/873fb078-54aa-47cc-b119-eabed73a4fc9

-- Tabel DateTime
-- pilt: https://github.com/user-attachments/assets/ef6972e6-2e78-4932-9173-d7ac6bf5beda

-- Erinevad ajapäringud:
select CURRENT_TIMESTAMP, 'CURRENT_TIMESTAMP' -- serveri aeg
select SYSDATETIME() -- täpsem ajaväärtus
select SYSDATETIMEOFFSET() -- aeg koos UTC nihkega
select GETUTCDATE() -- UTC aeg
-- pilt: https://github.com/user-attachments/assets/e077190c-dec0-4730-9d96-ef03b6c6177f

-- Kontrollime, kas antud string on kehtiv kuupäev:
select isdate('asd') -- tagastab 0, kuna ei ole kuupäev
-- pilt: https://github.com/user-attachments/assets/be11e873-1f7c-4a8a-9c61-a57580aa7901

select ISDATE(getdate()) -- tagastab 1, kuna on kuupäev
-- pilt: https://github.com/user-attachments/assets/b3b7f483-bb62-4c5b-9d2d-1d837b2ad5c8

select isdate('2025-03-24 09:19:01.1490061') -- tagastab 0, kuna komakohti on liiga palju
-- pilt: https://github.com/user-attachments/assets/4a796c36-a7f8-4c99-a4db-ddcb2a7e6883

select isdate('2025-03-24 09:19:01.149') -- tagastab 1, kuna formaadis on lubatud kolm komakohta
-- pilt: https://github.com/user-attachments/assets/30535ad8-2a02-4f1c-a9f9-96c5a3b35d98

-- Päeva, kuu ja aasta välja toomine:
select day(getdate()) -- tänase päeva number
-- pilt: https://github.com/user-attachments/assets/755a101c-bb32-4b7f-8050-7c35d16a08df

select day('02/28/2025') -- antud kuupäeva päev
-- pilt: https://github.com/user-attachments/assets/fabe5b7b-9400-4de9-a1c7-94c71bbec872

select month(getdate()) -- praeguse kuu number
-- pilt: https://github.com/user-attachments/assets/a025c9f3-9174-474e-bd00-1a88c26daac6

select month('02/28/2025') -- antud stringi kuu number
-- pilt: https://github.com/user-attachments/assets/eedd59d5-9b44-48cc-9ea5-185ee7e16234

select year(getdate()) -- käesolev aasta
-- pilt: https://github.com/user-attachments/assets/09713c9b-e36d-467f-890f-6a6329c1560f

select year('02/28/2025') -- kuupäeva aasta
-- pilt: https://github.com/user-attachments/assets/c6ef777f-3d08-419e-8ddc-2742d583de17

-- Päevade ja kuude nimede päring:
select datename(day, '2025-03-24 09:19:01.149') -- päeva number
-- pilt: https://github.com/user-attachments/assets/c3438a24-9975-474b-a9ac-99f76fba8241

select Datename(WEEKDAY, '2025-03-25 09:19:01.149') -- nädalapäev sõnana
-- pilt: https://github.com/user-attachments/assets/b57436d5-62fb-45f9-9386-bc040184e5b9

select datename(MONTH, '2025-03-24 09:19:01.149') -- kuu nimi
-- pilt: https://github.com/user-attachments/assets/2c3572fa-5454-44e7-9467-8bed40eae5f8

select datename(dayofYEAR, '2025-03-24 09:19:01.149') -- aasta päevanumber
-- pilt: https://github.com/user-attachments/assets/1cec21cc-d30c-4d4e-8453-ac4f377c4f46

-- Tabel: EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/feb983d1-8c0d-4e98-b52c-7eea58efd740

-- Töötajate sünnipäevade andmed:
select Name, DateOfBirth, DATENAME(weekday, DateOfBirth) as [Day] from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/070bd869-ba44-40f1-9b6d-2c651aca9a5b

select MONTH(DateOfBirth) as MonthNumber from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/0af328b7-5104-4237-8e03-93fd39b9ab77

select DateName(MONTH, DateOfBirth) as [MonthName] from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/15ed4bf8-a72f-45ef-9d53-23f8683d3004

select YEAR(DateOfBirth) as [Year] from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/b7ecbe9b-451a-46fe-9a9a-e36e1e7f78fb

-- Kuupäevaga seotud funktsioonid:
select DATEPART(weekday, '2025-01-30 12:22:56.401') -- nädalapäeva number
select DATEPART(MONTH, '2025-03-24 12:22:56.401') -- kuu number
select DATEADD(DAY, 20, '2025-03-24 12:22:56.401') -- lisab 20 päeva
select DATEADD(DAY, -20, '2025-03-24 12:22:56.401') -- lahutab 20 päeva
select datediff(MONTH, '11/30/2024', '03/24/2025') -- kuude vaheline erinevus
select datediff(year, '11/30/2022', '03/24/2025') -- aastate erinevus
-- pilt: https://github.com/user-attachments/assets/24ceacfc-7fd9-44cd-b1c3-274a6d2b0835

-- Funktsiooniga arvutatud vanus:
select Id, Name, DateOfBirth, dbo.fnComputeAge(DateOfBirth) as Age from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/95606d88-692c-4ad2-8b1a-9278e85a5540

select dbo.fnComputeAge('11/11/2010')
-- pilt: https://github.com/user-attachments/assets/01c4dab8-ce07-472f-b49a-f4b3740e0646

-- Kuupäeva teisendamine erinevasse formaati:
select Id, Name, DateOfBirth,
convert(nvarchar, DateOfBirth, 109) as ConvertedDOB
from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/7ad9b994-fb46-4224-811d-2288a7b1e305

-- Ühendame nime ja ID üheks väljakuks:
select Id, Name, Name + ' - ' + cast(Id as nvarchar) as [Name-Id] 
from EmployeesWithDates
-- pilt: https://github.com/user-attachments/assets/09b13c9c-2c03-4a31-ad50-703aa23c1500

-- Tänase kuupäeva väljastamine:
select cast(getdate() as date)
select convert(date, GETDATE())
-- pilt: https://github.com/user-attachments/assets/f4bd2205-916e-4642-ae5a-a54dc23d0175
