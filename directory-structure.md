# Структура папок

~~~~~
🗁 problem // Папка с задачей
├─🗁 files // Вспомогательные файлы 
│ ├─🗋 testlib.h
│ ├─🗋 contraints.hpp // Файл, где дополнительно хранятся ограничения
│ └─🗋 olymp.sty
├─🗁 generators
│ ├─🗋 gen1.cpp
│ ├─🗋 gen2.cpp
│ ├─ ...
│ ├─🗋 list // Список генераторов, описан в gen-config.md
│ └─🗋 Makefile // Генерируется системой
├─🗁 checkers
│ ├─🗋 check.cpp
│ ├─🗋 tests // Тесты чекера, формат описан в test-spec.md
│ └─🗋 Makefile // Генерируется системой
├─🗁 validators
│ ├─🗋 validator.cpp
│ ├─🗋 tests // Тесты валидатора, формат описан в test-spec.md
│ └─🗋 Makefile // Генерируется системой
├─🗁 testsets
│ ├─🗁 archive // Архивные тесты, разрешены как просто входные файлы, так и пары .in/.out
│ │ ├─🗋 1.in
│ │ ├─🗋 1.out
│ │ ├─🗋 test1.in
│ │ ├─🗋 2.in
│ │ ├─🗋 q.in
│ │ ├─🗋 q.out
│ │ └─ ...
│ ├─🗁 ts-tests // Тестсет, названия начинаются с префикса ts-
│ │ ├─🗋 1.in
│ │ ├─🗋 1.out
│ │ ├─🗋 2.in
│ │ ├─🗋 2.out
│ │ ├─ ...
│ │ ├─🗋 script.py // Скрипт генерации тестов
│ │ └─🗋 Makefile // Генерируется системой
│ ├─🗁 ts-pretests
│ │ ├─🗋 1.in
│ │ ├─🗋 1.out
│ │ ├─🗋 2.in
│ │ ├─🗋 2.out
│ │ ├─ ...
│ │ ├─🗋 script.py // Скрипт генерации тестов
│ │ └─🗋 Makefile // Генерируется системой
│ ├─ ...
│ ├─🗋 manual // Ручные тесты, формат описан в test-spec.md
│ ├─🗋 list // Список тестсетов, формат описан в testset-config.md
│ └─🗋 Makefile // Генерируется системой
├─🗁 solutions
│ ├─🗋 a.cpp
│ ├─🗋 b.pas
│ ├─🗋 c.java
│ ├─ ...
│ ├─🗋 list // Список решений, описан в solution-config.md
│ └─🗋 Makefile // Генерируется системой
├─🗁 statements
│ ├─🗁 en
│ │ ├─🗋 legend.tex
│ │ ├─🗋 input.tex
│ │ ├─🗋 output.tex
│ │ ├─🗋 notes.tex
│ │ ├─🗋 scoring.tex
│ │ └─🗋 Makefile // Генерируется системой
│ ├─🗁 ru
│ │ ├─🗋 legend.tex
│ │ ├─🗋 input.tex
│ │ ├─🗋 output.tex
│ │ ├─🗋 notes.tex
│ │ ├─🗋 scoring.tex
│ │ └─🗋 Makefile // Генерируется системой
│ └─🗋 Makefile // Генерируется системой
├─🗁 stresses
│ ├─🗋 my
│ ├─🗋 stress42
│ └─ ...
├─🗀 .taker // Папка для внутреннего использования в taker
├─🗋 Takefile // Основной файл конфигурации, описан в main-config.md
└─🗋 Makefile // Генерируется системой
~~~~~
