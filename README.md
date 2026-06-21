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

### String exercises

```sh
set car toyota

set shape traingle nx
setnx shape traingle

set news "Todays's Headlines" ex 2
```

## eCommerce app

### Redis client

[docs](https://github.com/redis/node-redis)

## Hash

### Get and set

```sh
hset company name "My company" age 1995 revenue 5.3
hget company name
hget company revenue
hgetall company
```

### Delete hash

```sh
hexists comapany name # 1
del comapny
hdel company name
```

### Numbers in hashes

```sh
hincrby company age 10
hincrbyfloat company age 10.123
hkeys company
havalues comapny
```

## Design patterns

### Data types

#### Use hashes

- record has many attributes
- collection sorted in many different ways
- single record access

#### Do not use hashes

- record must be unique
- few attributes
- creates relation
- time series data

### User implementation

## Sets

### Basics

- Collection of unique strigs
- Add "S" to each previous commands

```sh
SMEMBERS colors red
SMEMBERS # all set values
SADD colors red # 1 or 0
```


### Unions

All diffrence values from multiple sets

```sh
SUNION colors1 colors2 colors3
```

### Intersections

```sh
SINTER colors1 colors2 colors3
```

### Differences

```sh
SDIFF colors1 colors2 colors3
```

### Checking element

```sh
SISMEMBER colors red
SMISMEMBER colors red # multiple
```

### Scanning a set

```sh
SCARD colors # cardinality
SSCAN colors # scan all elements
SSCAN colors 3 count 2
```

## Sorted sets

Mix of hash and set

### Add and remove

```sh
# add element
ZADD products 45 monitor
# get score
ZSCORE products monitor
# remove
ZREM products monitor
ZSCORE products monitor
```

### Finding range

```sh
DEL products
ZADD products 45 monitor
ZADD products 10 cpu
ZADD products 55 keyboard
# cardinality
ZCARD products
# count in range
ZCOUNT products 0 55
# exclude 55
ZCOUNT products 0 (55
# all
ZCOUNT products
```

### Removing first and last

```sh
ZPOPMIN products
ZPOPMAX products
```

### Update score

```sh
ZINCRBY products 15 cpu
```

### Querying sorted set

```sh
ZRANGE products 1 2
ZRANGE products 1 2 WITHSCORES
ZRANGE products 0 (55 BYSCORES WITHSCORES
```

## Sortes sets practice

### Use cases

- Tabulate the last or the most
- Create relation between sorted record

## From relational data to Redis

###
