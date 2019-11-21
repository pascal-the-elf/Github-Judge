# Github Judge
An Online Judge System That Use Github Repository As Problem Database.

## Database

### Database Structure
A Github repository follows below structure can be a database.
```
Repository/
  problems/
    a/
      001/
        problem.json
        input/
          0
          1
          2
        output/
          0
          1
          2
      002/
        problem.json
        input.txt
        output.txt
      ...
    b/
      001/
        problem.json
        input/
          0
          1
        output/
          0
          1
      ...
    c/
      123/
        problem.json
        input/
          0
          1
          2
          3
        output/
          0
          1
          2
          3
      ...
    ...
```
[Example Database](https://github.com/pascal-the-elf/Github-Judge-Database)

### problem.json

```javascript
{
    "Prefix": "a",                                        // problem prefix
    "No": "001",                                          // problem id
    "Name": "Hello!",                                     // problem name
    "Description": "輸入一個字串S，然後輸出Hello, S!",      // problem description
    "Input": "Jacob\nPascal",                             // sample input
    "Output": "Hello, Jacob!\nHello, Pascal!",            // sample output
    "Tests": [                                            // subtasks
        {
            "score": 20,                                  // subtask score
            "time": 1,                                    // time limit
            "memory": 524288,                             // memory limit
            "input": "input/0",                           // input file
            "output": "output/0",                         // output file
            "constraint": "no space"                      // subtask constraint
        },
        {
            "score": 30,
            "time": 1,
            "memory": 524288,
            "input": "input/1",
            "output": "output/1",
            "constraint": "S.length() ≦ 100"
        },
        {
            "score": 50,
            "time": 1,
            "memory": 524288,
            "input": "input/2",
            "output": "output/2",
            "constraint": "no additional constraint"
        }
    ]
}
```

## Judge
The RESTful Judge API supports HTTPS and CORS.
POST data (problem informations and source code) to API Endpoint and your code will be judged soon.

### API Endpoint
```
https://judge.pascaltheelf.workers.dev/
```

### Example
```javascript
var data = {
    problem: {
        owner: "pascal-the-elf",
        database: "Github-Judge-Database",
        prefix: "a",
        id: "001"
    },
    code: SOURCE_CODE
};

fetch("https://judge.pascaltheelf.workers.dev/", {
    method: "POST",
    body: JSON.stringify(data)
}).then(r => r.json()).then(console.log);

```

