# Questions on how do we fix the exceptions while debugging or even from production

**Exception 1: Type of Exception: Resource**
```
System.IO.FileNotFoundException: 'The configuration file 'appsettings.json' was not found and is not optional. The expected physical path was 'C:\Users\NuthanMurarysetty\Source\Repos\dotnet-for-interviews\dotnet-for-interviews\EfCore.Consuming.App\bin\Debug\net8.0\appsettings.json'.'
```
**Solution:**
```
1. Right click on the file and click on Properties
2. Set Build Action == Embedded Resource
3. Set Copy to Output Directory == Copy Always/ Copy If Newer
```

**Exception 2: Type of Exception: Database Connectivity Issue**
```
      An error occurred during execution.
      Microsoft.Data.SqlClient.SqlException (0x80131904): A connection was successfully established with the server, but then an error occurred during the login process. (provider: SSL Provider, error: 0 - The certificate chain was issued by an authority that is not trusted.)
```

**Solution:**
```
If we add in connections string: TrustServerCertificate=True; then issue is resolved
"DatabaseConnection": "Server=locaohost;Database=BookDB;User Id=sa;Password=Admin@12345;TrustServerCertificate=True;"
```

**Exception 3: Type of Exception: Database Migration**
```
Add-Migration : The term 'Add-Migration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling 
of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Add-Migration Initial
+ ~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Add-Migration:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```
Solution:
```
Due to missing this following pacakge
Install-Package Microsoft.EntityFrameworkCore.Tools
For specific version
Install-Package Microsoft.EntityFrameworkCore.Tools -Version 8.0.0
```
**Exception 4: Type of Exception: During Migration**
```
Your startup project 'EfCore.Consuming.App' doesn't reference Microsoft.EntityFrameworkCore.Design. This package is required for the Entity Framework Core Tools to work. Ensure your startup project is correct, install the package, and try again.
```
**Solution:**
```
1. Default Project: Your EF Core project
2. Startup Project: Your EF Core project
```
**Exception 5: Type of Exception: During Migration**
```
Unable to create a 'DbContext' of type ''. The exception 'Unable to resolve service for type 'Microsoft.EntityFrameworkCore.DbContextOptions`1[EFCore_CodeFirstApproach.BookDBContext]' while attempting to activate 'EFCore_CodeFirstApproach.BookDBContext'.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728
```
**Solution:**
```
Added Default Constructor
 public BookDBContext()
 {

 }

Note: You should have the following code
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
{
   optionsBuilder.UseSqlServer("Server=KANINI-LTP-283;Database=BookDB;User Id=sa;Password=Admin@12345;TrustServerCertificate=True;");
}
```
**Exception 6: Type of Exception: During Migration**
```
Unable to create a 'DbContext' of type ''. The exception 'No database provider has been configured for this DbContext. A provider can be configured by overriding the 'DbContext.OnConfiguring' method or by using 'AddDbContext' on the application service provider. If 'AddDbContext' is used, then also ensure that your DbContext type accepts a DbContextOptions<TContext> object in its constructor and passes it to the base constructor for DbContext.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728
```

**Solution:**
```
Due to not added the following code in db context
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
{
   optionsBuilder.UseSqlServer("Server=KANINI-LTP-283;Database=BookDB;User Id=sa;Password=Admin@12345;TrustServerCertificate=True;");
}
```
