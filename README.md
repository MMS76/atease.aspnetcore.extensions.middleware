# atease.aspnetcore.extensions.middleware

## Installation:
execute the command in **Nuget** package manager console:
>`PM> Install-Package AtEase.AspNetCore.Extensions.Middleware`


### APi Error Handling Middleware:
this middleware contains from two part. the first is for handling validation errors in WebApi and return BadRequest (400) HttpStatus with the custom information.
as the folow, you must create and throw custom Exception class an inheritance it from Exception class.

```C#
throw new EntityNotFoundException();
```

if the error is related to validation of model that recieved from api, you must set the `ApiException` attribute class in your custom exception class.
the `ApiException` has two overload, one is `errorCode` and the other is `errorCode, message`.
`errorCode` is 
if the `message` argument left blank, the message value is taken from the Exception. e

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
