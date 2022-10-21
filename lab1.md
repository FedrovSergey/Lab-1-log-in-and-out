Создание системы http аутентификации

Возможности и особенности системы: 
1)Регистрация пользователя
2)Получение доступа к главной странице зарегистрированным пользователем
3)Восстановление пароля пользователем
4)Смена пароля пользователем
5)Пароли хранятся с солью в хешированном виде
6)Сессия зарегистрированного пользователя ограничена по времени
7)Пароли подлежат валидации

Вид окон в системе:

![окно регистрации](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
![окно входа](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B2%D1%82%D0%BE%D1%80%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
![окно восстановления пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D1%82%D1%80%D0%B5%D1%82%D0%B8%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
![окно смены пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D1%87%D0%B5%D1%82%D0%B2%D0%B5%D1%80%D1%82%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)
![главная страница](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%BF%D1%8F%D1%82%D0%BE%D0%B5%20%D0%BE%D0%BA%D0%BD%D0%BE.png)

Примеры запросов на сервер и ответы на них:
![успешный вход](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(1).png)
![успешный выход](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(2).png)
![безуспешная попытка перехода к профилю](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(3).png)
![смена пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(4).png)
![восстановление пароля](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(5).png)
![безуспешная регистрация](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled%20(6).png)
![успешная регистрация](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D1%8B/Untitled.png)

Работа сайта на примере блок схемы:
![блок схема сайта](https://github.com/FedrovSergey/Lab-1-log-in-and-out/blob/main/lab1/pictures/%D0%B1%D0%BB%D0%BE%D0%BA%20%D1%81%D1%85%D0%B5%D0%BC%D0%B0%20%D0%BB%D1%80-1%20%D0%BE%D0%BF.png)

База данных, использующаяся сайтом - это mySQL. Состоит таблица базы данных из 3 столбцов:
1)id  2)login  3)password.

