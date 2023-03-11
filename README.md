 ![image](https://github.com/NatashaSmolyak/Postman/blob/main/assets/Postman-header-image.png)


### Тестирование ПО: Postman для тестирования API. [Сертификат](https://stepik.org/cert/1936752)
------
### Курс по тестированию ПО Вадима Ксендзова.
***Страница находится в процессе разработки***.
### Задание 1. [Смотреть всю коллекцию](https://github.com/NatashaSmolyak/Postman/blob/main/Home_Work-1_Nata_Smolyak.postman_collection.json)
### Задание 2. [Смотреть всю коллекцию](https://github.com/NatashaSmolyak/Postman/blob/main/Home_Work-2_Nata_Smolyak.postman_collection.json)
Также на данной страничке можно посмотреть порядок выполнения Задания 2 

#### Задача 1
1. Отправить http-запрос методом GET: **http:162.55.220.72:5005/first**.
2. Проверить, что возращается 200 статус код.

Тест:
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.

Тест: 
```
pm.test("Body is correct", function () {
    pm.response.to.have.body("This is the first responce from server!ss");
});
```
<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/HW_2_1.png">
</p> </div>

#### Задача 2

1. Отправить http-запрос методом POST: **http:162.55.220.72:5005/user_info_3**
2. Проверить, что возращается 200 статус код.

Тест:
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```


