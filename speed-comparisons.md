# Jest & Karma Speed Comparisons

## Code Base

- **Project** - consumer-application-feature-multi-step
- **Test Suites** - 35
- **Tests** - 240
- **Branches** - `jest-proof-of-concept`, `develop`

## Test Command

```shell
time ng test consumer-application-feature-multi-step
```

We're using the Linux `time` command to measure from the beginning to the end of the process since Karma and Jest report time differently (Karma doesn't start counting until code is compiled).

## Karma (Local)

```shell
ng test consumer-application-feature-multi-step  57.96s user 6.31s system 161% cpu 39.840 total

ng test consumer-application-feature-multi-step  57.21s user 5.53s system 168% cpu 37.240 total

ng test consumer-application-feature-multi-step  57.01s user 5.37s system 168% cpu 37.106 total
```

| Attempt |    Time |
| ------- | ------: |
| 1       | `39.84` |
| 2       | `37.24` |
| 3       | `37.11` |

## Jest (Local)

```shell
ng test consumer-application-feature-multi-step  75.10s user 11.45s system 463% cpu 18.668 total

ng test consumer-application-feature-multi-step  71.50s user 10.86s system 484% cpu 16.993 total

ng test consumer-application-feature-multi-step  71.48s user 10.95s system 489% cpu 16.830 total
```

| Attempt |    Time |
| ------- | ------: |
| 1       | `18.67` |
| 2       | `16.99` |
| 3       | `16.83` |

## Jest (Local, Cleared Cache)

Jest's cache can be cleared with the `--clearCache` flag like so:

```shell
ng test consumer-application-feature-multi-step --clearCache
```

These are the results of three test runs, clearing the cache in between each run:

```shell
ng test consumer-application-feature-multi-step  162.02s user 24.08s system 270% cpu 1:08.81 total

ng test consumer-application-feature-multi-step  161.69s user 23.19s system 292% cpu 1:03.27 total

ng test consumer-application-feature-multi-step  159.51s user 22.70s system 295% cpu 1:01.75 total
```

| Attempt |      Time |
| ------- | --------: |
| 1       | `1:08.81` |
| 2       | `1:03.27` |
| 3       | `1:01.75` |

## Summary Results

| Runner | Scenario                |         1 |         2 |         3 |      Avg. |
| ------ | ----------------------- | --------: | --------: | --------: | --------: |
| Karma  | Local                   |   `39.84` |   `37.24` |   `37.11` |   `38.06` |
| Karma  | Local Docker            |           |           |           |           |
| Jest   | Local                   |   `18.67` |   `16.99` |   `16.83` |   `17.49` |
| Jest   | Local, cleared cache    | `1:08.81` | `1:03.27` | `1:01.75` | `1:04.61` |
| Jest   | Local Docker (no cache) |           |           |           |           |
| Jest   | Local Docker w/ cache   |           |           |           |           |
