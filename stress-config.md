# Конфигурация стресс-тестов

Конфигурация стресс тестов задается в файлах в папке `stress`. Их формат основан на описанном в [configs.md](configs.md), но имеет несколько расширений:

* Добавляются типы `int<>` и `float<>`, которые могут иметь следующие варианты значений:
  * `<x>`&mdash; случайное число в диапазоне `[0; x)`
  * `<a; b>`&mdash; случайное число в диапазоне `[a; b]`
* Добавляется тип `string<>`, который может иметь следующие варианты значений:
  * `r"<regex>"`&mdash; равновероятная строка, соответствующая регулярному выражению (как в функции `rnd.next()` из `testlib`).

Файл состоит из нескольких секций. В секции `[stress/body]` содержится основная информация:

* Поле `generators: string[]` содержит список генераторов, каждый выбирается равновероятно.
* Поле `solutions: string[]` содержит список решений, которые необходимо стресс-тестировать.
* Поле `stress-time: int` содержит время на стресс-тест в миллисекундах или `-1`, если необходимо продолжать до бесконечности.
* Поле `time-limit: int` содержит лимит времени на один тест в миллисекундах (если отсутствует, то значение равно ограничению по времени на задачу)
* Поле `memory-limit: int` содержит лимит памяти на один тест в килобайтах (если отстутствует, то значение равно ограничению по памяти на задачу)

На каждый из генераторов должно быть по одной секции с таким же названием, как у генератора. Внутри секции в качестве полей должны присутствовать аргументы генератора, кроме `seed`: `seed` выбирается случайно. В этих секциях можно использовать описанные выше расширения.

Пример конфига:

~~~~~
[stress/body]
generators: string[] = ["gen1", "gen2"]
solutions: string[] = ["author", badSolution"]
stress-time: int = 120000
time-limit: int = 250

[gen1]
n: int<> = <1; 10>
m: int<> = <100>
chance: int = 42

[gen2]
str: string<> = r"[0-9]{1,3}"
maxQ: int = 20
~~~~~
