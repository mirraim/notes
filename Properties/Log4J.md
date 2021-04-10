**Вывод информации в консоль:**

    log4j.appender.console=org.apache.log4j.ConsoleAppender

**Формат записи:**

    log4j.appender.console.layout=org.apache.log4j.PatternLayout
    log4j.appender.console.layout.ConversionPattern=%d{ISO8601} %5p %c:%M:%L - %m%n

1. Дата - %d{ISO8601}
2. Уровень сообщения - %5p
3. Класс, метод, строчка - %c:%M:%L
4. Текст сообщения - %m%n

**Уровень логгирования:**

    log4j.rootLogger=DEBUG, console
Чем критичнее сообщение, тем выше должен быть уровень сообщения.

1. ERROR - критические ошибки.
2. DEBUG - отладочная информация.