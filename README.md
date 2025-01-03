# Лабораторная работа: Шифрование файлов и каталогов

В этой лабораторной работе вам предстоит освоить базовые навыки работы с инструментом GnuPG для шифрования и дешифровки файлов и каталогов в операционной системе Linux.

Утилита GnuPG уже должна быть установлена предварительно на вашу систему Linux

Перед тем ĸаĸ выполнять задание, необходимо сгенерировать ключ:
1. Откройте терминал и выполните команду для генерации ключа:

    ```
    gpg --full-generate-key
    ```

2. Следуйте инструкциям на экране, выбрав тип ключа (по умолчанию RSA), длину ключа (2048 бит), срок действия ключа (0 = бессрочный) и введя ваше имя, email и комментарий.
3. Введите пароль для защиты закрытого ключа.


## Задание лаборатной работы

### 1. Шифрование файла:

1. Создайте тестовый файл с секретной информацией:

    ```
    echo "Если вы это читаете, то вы успешно расшифровали этот файл!" > secret_message.txt
    ```

2. Зашифруйте этот файл, используя ваш открытый ключ:

    ```
    gpg -e -r 'ваш_имя@пример.com' secret_message.txt
    ```

3. Убедитесь, что был создан зашифрованный файл с расширением .gpg


### 2. Дешифровка файла:

1. Расшифруйте зашифрованный файл:

    ```
    gpg -d secret_message.txt.gpg > decrypted_message.txt
    ```

2. Проверьте содержимое расшифрованного файла:

    ```
    cat decrypted_message.txt
    ```

### 3. Шифрование каталога:

1. Создайте каталог с несколькими файлами:

    ```
    mkdir encrypted_directory
    touch encrypted_directory/file1.txt encrypted_directory/file2.txt
    ```
2. Заполните эти файлы какой-либо информацией

3. Заархивируйте и зашифруйте этот каталог:

    ```
    tar czf - encrypted_directory | gpg -e -r 'ваш_имя@пример.com' > encrypted_directory.tar.gz.gpg
    ```

4. Удалите исходный каталог:

    ```
    rm -rf encrypted_directory
    ```

### 4. Дешифровка каталога:

1. Распакуйте и расшифруйте архивированный каталог:
    
    ```
    gpg -d encrypted_directory.tar.gz.gpg | tar xzf -
    ```

2. Убедитесь, что каталог восстановлен вместе со всеми файлами



## Как успешно сдать работу?

Создать свой репозиторий из шаблона этого. Как это делается - "Use this template" -> "Create a new repository" и сделайте его public.

Находясь уже в своем репозитории - создайте новый файл формата .md и там оформляйте отчет. В отчете опишите все шаги которые вы делали, чтобы получить финальный результат работы.

Что вам нужно знать, чтобы успешно защитить работу:

Знание основ шифрования:

* Понимание различий между симметричным и асимметричным шифрованием.
* Основы работы с открытыми и закрытыми ключами.

Понимание принципов работы GnuPG:

* Что такое GnuPG и для чего он предназначен
* Процесс генерации ключей (открытого и закрытого)
* Принципы шифрования и дешифрации файлов и каталогов

## Дополнительные источники

1. [Источник где можно найти все](https://google.com)
2. [stackoverflow](https://stackoverflow.com)
3. [Полезная статься на Habr](https://habr.com/ru/articles/358182/)
4. [Статья про шифрование на Wikipedia](https://ru.wikipedia.org/wiki/%D0%A8%D0%B8%D1%84%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)