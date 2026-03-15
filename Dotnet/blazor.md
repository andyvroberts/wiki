# Create

On linux, create a new dotnet solution in a new directory.  
https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-sln   
```
dotnet new sln -o solution_name  
cd solution_name  
```
Run the dotnet new command to create a child project  
https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new    
```
Dotnet new classlib -o app_nameA -n solution_name.app_nameA
Dotnet new blazor -o app_nameB -n solution_name.app_nameB
```
Then add the to projects to the solution.  
```
dotnet sln add app_nameA
dotnet sln add app_nameB
```
