To build this code, run the following command:

erlc -o ./ebin ./src/*.erl

To run the program, first start Erlang like this:

erl -pa ./ebin

Then, run the following in the Erlang shell:

1> application:start(simple_cache).
ok
2> simple_cache:insert(1, "foo").
true

