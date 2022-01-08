## Indroduction
**【Condition】** app can set rue and false branches, it will choose one of the branches according to the actual result.


<iframe 
    width="1280" 
    height="720" 
    src="https://www.youtube.com/embed/9bxxxI-P6hE"  frameborder="0" 
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
    </iframe>

## Parameter
**【Expr】**  parameter is used to set the conditional expression, such as ```1==2``` or use the variable expression ```"{{xxx.Output.0}}" ~= "test"```.

| Expr | Instruction                                                  |
| ---- | ------------------------------------------------------------ |
| ==   | Equal. If you want to compare strings, you need to double quotes, such as: ```"{{xxx.Output.0}}" == "hello"``` |
| ~=   | Not equal.                                                   |
| >    | Great than.                                                  |
| >=   | Great then and equal to.                                     |
| <    | Little than.                                                 |
| <=   | Little than and equal to.                                    |

The ```Condition``` app's ```Expr``` field references the output of ```Lua Function``` to make conditional expression.

<img src="https://public-pic-1251784084.cos.ap-guangzhou.myqcloud.com/image-20210314151941677.png" alt="image-20210314151941677" style="zoom:50%;" />

## Workflow Json File

```json
{
    "Apps": [
        {
            "Connections": [
                "4ikqch2c"
            ],
            "Desc": "",
            "InstId": "9zretas33r",
            "Name": "Start",
            "Parameters": {},
            "Positions": [
                99,
                102
            ],
            "Runtime": {
                "CallCount": 0,
                "EndAt": "2021-03-14 15:25:32",
                "Error": "",
                "Index": 0,
                "Output": [
                    null
                ],
                "Parameters": {},
                "StartAt": "2021-03-14 15:25:32",
                "Status": "done"
            },
            "Template": "start-trigger"
        },
        {
            "Connections": [
                "xzu8pp36m"
            ],
            "Desc": "",
            "InstId": "4ikqch2c",
            "Name": "Lua Function",
            "Parameters": {
                "code": "return 'hello'",
                "param": "",
                "timeout": 60
            },
            "Positions": [
                137,
                217
            ],
            "Runtime": {
                "CallCount": 1,
                "EndAt": "2021-03-14 15:25:33",
                "Error": "",
                "Index": 0,
                "Output": [
                    "hello"
                ],
                "Parameters": {
                    "code": "return 'hello'",
                    "param": "",
                    "timeout": 60
                },
                "StartAt": "2021-03-14 15:25:33",
                "Status": "done"
            },
            "Template": "lua-function"
        },
        {
            "Connections": [
                "1pa7c70gbw",
                "vi2az8si8y"
            ],
            "Desc": "",
            "InstId": "xzu8pp36m",
            "Name": "Condition",
            "Parameters": {
                "expr": "\"{{4ikqch2c.Output.0}}\"==\"hello world\"",
                "false": "vi2az8si8y",
                "true": "1pa7c70gbw"
            },
            "Positions": [
                266,
                353
            ],
            "Runtime": {
                "CallCount": 1,
                "EndAt": "2021-03-14 15:25:33",
                "Error": "",
                "Index": 0,
                "Output": [
                    false
                ],
                "Parameters": {
                    "expr": "\"hello\"==\"hello world\"",
                    "false": "vi2az8si8y",
                    "true": "1pa7c70gbw"
                },
                "StartAt": "2021-03-14 15:25:33",
                "Status": "done"
            },
            "Template": "condition"
        },
        {
            "Connections": [],
            "Desc": "",
            "InstId": "vi2az8si8y",
            "Name": "false branch",
            "Parameters": {
                "code": "print(\"false\")",
                "params": [],
                "timeout": 60,
                "type": "cmd"
            },
            "Positions": [
                491,
                267
            ],
            "Runtime": {
                "CallCount": 1,
                "EndAt": "2021-03-14 15:25:33",
                "Error": "",
                "Index": 0,
                "Output": [
                    "false\n"
                ],
                "Parameters": {
                    "code": "print(\"false\")",
                    "params": null,
                    "timeout": 60,
                    "type": "cmd"
                },
                "StartAt": "2021-03-14 15:25:33",
                "Status": "done"
            },
            "Template": "python-script"
        },
        {
            "Connections": [],
            "Desc": "",
            "InstId": "1pa7c70gbw",
            "Name": "true branch",
            "Parameters": {
                "code": "print(\"true\")",
                "params": [],
                "timeout": 60,
                "type": "cmd"
            },
            "Positions": [
                520,
                436
            ],
            "Runtime": {
                "CallCount": 0,
                "EndAt": "",
                "Error": "",
                "Index": 0,
                "Output": [],
                "Parameters": {
                    "code": "",
                    "params": [],
                    "timeout": 60,
                    "type": "cmd"
                },
                "StartAt": "",
                "Status": "todo"
            },
            "Template": "python-script"
        }
    ],
    "Creator": "",
    "Desc": "",
    "EndAppInstId": "",
    "Engine": "default",
    "Id": 0,
    "Name": "Unknown",
    "StartAppInstId": "",
    "Status": "done"
}
```

