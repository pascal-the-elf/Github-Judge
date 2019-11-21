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

```json
{
    "Prefix": "a",
    "No": "001",
    "Name": "Hello!",
    "Description": "輸入一個字串S，然後輸出Hello, S!",
    "Input": "Jacob\nPascal",
    "Output": "Hello, Jacob!\nHello, Pascal!",
    "Tests": [
        {
            "score": 20,
            "time": 1,
            "memory": 524288,
            "input": "input/0",
            "output": "output/0",
            "constraint": "S無空格"
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
            "constraint": "無其他條件"
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

