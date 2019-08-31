# atease.aspnetcore.extensions.middleware

## Installation:
execute the command in **Nuget** package manager console:
```
Install-Package AtEase.AspNetCore.Extensions.Middleware -Version 1.0.2
```

```C#
    [ApiException(-1, "EntityNotFound")]
    public class EntityNotFoundExceptionWithMessage : Exception
    {
    }


    [ApiException(-1)]
    public class EntityNotFoundException : Exception
    {
        public EntityNotFoundException() : base("EntityNotFound")
        {
        }
    }
```
