# JavaJDBCPostgres

приложение должно получать данные и заносить в созданную базу данных с помощью PostgreSQL

- **PostgreSQL** — свободная объектно-реляционная система управления базами данных (СУБД).

Существует в реализациях для множества UNIX-подобных платформ, включая AIX, различные BSD-системы, HP-UX, IRIX, Linux, macOS, Solaris/OpenSolaris, Tru64, QNX, а также для Microsoft Windows.


Поддержка стандартов, возможности, особенности


PostgreSQL базируется на языке SQL и поддерживает многие из возможностей стандарта SQL:2011.

В PostgreSQL версии 12 есть следующие ограничения:

- Максимальный размер базы данных - Нет ограничений

- Максимальный размер таблицы - 32 Тбайт

- Максимальный размер поля - 1 Гбайт

- Максимум записей в таблице - Ограничено размерами таблицы

- Максимум полей в записи - 250—1600, в зависимости от типов полей

- Максимум индексов в таблице - Нет ограничений

Сильные стороны PostgreSQL:

- высокопроизводительные и надёжные механизмы транзакций и репликации;

- расширяемая система встроенных языков программирования: в стандартной поставке поддерживаются PL/pgSQL, PL/Perl, PL/Python и PL/Tcl; дополнительно можно использовать PL/Java, PL/PHP, PL/Py, PL/R, PL/Ruby, PL/Scheme, PL/sh и PL/V8, а также имеется поддержка загрузки модулей расширения на языке C;

- наследование;

- возможность индексирования геометрических объектов и наличие базирующегося на ней расширения PostGIS;
встроенная поддержка слабоструктурированных данных в формате JSON с возможностью их индексации;
расширяемость (возможность создавать новые типы данных, типы индексов, языки программирования, модули расширения, подключать любые внешние источники данных).

# Основные возможности
**Функции**

*Функции являются блоками кода, исполняемыми на сервере, а не на клиенте БД. Хотя они могут писаться на чистом SQL, реализация дополнительной логики, например, условных переходов и циклов, выходит за рамки SQL и требует использования некоторых языковых расширений. Функции могут писаться с использованием одного из следующих языков:*

- *Встроенный процедурный язык PL/pgSQL, во многом аналогичный языку PL/SQL, используемому в СУБД Oracle;*
- *Скриптовые языки — PL/Lua, PL/LOLCODE, PL/Perl, PL/PHP, PL/Python, PL/Ruby, PL/sh, PL/Tcl, PL/Scheme, PL/v8 (Javascript);*
- *Классические языки — C, C++, Java (через модуль PL/Java);*
- *Статистический язык R (через модуль PL/R).*

PostgreSQL допускает использование функций, возвращающих набор записей, который далее можно использовать так же, как и результат выполнения обычного запроса.

Функции могут выполняться как с правами их создателя, так и с правами текущего пользователя.

Иногда функции отождествляются с хранимыми процедурами, однако между этими понятиями есть различие. С девятой версии возможно написание автономных блоков, которые позволяют выполнять код на процедурных языках без написания функций, непосредственно в клиенте.

**Триггеры**

Триггеры определяются как функции, инициируемые DML-операциями. Например, операция INSERT может запускать триггер, проверяющий добавленную запись на соответствия определённым условиям. При написании функций для триггеров могут использоваться различные языки программирования (см. выше).

Триггеры ассоциируются с таблицами. Множественные триггеры выполняются в алфавитном порядке.

**Правила и представления**

Механизм правил (англ. *rules*) представляет собой механизм создания пользовательских обработчиков не только DML-операций, но и операции выборки. *Основное отличие от механизма триггеров* заключается в том, что правила срабатывают на этапе разбора запроса, до выбора оптимального плана выполнения и самого процесса выполнения. Правила позволяют переопределять поведение системы при выполнении SQL-операции к таблице. Хорошим примером является реализация механизма представлений (англ. views): при создании представления создается правило, которое определяет, что вместо выполнения операции выборки к представлению система должна выполнять операцию выборки к базовой таблице/таблицам с учётом условий выборки, лежащих в основе определения представления. Для создания представлений, поддерживающих операции обновления, правила для операций вставки, изменения и удаления строк должны быть определены пользователем.

