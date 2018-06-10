# Welcome to jPool!

__jPool__ is a rails 5 _api-only_ app with a sqlite3 database and _rspec_ as testing framework.
In order to accomplish the exercise you need to complete a CR~~UD~~ over the _Person_ Model:

 - Create new _person_ via _POST_ /people
 - Get list of _people_ via _GET_ /people
 
## Tasks:
__1__. Create an _ActiveRecord_ _Person_ model with the following __mandatory__ attributes :
 - `name`
 - `age`: must be greater than 18
 -  `email`: must be valid email format
 - `code` Integer

Add the necessary ActiveModel validations

---------------

__2__.  Develop the necessary controller action to create a new person record via _POST /people_
The application should receive a `token` parameter in order to create a new person.
`token` will be used to obtain person data from the following web service:

`GET http://www.mocky.io/v2/<token>`

Use the following token as an example: `5b1e4132310000ea143ff716`

```
{
    "name": "Mrs. Joana Casper",
    "email": "joana.casper@11paths.com",
    "age": 32,
    "fibonacci": 15
}
```

Person's `name`, `age` and `email` will be directly obtained from the web service.

`code` will be the _Fibonacci number_ in `fibonacci` position

In order to keep our controllers _DRY_ and _KISS_, we'll create the `app/services/person_service.rb` class to create instances that receive a `token` and return a new `Person` object using `#build_person` method.

__Note__*: This code would be deployed to production. It's a __must__ to develop some tests for the `PersonService` class. The app is using _rspec_ with the basic structure _ready-to-code_.

---------------

__3__. Last but not least, develop the necessary controller action so that _GET /people_ returns a _JSON array_ with people data. It will accept an optional `code_min`  parameter to apply some filters.
