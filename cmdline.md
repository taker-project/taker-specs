# Описание команд утилиты take:


**`take run [ -t <time-limit> ] [ -m <memory-limit> ] [ -i <input-file> ] [ -o <output-file> ] <file> <parameters...>`**

Запуск `<file>` с параметрами `<parameters...>`. `<time-limit>` указывается в миллисекундах, `<memory-limit>`&mdash; в килобайтах.


**`take compile <file> [ -t <time-limit> ] [ -m <memory-limit> ] [ -I <include-paths> ] [ -l <language> ]`**

Компиляция `<file>`. `<time-limit>` указывается в миллисекундах, `<memory-limit>`&mdash; в килобайтах. `<include-paths>`&mdash; пути до подключаемых файлов, разделяются символом `;`. `<language>`&mdash; язык, если не указан, выбирается автоматически.

Возможные языки: `pas.fpc`, `pas.objfpc`, `pas.dpr`, `c.gcc`, `c.gcc11`, `cpp.g++`, `cpp.g++11`, `cpp.g++14`, `cpp.g++17`, `java.8`, `py.2`, `py.3`.

**`take create <dir-name> [ -i ]`**

Создает новую задачу в папке `<dir-name>`. Ключ `-i` предполагает создание не минимальной задачи, а с интерактивной настройкой некоторых параметров.


**`take option --list`**  
**`take option --set <name> <value>`**

* Ключ `--list` показывает все опции
* Ключ `--set` устанавливает опцию `<name>` в `<value>`. Поддерживается:  

  * `time-limit` (default: `2000`)
  * `memory-limit` (default: `131072`)
  * `input-file` (default: `stdin`)
  * `output-file` (default: `stdout`)
  * `strict` (default: `true`) -- поведение похоже на Are tests well-formed? на Polygon


**`take const --list`**  
**`take const --set <name> <type> <value>`**  
**`take const --unset <name>`**

Работает аналогично `take option`, но служит для установки ограничений/прочих универсальных констант. `<type>` может быть `int`, `float`, `char`, `string`, `int[]`, `float[]`, `char[]`, `string[]`. Как задавать значения, смотрите **TODO**.  
Ключ `--unset` удаляет константу.


**`take gen --add <filename> <parameters...>`**  
**`take gen --del <filename>`**  
**`take gen --add-param <filename> <parameters...>`**  
**`take gen --del-param <filename> <parameters...>`**  
**`take gen --build [<filenames...>] [ -j <process-count> ]`**  
**`take gen --clean`**

* Ключ `--add` создает генератор с именем файла `<filename>` и параметрами `<parameters...>` Параметры указываются по типу `<name>:<type>[=<value>]` (`<type>` может быть `int`, `float`, `char`, `string`, `int[]`, `float[]`, `char[]`, `string[]`). Если задано `[=<value>]`, то оно становится значением по умолчанию для этого параметра.
* Ключ `--del` удаляет генератор.
* Ключ `--add-param` добавляет к генератору параметры `<parameters...>`, разделенные пробелом. Параметры также указываются по типу `<name>:<type>[=<value>]`.
* Ключ `--del-param` удаляет параметры генератора (`<parameters...>`&mdash; список имен удаляемых параметров).
* Ключ `--build` компилирует генераторы (если `<filename...>` не задан, компилирует все генераторы).
* Ключ `--clean` чистит папку с генераторами от лишнего.


**`take checker --new`**  
**`take checker --default <checker-name>`**  
**`take checker --test`**  
**`take checker --build`**  
**`take checker --clean`**

* Ключ `--new` создает новый чекер.
* Ключ `--default` создает стандартный чекер (из тех, которые лежат в примерах testlib).
* Ключ `--test` запускает тесты для чекера.
* Ключ `--build` собирает чекер.
* Ключ `--clean` чистит <s>орлу перья</s> папку с чекерами от лишнего.


**`take validator --new`**  
**`take validator --del`**  
**`take validator --test`**  
**`take validator --build`**  
**`take validator --clean`**

* Ключ `--new` создает новый валидатор.
* Ключ `--del` убирает валидатор.
* Ключ `--test` запускает тесты для валидатора.
* Ключ `--build` собирает валидатор.
* Ключ `--clean` чистит папку с валидаторами от лишнего.


