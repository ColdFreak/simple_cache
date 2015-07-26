To build this code, run the following command:

erlc -o ./ebin ./src/*.erl

To run the program, first start Erlang like this:

erl -pa ./ebin

Then, run the following in the Erlang shell:

1> application:start(simple_cache).
ok

2> simple_cache:insert(1, "bingbing").
true

3> simple_cache:lookup(1).
{ok,"bingbing"}

%% 30秒後キャッシュから削除されたため
4> simple_cache:lookup(1).
{error,not_found}
