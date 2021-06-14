# Diplom
## Дипломный проект профессии «Тестировщик»
### Документация
* [План тестирования](https://github.com/BVBukaeva/Diplom/blob/main/documents/Plan.md "План тестирования")
* [Отчет по итогам тестирования](https://github.com/BVBukaeva/Diplom/blob/main/documents/Report.md "Отчет по итогам тестирования")
* [Комплексный отчет по итогам процесса автоматизации](https://github.com/BVBukaeva/Diplom/blob/main/documents/Summary.md "Комплексный отчет по итогам процесса автоматизации")
### О проекте
#### Проект представляет собой комплексное автоматизированное тестирование сервиса по покупке туров через интернет-банк. Купить тур можно с помощью двух способов:
* Покупка по дебетовой карте
* Покупка в кредит
#### Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:
* сервису платежей (Payment Gate)
* кредитному сервису (Credit Gate)
#### Приложение в собственной СУБД сохраняет информацию о том, каким способом был совершён платёж и успешно ли он был совершён.

### Запуск Авто-Тестов.
* Запустить в Docker контейнеры СУБД MySQl, PostgerSQL и Node.js
* Запустить контейнеры в терминале
1. Нужно ввести команду в терминале: 
**docker-compose up -d**
2. Зпускаем SUT, для этого в новой вкладке в терминале вводим следующую команду:
* Для СУБД MySQL: **java -jar ./artifacts/aqa-shop.jar**
* Для СУБД PostgreSQL: **java -jar ./artifacts/aqa-shop.jar --spring.datasource.url=jdbc:postgresql://localhost:5432/app**
3. Запускаем автотесты, следующе командой:
* Для MySQL:
**gradlew clean test**
* Для PostgreSQL: **gradlew clean test -Ddb.url=jdbc:postgresql://localhost:5432/app**
4. Сгенерировать отчеты: 
* **gradlew allureReport**
* **gradlew allureServ**
5. Для завершения работы allureServe выполнить команду: **Ctrl + С далее Y**
