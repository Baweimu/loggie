# Adjusting Message Formats

Loggie comes preconfigured with some default base styles for messages and their various appendages (timestamps, domains, etc.).

If you'd like to change how some of this stuff appears in a message, you can change that by going to **Project Settings -> Loggie -> Formats**.

![](assets/screenshots/formats.png)

Alternatively, if you are [using Custom Settings](docs/customization/CUSTOM_SETTINGS), you can set new values for the format variables.
For example, you can include the following in your `load` method and edit the values:

```
	format_timestamp = "[{day}.{month}.{year} {hour}:{minute}:{second}]"
	format_info_msg = "{msg}"
	format_notice_msg = "[b][color=cyan][NOTICE]:[/color][/b] {msg}"
	format_warning_msg = "[b][color=orange][WARN]:[/color][/b] {msg}"
	format_error_msg = "[b][color=red][ERROR]:[/color][/b] {msg}"
	format_debug_msg = "[b][color=pink][DEBUG]:[/color][/b] {msg}"
	format_header = "[b][i]{msg}[/i][/b]"
	format_domain_prefix = "[b]({domain})[/b] {msg}"
```

It is important to know which `{variables}` are available to use in each of the formats, so let's dive deeper into how each format works below.

---
#### Timestamp

Default format: `"[{day}.{month}.{year} {hour}:{minute}:{second}]"`

For a message printed on 25th April 2025, at 1:40 PM, you'll see:
Example: `[25.04.2025 13:40:23]`

| variable |
| -------- |
| {day}    |
| {month}  |
| {year}   |
| {hour}   |
| {minute} |
| {second} |
All of these variables are provided as strings which contain a number.
Frontal padding with a 0 is applied if the number is single digit.
*(e.g. '04' instead of '4' for month April).*

---
#### Stack Trace Entry

Default format:
```gdscript
"{index}: [color=#ff7085]func[/color] [color=#53b1c3][b]{fn_name}[/b]:{line}[/color] [color=slate_gray][i](in {source_path})[/i][/color]"
```

| variable      | meaning                                                                                                                                                                       |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| {index}       | The index of the stack frame in the entire stack. <br>The lower this number is, the further away the call to that function was from the original call that started the stack. |
| {fn_name}     | The name of the function that was called.                                                                                                                                     |
| {line}        | The number where the line of code calling the function is located in the source script.                                                                                       |
| {source_path} | The path to the script which is the source of this function call.                                                                                                             |

---

#### Error Message

Default format: `"[b][color=red][ERROR]:[/color][/b] {msg}"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Warning Message

Default format: `"[b][color=orange][WARN]:[/color][/b] {msg}"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Notice Message

Default format: `"[b][color=cyan][NOTICE]:[/color][/b] {msg}"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Info Message

Default format: `"{msg}"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Debug Message

Default format: `"[b][color=pink][DEBUG]:[/color][/b] {msg}"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Header

Default format: `"[b][i]{msg}[/i][/b]"`

| variable | meaning                                  |
| -------- | ---------------------------------------- |
| {msg}    | The content of the message being logged. |

---
#### Domain Prefix

Default format: `"[b]({domain})[/b] {msg}"`

| variable | meaning                                         |
| -------- | ----------------------------------------------- |
| {msg}    | The content of the message being logged.        |
| {domain} | The name of the domain this message belongs to. |

---
#### Related Articles:
👀 **► [Browse All Features](docs/ALL_FEATURES.md)**
📚 ► [Using Custom LoggieSettings](docs/customization/CUSTOM_SETTINGS.md)