**`take testsets --add <testset>`**  
**`take testsets --del <testset>`**  
**`take testsets --status [<testsets...>]`**  
**`take testsets --enable [<testsets...>]`**  
**`take testsets --disable [<testsets...>]`**  
**`take testsets --list`**

* Ключ `--add` создает новый тестсет.
* Ключ `--del` удаляет тестсет.
* Ключ `--status` показывает статус тестсетов (будут ли эти тестсеты использоваться при сборке пакетов). Если тестсетов не указано, показывает статус всех.
* Ключ `--enable` включает тестсеты для сборки пакетов. Если тестсетов не указано, будут включены все.
* Ключ `--disable` действует похоже на `--enable`, но выключает.
* Ключ `--list` показывает все доступные тестсеты.


**`take tests --gen <tests> [ -j <process-count> ]`**  
**`take tests --degen <tests>`**  
**`take tests --clean`**

`<tests>` задаются в виде набора аргументов, разделенных пробелом. Каждый аргумент задается одним из двух способов  

* `testset:testnums`
* `testset`

`testset` обозначает имя тестсета, `testnums`&mdash; номера тестов в формате вроде `1,2,3..15,18,24..26,29`. Запись в форме без `testnums` обозначает генерацию всех тестов. Запись `testset:` не генерит ничего (надо ли это кому-нибудь?)

* Ключ `--gen` генерирует заданные тесты (если тесты не заданы, то генерирует все тесты **включенных** тестсетов).
* Ключ `--degen` чистит каталог от заданных тестов (если тесты не заданы, удаляет все тесты **включенных** тестсетов).
* Ключ `--clean` выполняет полную очистку каталога с тестами от лишнего.


**`take solution --add <filename> <tags> [ -l <language> ]`**  
**`take solution --del <filename>`**  
**`take solution --get-tags <filename>`**  
**`take solution --set-tags <filename> <tags>`**  
**`take solution --run <filenames...> [ -t <tests> ]`**

`<tags>`&mdash; какие вердикты должно получать решение (через запятую). Например, `WA,RE,AC` (поддерживаются `AC`, `WA`, `PE`, `TL`, `ML`, `RE`). Либо `MAIN` (без никаких других тегов), если это авторское решение.

* Ключ `--add` добавляет решение с тэгами `<tags>`. `-l` позволяет указать язык, иначе он будет выбран автоматически. Возможные языки смотрите в описании `make compile`.
* Ключ `--del` удаляет решение.
* Ключ `--get-tags` получает тэги решения.
* Ключ `--set-tags` устанавливает тэги для решения.
* Ключ `--run` запускает решения `<filenames...>` на тестах `<tests>`. `<tests>` задаются так же, как описано выше; ключ `-t` разделяет решения и тесты. Если ключа `-t` нет, тестируется на всех тестах **включенных** тестсетов. Если есть ключ `-t`, а тестов нет, то тестить ни на каких тестах (надо ли это кому нибудь?)


**`take statement --add <lang>`**  
**`take statement --del <lang>`**  
**`take statement --build [<lang>] [ -j <process-count> ]`**  
**`take statement --clean`**

* Ключ `--add` добавляет условие на языке `<lang>`.
* Ключ `--del` удаляет условие на языке `<lang>`.
* Ключ `--build` собирает условие на языке `<lang>` (если не указано, то на всех).
* Ключ `--clean` чистит каталог от файлов сборки.

`<lang>`&mdash; (пока что) один из `en`, `ru`


**`take stress <filename> [ -j <process-count> ]`**

Запускает стресс-тест с названием файла конфигурации `<filename>`.


**`take refresh`**

Обновляет `makefil`'ы и прочее из конфигов.


**`take verify`**

Верификация задачи (прогон всех решений на соответствие тегам, валидаторов, чекеров по авторским тестам).


**`take build [ -j <process-count> ] [ -v ]`**

Сборка задачи полностью. Ключ `-v` запускает дополнительно верификацию.


**`take export [ --tester | --polygon ]`**

Экспорт пакета с задачей. `--tester`&mdash; для Тестера, `--polygon`&mdash; в пакет, похожий на пакет Polygon.


**`take clean`**

Очистка каталога задачи от лишнего.
