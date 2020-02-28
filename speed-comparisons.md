# Jest & Karma Speed Comparisons

- [Jest & Karma Speed Comparisons](#jest--karma-speed-comparisons)
  - [Results](#results)
    - [Angular 9](#angular-9)
    - [Angular 8](#angular-8)
  - [Details](#details)
    - [Code Base](#code-base)
    - [Test Command](#test-command)
    - [Clearing Jest's Cache](#clearing-jests-cache)
  - [Output of Individual Test Runs](#output-of-individual-test-runs)
    - [Angular 9](#angular-9-1)
      - [Jest (Local)](#jest-local)
      - [Jest (Local, cleared cache)](#jest-local-cleared-cache)
      - [Jest (Local, Docker)](#jest-local-docker)
      - [Jest (Local, Docker, cleared cache)](#jest-local-docker-cleared-cache)
    - [Angular 8](#angular-8-1)
      - [Karma (Local)](#karma-local)
      - [Karma (Local, Docker)](#karma-local-docker)
      - [Jest (Local)](#jest-local-1)
      - [Jest (Local, cleared cache)](#jest-local-cleared-cache-1)
      - [Jest (Local, Docker)](#jest-local-docker-1)
      - [Jest (Local, Docker, cleared cache)](#jest-local-docker-cleared-cache-1)

## Results

### Angular 9

| Runner | Scenario                     |         1 |         2 |         3 |      Avg. |
| ------ | ---------------------------- | --------: | --------: | --------: | --------: |
| Karma  | Local                        |           |           |           |           |
| Karma  | Local, Docker                |           |           |           |           |
| Jest   | Local                        |   `15.76` |   `14.43` |   `14.75` |   `14.98` |
| Jest   | Local, cleared cache         | `1:05.33` | `1:02.56` | `1:04.53` | `1:04.14` |
| Jest   | Local, Docker                |   `22.20` |   `21.27` |   `20.00` |   `21.16` |
| Jest   | Local, Docker, cleared cache |   `48.88` |   `53.44` |   `52.52` |   `51.61` |

### Angular 8

| Runner | Scenario                     |         1 |         2 |         3 |      Avg. |
| ------ | ---------------------------- | --------: | --------: | --------: | --------: |
| Karma  | Local                        |   `39.84` |   `37.24` |   `37.11` |   `38.06` |
| Karma  | Local, Docker                |   `59.99` | `1:05.34` | `1:00.48` | `1:01.94` |
| Jest   | Local                        |   `18.67` |   `16.99` |   `16.83` |   `17.49` |
| Jest   | Local, cleared cache         | `1:08.81` | `1:03.27` | `1:01.75` | `1:04.61` |
| Jest   | Local, Docker                |   `20.26` |   `18.84` |   `17.86` |   `18.99` |
| Jest   | Local, Docker, cleared cache |   `42.04` |   `45.88` |   `43.40` |   `43.77` |

## Details

### Code Base

- **Project** - consumer-application-feature-multi-step
- **Test Suites** - 35
- **Tests** - 240
- **Branches** - `jest-proof-of-concept`, `develop`

### Test Command

```shell
time ng test consumer-application-feature-multi-step
```

We're using the Linux `time` command to measure from the beginning to the end of the process since Karma and Jest report time differently (Karma doesn't start counting until code is compiled).

### Clearing Jest's Cache

Jest's cache can be cleared with the `--clearCache` flag like so:

```shell
ng test consumer-application-feature-multi-step --clearCache
```

All of the test scenarios labeled "cleared cache" mean that I cleared the cache between each test run.

## Output of Individual Test Runs

### Angular 9

#### Jest (Local)

```shell
ng test consumer-application-feature-multi-step  41.26s user 5.14s system 294% cpu 15.762 total

ng test consumer-application-feature-multi-step  36.12s user 5.18s system 286% cpu 14.429 total

ng test consumer-application-feature-multi-step  34.89s user 5.36s system 272% cpu 14.747 total
```

#### Jest (Local, cleared cache)

```shell
ng test consumer-application-feature-multi-step  92.72s user 13.12s system 162% cpu 1:05.33 total

ng test consumer-application-feature-multi-step  90.97s user 12.27s system 165% cpu 1:02.56 total

ng test consumer-application-feature-multi-step  103.66s user 14.89s system 183% cpu 1:04.53 total
```

#### Jest (Local, Docker)

```shell
real    0m22.196s
user    0m35.986s
sys     0m7.549s

real    0m21.271s
user    1m29.733s
sys     0m16.195s

real    0m20.002s
user    1m6.438s
sys     0m12.169s
```

#### Jest (Local, Docker, cleared cache)

```shell
real    0m48.883s
user    2m59.136s
sys     0m39.458s

real    0m53.440s
user    3m1.907s
sys     0m50.752s

real    0m52.521s
user    2m57.339s
sys     0m58.312s
```

### Angular 8

#### Karma (Local)

```shell
ng test consumer-application-feature-multi-step  57.96s user 6.31s system 161% cpu 39.840 total

ng test consumer-application-feature-multi-step  57.21s user 5.53s system 168% cpu 37.240 total

ng test consumer-application-feature-multi-step  57.01s user 5.37s system 168% cpu 37.106 total
```

#### Karma (Local, Docker)

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

#### Jest (Local)

```shell
ng test consumer-application-feature-multi-step  75.10s user 11.45s system 463% cpu 18.668 total

ng test consumer-application-feature-multi-step  71.50s user 10.86s system 484% cpu 16.993 total

ng test consumer-application-feature-multi-step  71.48s user 10.95s system 489% cpu 16.830 total
```

#### Jest (Local, cleared cache)

```shell
ng test consumer-application-feature-multi-step  162.02s user 24.08s system 270% cpu 1:08.81 total

ng test consumer-application-feature-multi-step  161.69s user 23.19s system 292% cpu 1:03.27 total

ng test consumer-application-feature-multi-step  159.51s user 22.70s system 295% cpu 1:01.75 total
```

#### Jest (Local, Docker)

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

#### Jest (Local, Docker, cleared cache)

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
