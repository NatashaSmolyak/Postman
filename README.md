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
### Тесты пройдены :ok_hand:
<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/HW_2_Task_1.png">
</p> </div>

#### Задача 2

1. Отправить http-запрос методом POST: **http:162.55.220.72:5005/user_info_3**

Body запроса:
<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/Body_form_data.png">
</p> </div>
2. Проверить, что возращается 200 статус код.

```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let MyData = pm.response.json();
```
4. Проверить, что name в ответе равно name из request (name вбить руками.)
```
pm.test("Name from Response = Name from Request", function () {
        pm.expect(MyData.name).to.eql("Natasha");
});
```
5. Проверить, что age в ответе равно age из request (age вбить руками.)
```
pm.test("Age from Response = Age from Request", function () {
       pm.expect(MyData.age).to.eql("50");
});
```
6. Проверить, что salary в ответе равно salary из request (salary вбить руками.)
```
pm.test("Salary from Response = Salary from Request", function () {
        pm.expect(MyData.salary).to.eql(5000);
});
```
7. Спарсить request.
```
let req=request.data
```
8. Проверить, что name в ответе равно name из request (name забрать из request.)
Создаем переменные: req_name, req_age, req_salary
```
let req_name=req.name;
let req_age=req.age;
let req_salary=+req.salary;
```
```
pm.test("Name from Response = Name from Request", function () {
       pm.expect(MyData.name).to.eql(req_name);
});
```
9. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("Age from Response = Age from Request", function () {
        pm.expect(MyData.age).to.eql(req_age);
});
```
10. Проверить, что salary в ответе равно salary из request (salary забрать из request.)
```
pm.test("Salary from Response = Salary from Request", function () {
       pm.expect(MyData.salary).to.eql(req_salary);
});
```
11. Вывести в консоль параметр family из response.
```
console.log(MyData.family);
console.log("Children= "+ MyData.family.children)
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
let resp_salary_1_5_year=req_salary*4
pm.test("Salary 1_5 year from Response = Salary * 4 from Request", function () {
        pm.expect(MyData.family.u_salary_1_5_year).to.eql(resp_salary_1_5_year);
});
```

### Тесты пройдены :ok_hand:

<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/HW_2_Task_2.png">
</p> </div>


#### Задача 3

1. Отправить http-запрос методом GET: **http:162.55.220.72:5005/object_info_3**
2. Проверить, что возращается 200 статус код.
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let responseData = pm.response.json();
```
4. Спарсить request.
```
let requestData = pm.request.url.query.toObject()
```
5. Проверить, что name в ответе равно name из request (name забрать из request.)
Создаем переменные: req_name, req_age, req_salary
```
let req_name=requestData.name;
let req_age=requestData.age;
let req_salary=+requestData.salary;
```

```
pm.test("Name from Response = Name from Request", function () {
        pm.expect(responseData.name).to.eql(req_name);
});
```

6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("Age from Response = Age from Request", function () {
        pm.expect(responseData.age).to.eql(req_age);
});
```

7. Проверить, что salary в ответе равно salary из request (salary забрать из request.)
```
pm.test("Salary from Response = Salary from Request", function () {
        pm.expect(responseData.salary).to.eql(req_salary);
});
```