**Индексы**

В PostgreSQL имеется поддержка индексов следующих типов: B-tree , hash , GiST , GIN , BRIN , Bloom. При необходимости можно создавать новые типы индексов. Индексы в PostgreSQL обладают следующими свойствами:

- возможен просмотр индекса не только в прямом, но и в обратном порядке — создание отдельного индекса для работы конструкции ORDER BY ... DESC не нужно;
-  возможно создание индекса над несколькими столбцами таблицы, в том числе над столбцами различных типов данных;
- индексы могут быть функциональными, то есть строиться не на базе набора значений некоего столбца/столбцов, а на базе набора значений функции от набора значений;
- индексы могут быть частичными, то есть строиться только по части таблицы (по некоторой её проекции); в некоторых случаях это помогает создавать намного более компактные индексы или достигать улучшения производительности за счёт использования разных типов индексов для разных (например, с точки зрения частоты обновления) частей таблицы;
- планировщик запросов может использовать несколько индексов одновременно для выполнения сложных запросов.

**Многоверсионность (MVCC)**

PostgreSQL поддерживает одновременную модификацию БД несколькими пользователями с помощью механизма Multiversion Concurrency Control (MVCC). Благодаря этому соблюдаются требования ACID и практически отпадает нужда в блокировках чтения.

**Типы данных**
PostgreSQL поддерживает большой набор встроенных типов данных:
- Численные типы
- Целые
- С фиксированной точкой
 - С плавающей точкой
 - Денежный тип (отличается специальным форматом вывода, а в остальном аналогичен числам с фиксированной точкой с двумя знаками после запятой)
 - Символьные типы произвольной длины
 - Двоичные типы (включая BLOB)
 - Типы «дата/время» (полностью поддерживающие различные форматы, точность, форматы вывода, включая последние изменения в часовых поясах)
 - Булев тип
 - Перечисление
 - Геометрические примитивы
 - Сетевые типы
         - IP и IPv6-адреса
         - CIDR-формат
         - MAC-адрес
 - UUID-идентификатор
 - XML-данные
 - Массивы
 - JSON
 - Идентификаторы объектов БД
 - Псевдотипы
Более того, пользователь может самостоятельно создавать новые требуемые ему типы и программировать для них механизмы индексирования с помощью GiST.

**Пользовательские объекты**

PostgreSQL может быть расширен пользователем для собственных нужд практически в любом аспекте. Есть возможность добавлять собственные:

- Преобразования типов
- Типы данных
- Домены (пользовательские типы с изначально наложенными ограничениями)
- Функции (включая агрегатные)
- Индексы
- Операторы (включая переопределение уже существующих)
- Процедурные языки

**Наследование и партицирование**

Таблицы могут наследовать характеристики и наборы полей от других таблиц (родительских). При этом данные, добавленные в порождённую таблицу, автоматически будут участвовать (если это не указано отдельно) в запросах к родительской таблице.

В PostgreSQL 10 был добавлен механизм партицирования таблиц. ***Партицирование*** предназначено для разделения одной таблицы на несколько, так называемые партиции. ***Партицирование*** схоже с наследованием, но имеет более дружелюбный к пользователю синтаксис и более строгие ограничения, что позволяет выполнять дополнительные оптимизации при планировании запросов.

**Прочие возможности**

- Соблюдение принципов ACID
- Соответствие стандартам ANSI SQL-92, SQL-99, SQL:2003, SQL:2011
- Поддержка запросов с OUTER JOIN, UNION, UNION ALL, EXCEPT, INTERSECT и подзапросов
- Последовательности
- Контроль целостности
- Репликация
- Общие табличные выражения и рекурсивные запросы
- Аналитические функции
- Поддержка Юникода (UTF-8)
- Поддержка регулярных выражений в стиле Perl
- Встроенная поддержка SSL, SELinux и Kerberos
- Протокол разделяемых блокировок
- Подгружаемые расширения, поддерживающие SHA1, MD5, XML
- Расширения для написания сложных выборок, отчётов и т. д. (API открыт)
- Средства для генерации совместимого с другими системами SQL-кода и импорта из других систем
- Автономные блоки на доступных языках, а не только SQL
