# Questions on how do we fix the exceptions while debugging or even from production

**Exception 1:**
```
System.IO.FileNotFoundException: 'The configuration file 'appsettings.json' was not found and is not optional. The expected physical path was 'C:\Users\NuthanMurarysetty\Source\Repos\dotnet-for-interviews\dotnet-for-interviews\EfCore.Consuming.App\bin\Debug\net8.0\appsettings.json'.'
```
**Solution:**
```
1. Right click on the file and click on Properties
2. Set Build Action == Embedded Resource
3. Set Copy to Output Directory == Copy Always/ Copy If Newer
```
