# Глобальный файл конфигурации

Глобальный файл конфигурации оформлен в соответствии с [configs.md](configs.md), расположен в `~/.taker/options` и выглядит следующим образом:

~~~~~
[time-limits] # Ограничения по времени
default-tl: int = 2000 # По умолчанию для задачи (в миллисекундах)
checker-tl: int = 30000 # Для чекера (в миллисекундах)
validator-tl: int = 30000 # Для валидатора (в миллисекундах)
generator-tl: int = 30000 # Для генератора (в миллисекундах)
compiler-tl: int = 30000 # Для компилятора (в миллисекундах)

[memory-limits]
default-ml: int = 262144 # По умолчанию для задачи (в килобайтах)
checker-ml: int = 524288 # Для чекера (в килобайтах)
validator-ml: int = 524288 # Для валидатора (в килобайтах)
generator-ml: int = 524288 # Для генератора (в килобайтах)
compiler-ml: int = 524288 # Для компилятора (в килобайтах)

[tests]
max-test-count: int = 4096 # Максимальное количество тестов
~~~~~
