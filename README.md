# Example projects for `actuatorjs`

This is a repository containing example projects using [actuatorjs](https://github.com/actuatorjs/actuatorjs).

## Express

You can find a simple express API with an actuator instantiated in the [express](./express) folder.

This shows how to use both `SimpleHealthIndicator` and how to extend `AbstractHealthIndicator` for a simple `postgres` health check.

Try running `bun run dev` before starting the database with docker compose, then check out `http:localhost:3000/actuator/health`.
You should get:

```json
{"status":"DOWN","components":{"abstract-postgres":{"status":"DOWN","details":{"error":"connect ECONNREFUSED ::1:5432; connect ECONNREFUSED 127.0.0.1:5432"}},"simple-postgres":{"status":"DOWN","details":{"error":"connect ECONNREFUSED ::1:5432; connect ECONNREFUSED 127.0.0.1:5432"}}}}
```

Then try it after running `docker compose up -d`, and check the url again, you should get:

```json
{"status":"UP","components":{"simple-postgres":{"status":"UP"},"abstract-postgres":{"status":"UP"}}}
```
