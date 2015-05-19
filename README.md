# Smoothie
Cute web framework for Erlang built on top of Cowboy.

----
## Installing

In rebar.config:

```Erlang
{smoothie,  ".*", {git, "git://github.com/myua/smoothie", {tag, "master"} }}
```

----
## Usage

Starting http server:

```Erlang
sm:start_http([
  {ranch, [{port, 3000}]},
  {cowboy, [
    {nb_acceptors, 100},
    {protocol, [{compress, true}]}
  ]},
  {routes, [
    sm:route("/",         {priv_file, myapp, "static/index.html"}),
    sm:route("/js/[...]", {priv_dir, "staric/js"}),
    sm:route("/ws/[...]", {websocket, myhandler, sm_protocol_bert})
  ]}
])
```

More about configuring Ranch TCP transport and Cowboy protocol: 
[ranch\_tcp](http://ninenines.eu/docs/en/ranch/HEAD/manual/ranch_tcp/), 
[cowboy\_protocol](http://ninenines.eu/docs/en/cowboy/HEAD/manual/cowboy_protocol/).

More about routing:
[Routing](http://ninenines.eu/docs/en/cowboy/HEAD/guide/routing), 
[Constraints](http://ninenines.eu/docs/en/cowboy/HEAD/guide/constraints), 
[Static files](http://ninenines.eu/docs/en/cowboy/HEAD/guide/static_files).
