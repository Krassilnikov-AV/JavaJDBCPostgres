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
