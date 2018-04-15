# Главный файл конфигурации

Главный файл конфигурации находится в `Takefile`. Он использует формат, описанный в [configs.md](configs.md). Структура этого файла следующая:

~~~~~
[options] # Основные опции задачи
time-limit: int = 2000 
memory-limit: int = 131072
input-file: string = "stdin"
output-file: string = "stdout"
strict: bool = true

[consts] # Константы, используемые препроцессором, дополнительно хранятся в files/consts.hpp
# Пример
maxN: int = 50000
maxM: int = 100000

[problem]
has-validator: bool = true
~~~~~
