# Execute a shell script
This activity provides your Flogo application with the ability to execute shell or bash scripts.

# Installation
```
flogo install github.com/iainharfield/flogo/activity/runshellscript
```

# Schema
## Inputs and Outputs:
```json
{
  "inputs":[
    {
      "name": "cmd",
      "type": "string",
      "required": true
    }
  ],
  "outputs": [
    {
      "name": "result",
      "type": "string"
    }
  ]
}
```

## Inputs: Schema of cmd parameter:
The activity expects the script to be executed put into JSON scema. The Schema contains the fully qualifies path and script name to execute which is manfdatory and the parameters to be passed in.  The activity is limeted to 20 parameters.

JSON schma example, execute test01.sh in local directory and passes in 3 parameters.  See example script below.
```
{
  "cmd":"./test01.sh",
  "params":"aaa bbb ccc"
}
```
## Output from the Activity:
The output is straight text returned from the script. See very simple example below.

## Configuration Example
```
{
    "id": "setQoS_3",
    "name": "Execute a shell script",
    "description": "Run a script",
    "activity": {
    "ref": "github.com/iainharfield/flogo/activity/runshellscript",
    "mappings": {
    "input": [
        {
            "type": "assign",
            "value": "$flow.command",
            "mapTo": "cmd"
        }
     ]
}
```
## Example bash script
#!/bin/bash
printf "test01 output: $1 $2 $3"