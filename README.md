# Postman ![Postman](https://img.shields.io/badge/-Postman-103606?style=for-the-badge&logo=Postman)

####Тестирование ПО: Postman для тестирования API. [Сертификат](https://stepik.org/cert/1936752)
------
#### Курс по тестированию ПО Вадима Ксендзова.
#### Задание 1. [Смотреть всю коллекцию](https://github.com/NatashaSmolyak/Postman/blob/main/Home_Work-1_Nata_Smolyak.postman_collection.json)
#### Задание 2. [Смотреть всю коллекцию](https://github.com/NatashaSmolyak/Postman/blob/main/Home_Work-2_Nata_Smolyak.postman_collection.json)
Также на данной страничке можно посмотреть порядок выполнения Задания 2.
Как парсить request в разных запросах:
1. POST с использованием **Raw**:
`let post_raw = JSON.parse(request.data);`

2. POST с использованием **Form-data**:
`let post_form_data = request.data;`

3. GET с использованием **Params**:
`let get_params = pm.request.url.query.toObject()`


#####Задача 1
1. Отправить http-запрос методом GET: **http:162.55.220.72:5005/first**.
2. Проверить, что возращается 200 статус код.
Тест:
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```
pm.test("Body is correct", function () {
    pm.response.to.have.body("This is the first responce from server!ss");
});
```



