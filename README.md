To build this code, run the following command:

`erlc -o ./ebin ./src/*.erl`

To run the program, first start Erlang like this:

`erl -pa ./ebin`

Then, run the following in the Erlang shell:

```
1> application:start(simple_cache).
ok
2> simple_cache:insert(1, "bingbing").
true
3> simple_cache:lookup(1).
{ok,"bingbing"}
4> %% 30秒後キャッシュから削除されたため
4> simple_cache:lookup(1).
{error,not_found}
```

redbugでデバッグの一例

```
66> redbug:start("sc_element:handle_cast(delete, _) ->return;stack", [ {time, 10000}]).
{42,1}
67> simple_cache:delete(9).
ok

% 22:37:48 <0.5429.0>(dead)
% sc_element:handle_cast(delete, {state,"mike",86400,63605513944})
  proc_lib:init_p_do_apply/3

% 22:37:48 <0.5429.0>(dead)
% sc_element:handle_cast/2 -> {stop,normal,{state,"mike",86400,63605513944}}
redbug done, timeout - 1
```
