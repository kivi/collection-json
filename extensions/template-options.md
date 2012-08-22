# Template Options

Support template data **options** by adding property attribute with an array of **text** and **values**. Additionally add a **multiple** property, which indicates multiple values are suppored if set to "true".

1. Add an optional property to the <code>data</code> object: option (array of objects. text/value pair)
2. Add an optional property to the <code>data</code> object: multiple (boolean). This property has no impact if option property is not set.


```json
{ "collection" :
  {
    "version" : "1.0",
    "href" : "http://example.org/users",

    "template" : {
      "data" : [
        { "name" : "username", "value" : "", "prompt" : "User name", "required" : "true" },
        { "name" : "country", "value" : "", "prompt" : "Country", "multiple" : "false",  "options" : [ { "prompt" : "Germany", "value" : "de" }, { "prompt" : "Poland", "value" : "pl" } ] },
        { "name" : "talents", "value" : "", "prompt" : "Talents", "required" : "true", "multiple" : "true",  "options" : [ { "prompt" : "Swimming", "value" : "swimming" }, { "prompt" : "Climbing", "value" : "climbing" }, { "prompt" : "Socializing", "value" : "socializing" } ] }
      ]
    }
  }
}
```

### References
1. https://groups.google.com/d/msg/collectionjson/PQK5PoB7eSI/-TQgtjFTeqsJ
