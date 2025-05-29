# Questions on EntityFramework Core
You can find the list of questions where i am expecting from a candidate irrespective of his experience considering if he is in coding.

### Candidate should have a minimum knowledge on,
1. Purpose of this efcore
2. How do we create a EF Core project?
   - Is it Class Library, Console application?
4. What all necessary required to start an EF Core project?,
   - Packages: Choose based on .NET Framework
     - For EF Core functionality
     - For Database Provider: SQL Server, POSTGRESS, SQLLITE, INMEMORY
     - For Migrations: **.Tools** and ***.Design** packages are really required if yes for which purpose we use these?
5. What is **Code-First** and **Database-First** approach?
6. If we follow **Database-First**, How do we get the database entities/sourcemodels into EF Core project?
7. How do we push Code(Classes/Entities/SourceModels) to Database tables?

### Basic Questions
1. How are we gonna interact SQL Database : Fetching/CRUD operations using EF Core?
2. Query: var employee = dbContext.Employee.FirstOrDefault(x=>x.Id == 1);
   Now, I want to see SQL query for the above LINQ query. How you are gonna get this?
   Option 1: Use dbContext.Employee.FirstOrDefault(x=>x.Id == 1).ToQueryString()
   Option 2: Get this sql query from command prompt
   



