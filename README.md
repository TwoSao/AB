
![image](https://github.com/user-attachments/assets/3345bdef-bd03-44c3-88c0-83ebd6952540)# AB

select * from Person
go
delete from Person where Id = 8
go
select * from Person
![image](https://github.com/user-attachments/assets/37c7a971-738e-4d1a-b23c-f10be11f127e)

select * from Person where City = 'Gotham'
![image](https://github.com/user-attachments/assets/8d54a50f-9638-40df-8ba4-23290924a3c7)

select * from Person where City <> 'Gotham'
select * from Person where City != 'Gotham'
![image](https://github.com/user-attachments/assets/04003536-52fb-49a2-861e-6ab9ccec2e08)

select *from Person where Age = 100 or 
Age = 50 or Age = 20
select * from Person where Age in (100, 50, 20)
![image](https://github.com/user-attachments/assets/7b4be8d0-09f5-4fd1-a150-492583bfe91a)

select * from Person where City like 'n%'
select * from Person where Email like '%@%'
![image](https://github.com/user-attachments/assets/0445a650-de0e-4a86-ac6d-2c49067fac0a)

select * from Person where Email not like '%@%'
![image](https://github.com/user-attachments/assets/1b089519-b047-4a20-a799-1ce91505a4ae)

select * from Person where Email like '_@_.com'
  ![image](https://github.com/user-attachments/assets/c873cb5b-92dc-4628-bb75-3888e271f727)

select * from Person where Name like '[^WAS]%'
![image](https://github.com/user-attachments/assets/0c690080-7263-4a04-9291-76f9c5f94f13)

select * from Person where (City = 'Gotham' or City = 'New York')
and Age >= 40
![image](https://github.com/user-attachments/assets/f1c38f63-1f8f-4db8-9821-1a25fc4751fb)

select top 3 * from Person
![image](https://github.com/user-attachments/assets/bf7e24e5-e46f-4898-ac2d-731e28ba85bf)

select * from Person
select top 3 Age, Name from Person
![image](https://github.com/user-attachments/assets/3ada7017-d503-4505-aec5-c06148beaa3f)

select top 50 percent * from Person
![image](https://github.com/user-attachments/assets/2d04c888-5dc2-407e-b239-b72fb3f7f020)

select * from Person order by cast(Age as int)
select * from Person order by Age
![image](https://github.com/user-attachments/assets/c6db8198-f65e-40ab-b1c5-495e37721ed6)

select sum(cast(Age as int)) from Person
![image](https://github.com/user-attachments/assets/e8ab371e-1360-41dd-8324-ccb0c75f3f01)

select min(cast(Age as int)) from Person
![image](https://github.com/user-attachments/assets/0b3f4e4b-5663-44b1-8a8f-f656dfc55878)

select max(cast(Age as int)) from Person
![image](https://github.com/user-attachments/assets/cb6f6c97-bffb-45ba-a91c-88a61568c94f)

select City, sum(cast(Age as int)) as TotalAge from Person group by City
![image](https://github.com/user-attachments/assets/709c52c5-4664-405d-afcf-2e380e8de2eb)
