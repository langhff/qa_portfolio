### ***В этой папке представлены результаты выполнения задания из модуля "Тестирование API"***

Для тестирования давался специальный поддомен http://api-qa.skillbox.ru/practice3/
Он состоит из формы регистрации и авторизации, формы создания клиента. Форма просмотра клиентов находится в разработке.

### ***Задание:***
С помощью Postman протестируйте следующий функционал в новом приложении: 
Создание клиента.
Редактирование клиента.
Удаление клиента.
Оформите найденные баги в виде баг-репорта.

Документация к сервису представлена в файле [Документация к сервису.pdf](/skillbox%20тестирование%20API/Документация%20к%20сервису.pdf) (docs.googl https://docs.google.com/document/d/1nvLIq2fcYiDOXtpWp1wm7LGCUFz__VKzlWtP7d_iikg/edit)

Баг-репорты представлены в файле [Баг-репорты.xlsx](/skillbox%20тестирование%20API/Документация%20к%20сервису.pdf) (docs.googl https://docs.google.com/spreadsheets/d/13lUuUgi4e5qAUU5e1tNes-_TspnSYFDTL5fDyurjlEc/edit?usp=sharing)

_[Отчёт о проведённой автоматизации](/documents/Summary.md)_

_[баги](https://github.com/shpilkaQA/diplom-portfolio/issues)_

## Инструкция по запуску:

### ***для Windows***
**(*для остальных ОС использовать localhost вместо ip*)**

1. Клонировать текущий репозиторий
1. Перейти в директорию с клонированным репозиторием
1. Из папки с репозиторием запустить контейнеры
    ```
    docker-compose up -d
    ```
3. Запустить SUT
    * ***Для работы с MySQL***
   
    ```
    java -Dspring.datasource.url=jdbc:mysql://192.168.99.100:3306/app -jar artifacts/aqa-shop.jar
    ```
    
    * ***Для работы с Postgres***
   
    ```
    java -Dspring.datasource.url=jdbc:postgresql://192.168.99.100:5432/app -jar artifacts/aqa-shop.jar
   ```  
    дополнительно можно передать логин и пароль, установленные по умолчанию, добавив
    ```
    -Duser=app –Dpassword=pass
    ```

1. Запустить тесты
    * ***Для работы с MySQL***
       
    ```
    gradlew test
    ```
    Запуск в mysql установлен по умолчанию

    параметры:
    ```
    db.url=jdbc:mysql://192.168.99.100:3306/app
    user=app
    password=pass
    ```
        
    * ***Для работы с Postgres***
    
    ```
    gradlew test -Ddb.url=jdbc:postgresql://192.168.99.100:5432/app
    ```
    
1. Для формирования отчета Allure и его открытия в браузере выполнить команды
    ```
    gradlew allureReport
    gradlew allureServe
    ```

1. Остановить и удалить контейнеры    
    ```
    docker-compose down
    ```