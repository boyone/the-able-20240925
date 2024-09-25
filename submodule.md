# Submodule

1. Create submodule project

   ```sh
   mkdir HelloWorldSolution
   cd HelloWorldSolution
   dotnet new sln
   dotnet new classlib -o HelloWorld
   dotnet new xunit -o HelloWorld.Test
   dotnet sln add HelloWorld/HelloWorld.csproj
   dotnet sln add HelloWorld.Test/HelloWorld.Test.csproj
   cd HelloWorld.Test
   dotnet add HelloWorld.Test reference HelloWorld/HelloWorld.csproj
   ```

   ```txt
   /HelloWorldSolution
   |__HelloWorldSolution.sln
   |__HelloWorld/
   |__HelloWorld.Test/
   ```

2. Restore and build project

   ```sh
   dotnet restore
   dotnet build
   ```

3. Implement Test Code call `HelloWorld.Test/HelloWorldTest.cs`

   ```cs
   namespace HelloWorld.Test;

   public class HelloWorldTest
   {
       [Fact]
       public void GreetingShouldReturnHello_World()
       {
           Greeting greeting = new Greeting();

           string actualResult = greeting.Hello();

           Assert.Equal("Hello, World!", actualResult);
       }
   }
   ```

4. Implement Production Code call `HelloWorld/Greeting.cs`

   ```cs
   namespace HelloWorld;

   public class Greeting
   {
       public Greeting()
       {
       }

       public string Hello()
       {
           return "Hello, World!";
       }
   }
   ```

5. Run Test

   ```sh
   dotnet test
   ```

6. Set PackageID and Version HelloWorld.csproj

   ```xml
   <PropertyGroup>
      <PackageId>HelloWorld</PackageId>
      <Version>1.0.0</Version>
      <TargetFramework>net8.0</TargetFramework>
      <ImplicitUsings>enable</ImplicitUsings>
      <Nullable>enable</Nullable>
   </PropertyGroup>
   ```

7. Pack HelloWorld.1.0.0.nupkg

   ```sh
   dotnet pack HelloWorld -o pack
   dotnet pack HelloWorld -o pack --include-source
   ```

8. Add nuget source

   ```sh
   dotnet nuget add source local --name local
   dotnet nuget list source
   ```

9. Create local directory

   ```sh
   mkdir ~/.nuget/NuGet/local
   ```

10. Push `nupkg`

    ```sh
    dotnet nuget push pack/HelloWorld.1.0.0.nupkg --source local
    ```

11. Add local package to Project

    ```sh
    dotnet add package HelloWorld --version 1.0.0 -s ~/.nuget/NuGet/local
    ```

---

## Publish Package

### NuGet.org: https://learn.microsoft.com/en-us/nuget/nuget-org/publish-a-package

### Private Feed: https://learn.microsoft.com/en-us/nuget/hosting-packages/overview

1. [nuget-server](https://learn.microsoft.com/en-us/nuget/hosting-packages/nuget-server)
2. [local feeds](https://learn.microsoft.com/en-us/nuget/hosting-packages/local-feeds)
