### Graphql
How to fetch github API
1. Define token with `const token = ...`


2. Define a query 
``` js
q = `{
    repository(name: "logan_admin", owner: "armandasalmd") {
        name
        forkCount
    }
}`
```

3. Run a fetch
``` js
fetch("https://api.github.com/graphql",
    {
        method: "POST",
        headers: { "Authorization": `Token ${token}` },
        body: JSON.stringify({ query: q })
    }
).then(a=> a.json()).then(console.log)
```

#### GraphQL playground
https://lucasconstantino.github.io/graphiql-online/
