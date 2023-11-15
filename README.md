# Bot-Race-JSON-Schema

## JSON Schema

You can find the current schema, v0.1.0, [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.1.0/schema.json)

If you want to test your report against the schema you can fetch the schema and use a JSON schema cli implementation such as [ajv-cli](https://github.com/ajv-validator/ajv-cli).

```sh
curl https://raw.githubusercontent.com/code-423n4/Bot-Race-JSON-Schema/v0.1.0/schema.json -o schema.json
npx ajv-cli --spec=draft2020 -s ./schema.json -d report.json
```

### Upcoming Version 0.2.0

A new version of the schema will be replace v0.1.0 soon (dates to be announced) and can be found [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.2.0/schema.json).
This version restricts the values of `severity`, making it an enum instead of an open string.

If you want to test your report against the upcoming schema you can fetch the latest tag and validate as before:

```
curl https://raw.githubusercontent.com/code-423n4/Bot-Race-JSON-Schema/v0.2.0/schema.json -o schema.json
npx ajv-cli --spec=draft2020 -s ./schema.json -d report.json
```


## Details

-------
All string fields are intended to support markdown, please make sure that all special characters are escaped correctly to be parsed as JSON.

comment : **Optional** - string/null

footnote: **Optional** - string/null

findings: **Mandatory** - array of issues found

* severity   : **Mandatory** - string - current expected severity - "High" | "Medium" | "Low" | "Gas" | "Refactoring" | "NonCritical" | "Disputed"
   
* title      : **Mandatory** - string
   
* description: **Mandatory** - string
   
* gasSavings : **Optional** - float/null. Total gas savings for the individual issue. If you wish to include the individual gas saving for each instance, please add that into the `content` section of the instances.
  
* category   : **Optional** - string/null. Not currently in use, but may become required in future.
  
* instances  : **Mandatory** - an array of instances. Supports either blocks of instances, or each instance in the array as its own instance.

  * content : **Mandatory** - string; this is where the content, code snippets, @audit tags, and the file would need to be. You may choose to stack all content for an individual file here as a block, or treat it as an individual instance. If you wish to treat these as seperate instances instead of a block of instances, and you want the file to be present for each instance, please ensure that you include this in the content of each issue.

  * loc     : **Mandatory** - an array of lines of code for this instance. This value will be used to calculate the total instances, when generating the report.

------

## Example

This sample json come the winning bot (Henry) report from the recent Canto Bot race. [view report](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/main/bot-henry-example.json)

