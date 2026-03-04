## Краткое описание

#### Пример
Небольшой класс, реализующий функциональность, аналогичную функциональности оператора `cache`, но хранящий скешированные результаты на сервере memcached:

```parser3
@main[]
$m[^mcache::open[localhost]]
^m.cache[key2;10]{dt: $d[^date::now[]] ^d.sql-string[] ^sleep(3)}

@CLASS
mcache

@auto[]
$timeout(4) ^rem{ timeout, seconds }
$retry_on_timeout(false) ^rem{ retry cache lock attempts }

@open[connect-options]
$m[^memcached::open[$connect-options]]

@cache[key;expires;code][lock;i]
$result[$m.$key]
^if(!def $result){
	^rem{ not cached yet }
	$lock[${key}-lock]
	^while(!^m.add[$lock; $.value[$timeout] $.expires($timeout)]){
		^rem{ another process got the lock, waiting ... }
		^for[i](1;$timeout*5){
			^sleep(0.2)
			$result[$m.$key]
			^if(def $result){
				^break[]
			}
		}
		^if(def $result){
			^break[]
		}{
			^if(!$retry_on_timeout){
				^throw[$self.CLASS_NAME;Timeout while getting lock for key '$key']
			}
		}
	}
	^if(!def $result){
		^rem{ we got the lock, processing the code }
		^try{
			$result[$code]
			$m.[$key][ $.value[$result] $.expires($expires) ]
		}{}{
			^m.delete[$lock]
		}
	}
}
```
