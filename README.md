# Redis: The Complete Developer's Guide

## Getting started

### Why Redis

- Data stored in memory
- Data organized in simple structures
- Simple feature set

### Initial setup

- cloud on [redis](redis.com)
- local

### Redis commands

- rbook.cloud
- local machine
- redis cli

### rBook locally

_npx rbook_ and navigate to http://localhost:3050

## Save and get data commands

### Basic commands

```sh
docker exec -it redis redis-cli
SET message "ciao"
GET message
```

### Documentation

[Docs](https://redis.io/docs/latest/commands/)

### Variations of SET

```sh
set color red
set color greet get #.return prev value
set colot blue NX # set only in key not exists
```

### Expiration options

```sh
set color red ex 2 # expires after 2s
```

### Expiration use cases

- API checks Redis cache
- If empty, API reads data from DB and updates cache
- Expiration invalidates cahce in order to update cache regurally

### Setting multiple keys

```sh
setex color 2 red # set with expiration
setnx color red # set var only if i does not exist
mset color red car toyota # multiple vars set
msetnx color red car toyota # if any keys exist, no set is done

```

### Get and MGet

```sh
mget color car # multiple get
```

### String ranges

```sh
del color # delete a key
getrange color 0 3 # get substring
setrange color 2 blue # replace from char
```

### Numbers

Redis stores numbers as strings: using these commands on strings is not possible

```sh
set age 20
incr age # 21
decr age # 20
incrby age 10 # 30
decrby age 10 # 20
incrbyfloat age 1.123
```
