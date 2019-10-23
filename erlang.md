# Erlang

## Why we chose erlang over java, scala, go and c
Link: [https://www.youtube.com/watch?v=OcExABAAsXs](https://www.youtube.com/watch?v=OcExABAAsXs)

- Release speed
- Is it product/market fit
- Quick to scale
- Never enough time

**Unless**
- You are well funded
- A lifestyle business
- You are incredibly lucky

Sometimes quality takes a backseat

### Monolith
That's version one
- Like most companies, starting with monolith
- Python agent, nodejs app, mongoDB
- 2 nodes for HA

### Microservices
Pros:
- Isolation
- Indepently deployable
- Flexibility (lang, tech)
- Team alignment and ownership

Impediments
- Requires infra
- Packaging, deployment, hosting
- COmmunication - bus, http
- Service discovery

### Erlang: state and concurrency
- no shared state
- actor model
- communication via messages
- Like human interaction

### Erlang: Supervisors
- Supervise worker processes
- Restart upon crash
- Fault tolerance
- Independently configurable
- Different layers of protection

### Erlang: Behavior
- Formalized common patterns
- Battle hardened
- Reliable systems made easy
- Prevent race condtions
- Handle partial failures

### Erlang: visibility
- SImple to inspect live systems
- Even via GUI and shell
- Support interaction: sending messages

### Erlang: Applications as microservices
- BEAM lika an OS
- App independent start/stop
- Different deployment configs
- Like a standalone microservice

**Distribution at its core**
**Live code reload**

### Elixir
- New kid
- ALl power of erlang/OTP BEAM
- Ruby sugar for the kids
- Massively growing

## Learn Erlang in one video
Link: [https://www.youtube.com/watch?v=IEhwc2q1zG4](https://www.youtube.com/watch?v=IEhwc2q1zG4)

In erlang, we have `modules`. Every module will have the following:
```
-module(tut).
```
For importing, you do the following:
```
-import(string, [len/1, concat/2, chr/2, substr/3]).
```
`len/1` means function `len` with `1` attribute being sent

The statements in erlang end with a period `.`

After this, you export the functions which you can call by importing this module by:
```
-export([hello_world/0]).
```

Writing the hello_world function as follows:
```
hello_world() ->
    io:fwrite("Hello World\n").
```

Adding another function is simple as well, just change the export to as follows:
```
-export([hello_world/0, add/2]).
```
and then add another function as follows:
```
add(A, B) ->
    hello_world(),
    A + B.
```

Function overloading is allowed just like any other language. Hence can export `add/2` and `add/3` both.

