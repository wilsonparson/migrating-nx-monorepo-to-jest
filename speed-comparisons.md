# Jest & Karma Speed Comparisons

| Runner | Scenario                     |         1 |         2 |         3 |      Avg. |
| ------ | ---------------------------- | --------: | --------: | --------: | --------: |
| Karma  | Local                        |   `39.84` |   `37.24` |   `37.11` |   `38.06` |
| Karma  | Local, Docker                |   `59.99` | `1:05.34` | `1:00.48` | `1:01.94` |
| Jest   | Local                        |   `18.67` |   `16.99` |   `16.83` |   `17.49` |
| Jest   | Local, cleared cache         | `1:08.81` | `1:03.27` | `1:01.75` | `1:04.61` |
| Jest   | Local, Docker                |   `20.26` |   `18.84` |   `17.86` |   `18.99` |
| Jest   | Local, Docker, cleared cache |   `42.04` |   `45.88` |   `43.40` |   `43.77` |

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

## Karma (Local, Docker)

```shell
real    0m59.982s
user    1m14.943s
sys     0m13.168s

real    1m5.450s
user    1m19.685s
sys     0m14.727s

real    1m0.480s
user    1m15.836s
sys     0m13.671s
```

## Jest (Local)

```shell
ng test consumer-application-feature-multi-step  75.10s user 11.45s system 463% cpu 18.668 total

ng test consumer-application-feature-multi-step  71.50s user 10.86s system 484% cpu 16.993 total

ng test consumer-application-feature-multi-step  71.48s user 10.95s system 489% cpu 16.830 total
```

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

## Jest (Local Docker w/ cache)

```
real    0m20.264s
user    0m47.148s
sys     0m9.262s

real    0m18.838s
user    0m48.879s
sys     0m9.081s

real    0m17.864s
user    0m59.507s
sys     0m11.731s
```

## Jest (Local Docker, cleared cache)

```
real    0m42.036s
user    2m26.939s
sys     0m39.761s

real    0m45.879s
user    2m31.435s
sys     0m44.920s

real    0m43.399s
user    2m26.750s
sys     0m41.127s
```
