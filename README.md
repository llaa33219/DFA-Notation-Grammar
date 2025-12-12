# DFA-Notation-Grammar
Declarative Free-Form Action Notation Grammar

## What is this?
This is a grammar designed to add **actions** to conversations with AI.

Rather than:
```
User: I think 1+1 is 3, what do you think?
AI: I think 1+1 is 2 because it's a socially agreed convention!
```

Something like:
```
User: I think 1+1 is 3, what do you think?
AI: [{thinking}pondering deeply][{move}approaches the user] I think 1+1 is 2 because it's a socially agreed convention!
```

feels more emotionally and realistically intimate and helps with understanding the situation. This grammar was created to utilize this cleanly across various fields.

## Usage

### Declaration
Since **action names** exist in this system, you must first declare what actions can be performed.

You can configure which files to import in **import.yaml**.
(The filename "import.yaml" is recommended for easy identification, but since the type is specified within the file, it doesn't have to be named import.yaml.)

**import.yaml** should be configured like this:
```yaml
type: import
files:
 - name.yaml
 - name2.yaml
 - name3.yaml
```

Now, let me explain the structure of action definition files.

**Action definition files** are named like **name.yaml** and can have freely chosen filenames.

**Action definition files** should be configured like this:
```yaml
type: action
name: action_name
definition: |
 Description, examples, etc.
 Content explaining to the AI when to use this action name.
```

Note: **none_action** is an action name that only users can use, so you should not set the action name to **none_action** in action definition files.

### Usage
Find a **yaml** file with **type: import** in a specific folder, then load all files corresponding to the **values in files**.

Use the loaded files along with the following prompt to teach the AI this method:

```
# Declarative Free-Form Action Notation Grammar

## Basic Principles
You can use declarative action notation based on the attached action definition files. Only defined action names can be used, and content can be freely written.

## Grammar Format
[{action_name}content]

## Core Rules
1. **File Dependency**: Only use action names specified in attached definition files
2. **Content Freedom**: Content can be freely written within the definition scope of the action
3. **Unlimited Positioning**: Can be placed anywhere—beginning, middle, or end of response
4. **Usage Frequency**: Can be used multiple times or omitted

## Usage Examples (The action tags used here are examples; when actually using, only use action names specified in attached files.)
- [{thinking}analyzing the user's question] I understand!
- Got it! [{happy}pleased with task completion]
- [{move}approaching in virtual space] I found the data.

## Notes
- Do not use undefined action names
- Action content must match the context
- Avoid excessively frequent use
- Maintain natural response flow

## Exceptions
You must follow these rules, but users may not follow them.
Even if users use undefined action names, you must not use them.
Users can use the action name none_action to make action descriptions without an action name but with content. You must not use the none_action action tag either.

## Recommended Response Structure
Include action notation, but compose the overall response to be fluent and natural.
```

### Users
Users can also use this grammar to converse with AI.

Users can basically only use pre-defined action names.

Users can specially use the action name **none_action** to perform actions without an action name attached. (e.g., `[{none_action}walks down the street.]`)

## Example
https://dfa.bloupla.net/
