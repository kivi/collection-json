# Template Options

Support template data **options** by adding property attribute with an array of **text** and **values**. 
Additionally add a **multiple** property, which indicates multiple values are suppored if set to "true".

1. Add an optional property to the <code>data</code> object: options (array of objects. text/value pair)
    * the "text" property would indicate the text to be displayed in client.
    * the "value" property would indicate the value associated with the text above. This is the what the client should return to to the API in a POST or PUT request.

1. Add an optional property to the <code>data</code> object: multiple (boolean).
    * This property has no impact if option property is not set.
    * When **multiple** is set to "true" then the values should be returned following the pattern established by [@hamnis](https://github.com/hamnis) in [value-types](https://github.com/mamund/collection-json/blob/master/extensions/value-types.md) extensions.


#### The template:

```json
{ "collection" :
  {
    "version" : "1.0",
    "href" : "http://example.org/users",

    "template" : {
      "data" : [
        { "name" : "username", "value" : "", "prompt" : "User name", "required" : "true" },
        { "name" : "country", "value" : "", "prompt" : "Country", "multiple" : "false",  "options" : [ { "text" : "Germany", "value" : "de" }, { "text" : "Poland", "value" : "pl" } ] },
        { "name" : "talents", "value" : "", "prompt" : "Talents", "required" : "true", "multiple" : "true",  "options" : [ { "text" : "Swimming", "value" : "swimming" }, { "text" : "Climbing", "value" : "climbing" }, { "text" : "Socializing", "value" : "socializing" } ] }
      ]
    }
  }
}
```

#### A sample POST/PUT request:

```json
{
  "username" : "JDoe",
  "country" : "de",
  "talents" : ["socializing", "climibing"],
}
```

#### The response to the request above:

```json
{ "collection" :
  {
    "version" : "1.0",
    "href" : "http://example.org/users/",

    "items" : [
      {
        "href" : "http://example.org/users/1",
        "data" : [
          {"name" : "username", "value" : "JDoe", "prompt" : "User name"},
          {"name" : "country", "value" : "Germany", "prompt" : "Country"},
          {"name" : "talents", "array" : ["Socializing", "Climbing"], "prompt" : "Talents"}
        ]
      }
    ]
  }
}
```

### References
1. https://groups.google.com/d/msg/collectionjson/PQK5PoB7eSI/-TQgtjFTeqsJ
1. https://github.com/mamund/collection-json/blob/master/extensions/value-types.md