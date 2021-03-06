# Лаба 5

#### Все та же 4 лабораторная, но теперь с асинхронными методами.

## Изменения
 - Рефакторинг кода для добавления асинхронного поведения. Рефакторинг касается всех элементов.
 - Переведены все операции ввода-вывода (IO operations) в асинхронный вариант.
 - Использован паттерн TAP (Task-based asynchronous pattern).
 
 ### Немного об асинхронности
  
  1) Асинхронность позволяет вынести отдельные задачи из основного потока в специальные асинхронные методы.
  При запросах к базе данных асинхронный метод уснет на время, пока не получит данные от БД, а основной поток сможет продолжить свою работу. 
  В синхронном же приложении, если бы код получения данных находился в основном потоке, этот поток просто бы блокировался на время получения данных.
  
  ### Что за TAP?
  2) TAP состоит из типов: System.Threading.Tasks.Task и System.Threading.Tasks.Task<TResult> в пространсте имен System.Threading.Tasks,
   которые используются для представления произвольных асинхронных операций.

### Архитектура (Дублирую для наглядности)
- Data Access (уровень доступа к данным): класс для работы с разными технологиями доступа к данным
- Models хранит сущности бд
- ServiceLayer слой сервисов для работы с DAL
- DataManager осуществляет работу с данными и пересылку файла на FTP сервер:
  1) Извлекает данные из базы данных MS SQL Server.
  2. Генерирует на основе имеющихся данных XML файл/файлы необходимой структуры.
  3. Отправляет его на FTP сервер.

### Ресурсы
1) Инфа о TAP: https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap?redirectedfrom=MSDN
2) Асинхронка: https://metanit.com/sharp/tutorial/13.3.php
