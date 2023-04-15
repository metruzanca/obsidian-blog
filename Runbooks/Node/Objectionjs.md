> The //FIXME comments are so I remember to remove the comment 😅

Get current DB:
```ts
console.log(await Model.knex().raw(` SELECT current_database();`)); //FIXME
```

Get raw SQL generated 
```ts
console.log({ SQL: query.clone().toKnexQuery().toSQL().toNative()}); //FIXME
```