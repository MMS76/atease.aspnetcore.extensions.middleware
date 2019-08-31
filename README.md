# atease.aspnetcore.extensions.middleware

## Installation:
execute the command in **Nuget** package manager console:
>`PM> Install-Package AtEase.AspNetCore.Extensions.Middleware`


### APi Error Handling Middleware:
this middleware contains from two part. the first is for handling validation errors in WebApi and return BadRequest (400) HttpStatus with the custom information.
as the folow, you must create and throw custom Exception class an inheritance it from Exception class.
```C#
    public class EntityNotFoundException : Exception
    {
    }
```
```C#
throw new EntityNotFoundException();
```

if the error is related to validation of model that recieved from api, you must set the `ApiException` attribute class in your custom exception class.
the `ApiException` has three overload, first is `fieldName` and the second is `fieldName, message` and the third is `title,fieldName, message`.
`fieldName` is name of the invalid field.
`message` is custom message to show to end user
`title` title of the error message
if the `message` argument left blank, the message value is taken from the Exception. e

```C#
    [ApiValidationException("Id", "EntityNotFound!!")]
    public class EntityNotFoundException : Exception
    {
    }
```
or
```C#
    [ApiValidationException("Id")]
    public class EntityNotFoundException : Exception
    {
        public EntityNotFoundException() : base("EntityNotFound!!")
        {
        }
    }
```
or
```C#
    [ApiValidationException("Title of Error", "Id", "EntityNotFound")]
    public class EntityNotFoundExceptionWithMessage : Exception
    {
    }
```



