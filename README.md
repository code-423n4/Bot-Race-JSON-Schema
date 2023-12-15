# Bot-Race-JSON-Schema

## JSON Schema

You can find the current schema, v0.1.0, [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.1.0/schema.json)

If you want to test your report against the schema you can fetch the schema and use a JSON schema cli implementation such as [ajv-cli](https://github.com/ajv-validator/ajv-cli).

```sh
curl https://raw.githubusercontent.com/code-423n4/Bot-Race-JSON-Schema/v0.1.0/schema.json -o schema.json
npx ajv-cli --spec=draft2020 -s ./schema.json -d report.json
```

### Upcoming Version 0.3.0

A new version of the schema will replace v0.1.0 on [Place Holder Date - TBD] and can be found [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.3.0/schema.json).
**Changes**:

- restricts the values of `severity`, making it an enum instead of an open string.
- `content` and `description` are optional
- `content` must be in code block format, we are expecting \`\`\` at the begining and end of this string.
- `loc` must contain a link to the code or file.

If you want to test your report against the upcoming schema you can fetch the latest tag and validate as before:

```
curl https://raw.githubusercontent.com/code-423n4/Bot-Race-JSON-Schema/v0.3.0/schema.json -o schema.json
npx ajv-cli --spec=draft2020 -s ./schema.json -d report.json
```


## Details

-------
# Bot Report Schema Documentation

## Table of Contents
- [Properties](#properties)
  - [comment](#comment)
  - [footnote](#footnote)
  - [findings](#findings)
- [Findings Array](#findings-array)
  - [Severity](#severity)
  - [Title](#title)
  - [Description](#description)
  - [Gas Savings](#gas-savings)
  - [Category](#category)
  - [Instances](#instances)
    - [Content](#content)
    - [LOC (Line of Code)](#loc-line-of-code)

## Properties

### comment

Comments will be added at the top of your report. Accepts plain strings or valid markdown.

- Type: String | Null

### footnote

Footnotes will be added at the bottom of your report. Accepts plain strings or valid markdown.

- Type: String | Null

### findings

An array of all findings.

- Type: Array
- Min Items: 1

## Findings Array

### Severity

High | Medium | Low | Gas | Refactoring | NonCritical | Disputed

- Type: String (Enum: "High", "Medium", "Low", "Gas", "Refactoring", "NonCritical", "Disputed")

### Title

Title of the issue. Accepts plain strings or valid markdown.

- Type: String

### Description

Description of the issue. Accepts plain strings or valid markdown.

- Type: String | Null

### Gas Savings

Gas Savings.

- Type: Number | Null

### Category

If category of the issue is clear it can be set as a plain string, otherwise if can be left empty

- Type: String | Null

### Instances

An array of instances where the issues have occurred. This can be separated out for every instance or used as a block of instances. The instance count will be generated from the LOC.

- Type: Array

#### Content

This is expected to be in code block format and must start and end with ```. Content is for code snippets, @audit tags, and file data. You may choose to stack all content for an individual file here as a block, or treat it as an individual instance. If you wish to treat these as separate instances instead of a block of instances, and you need the file to be present for each instance, please ensure that you include this in the content of each issue. If the issue is with the whole file you may leave this empty and just have the link in the loc field.

- Type: String | Null
- Pattern: ^(\`{3})[^`]*(\\1)$

#### LOC (Line of Code)

Links to the line of code.

- Type: Array
- Items: String
- Pattern: https:\\/\\/github\\.com\\/[^\\/]+\\/.*#L\\d+(-L\\d+)?\\)?$
- Min Items: 1


------

## Example

This sample json come the winning bot (Henry) report from the recent Canto Bot race. [view report](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/main/bot-henry-example.json)

Here is an example report gist that is generated from the winning bot (Henry) report from the recent Canto Bot race. [view gist](https://gist.github.com/code423n4/f2f9d9ea48372636f7d67e29c71c59bb#D%E2%80%9124)
