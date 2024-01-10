# Bot-Race-JSON-Schema

## JSON Schema

You can find the current schema, v0.1.0, [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.1.0/schema.json)

### Upcoming Version 0.3.0

A new version of the schema will replace v0.1.0 on **January 18th, 2024** and can be found [here](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/v0.3.0/schema.json).

**Changes**:

- `severity` is no longer an open string and must be one of ("High", "Medium", "Low", "Gas", "Refactoring", "NonCritical", "Disputed")
- `content` and `description` are now optional
- `content` is recommended to be in markdown format, such as wrapped in codeblocks (\`\`\`), but will still accept any string.
- `loc` must contain an absolute github url to line(s) of code.
- `loc` may continue to be wrapped as a link such as `[1](https://...#L1)`.
- `loc` can now be set to an empty array, `[]`, but only if `content is provided`

You can see an example of a valid, winning JSON report [here](./LightChaser-example.json)

If you want to test your report for both validation and markdown generation, you can use the new [C4 Botrace Utils](https://www.npmjs.com/package/@code4rena/botrace-utils) cli tool:

### Validation and Markdown Tooling
The following example will install the [C4 Botrace Utils](https://www.npmjs.com/package/@code4rena/botrace-utils) tool and:
- Validate a local `./report.json` against the latest Bot Race Schema version
- Render the markdown of the report to `./report.md` as it will be created via the submission process.

_Requires Node.js 18+_. See https://www.npmjs.com/package/@code4rena/botrace-utils for more options.

```
npx @code4rena/botrace-utils ./report.json > report.md
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
- Required

### Title

Title of the issue. Accepts plain strings or valid markdown.

- Type: String
- Required

### Description

Description of the issue. Accepts plain strings or valid markdown. May be set to `null`.

- Type: String | Null
- Required

### Gas Savings

Gas Savings.

- Type: Number | Null
- Optional

### Category

If category of the issue is clear it can be set as a plain string, otherwise if can be left empty

- Type: String | Null
- Optional

### Instances

An array of instances where the issues have occurred. This can be separated out for every instance or used as a block of instances. The instance count will be generated from the LOC.

- Type: Array

#### Content

Supports markdown strings and is recommended to be formatted as a codeblock (starts and ends with \`\`\`). Content is for code snippets, @audit tags, and file data. The field is optional as long as there is at least 1 entry in the `loc` array. It is recommended to only omit content, if the loc and instance description sufficiently describe the issue.

- Type: String | Null
- Required (Must be set when the loc array is empty)

#### LOC (Line of Code)

Absolute Github URLs including hash param deep links to lines of code.

- Type: Array
- Items: String
- Pattern: https:\\/\\/github\\.com\\/[^\\/]+\\/.*#L\\d+(-L\\d+)?\\)?$
- Min Items: 1 (May be an empty array as long as `content` is set)

##### Example Links
- `https://github.com/code-423n4/2024-01-renft/blob/main/bot-report.json#L20`
- `https://github.com/code-423n4/2024-01-renft/blob/main/bot-report.json#L20-L23`
- `[20](https://github.com/code-423n4/2024-01-renft/blob/main/bot-report.json#L20)`
- `[20-23](https://github.com/code-423n4/2024-01-renft/blob/main/bot-report.json#L20-L23)`

------

## Example

This sample json come the winning bot (LightChaser) report from the recent reNFT race. [view report](https://github.com/code-423n4/Bot-Race-JSON-Schema/blob/main/LightChaser-example.json)

Here is an example markdown file that is generated from the winning bot (LightChaser) report from the recent reNFT Bot race. [view bot-report.md](https://github.com/code-423n4/2024-01-renft/blob/main/bot-report.md)
