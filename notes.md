# Migration notes

It looks like by default in Docker jest stores the cache in `/tmp/jest_0`:

```shell
> ng test "consumer-application-feature-multi-step" "--clearCache"

Cleared /tmp/jest_0
```
