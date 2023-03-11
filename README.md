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
Создаем переменные: req_name, req_age, req_salary
```
let req_name=req.name;
let req_age=req.age;
let req_salary=+req.salary;
```
8. Проверить, что name в ответе равно name из request (name забрать из request.)
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
Создаем переменные: req_name, req_age, req_salary
```
let req_name=requestData.name;
let req_age=requestData.age;
let req_salary=+requestData.salary;
```
5. Проверить, что name в ответе равно name из request (name забрать из request.)
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
8. Вывести в консоль параметр family из response.
```
console.log(responseData.family)
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("The Dog parameter has a Name parameter", function () {
       pm.expect(responseData.family.pets.dog).to.have.property("name")
});
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("The Dog parameter has an Age parameter", function () {
   pm.expect(responseData.family.pets.dog).to.have.property("age")
});
```
11. Проверить, что параметр name имеет значение Luky.
```
pm.test("The Dog name is Luky", function () {
      pm.expect(responseData.family.pets.dog.name).to.eql("Luky")
});
```
12. Проверить, что параметр age имеет значение 4.
```
pm.test("The Dog  is 4 years old", function () {
    var responseData = pm.response.json();
   pm.expect(responseData.family.pets.dog.age).to.eql(4)
});
```
### Тесты пройдены :ok_hand:

<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/HW_2_Task_3.png">
</p> </div>

#### Задача 4

1. Отправить http-запрос методом GET: **http:162.55.220.72:5005/object_info_4**
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
Создаем переменные: req_name, req_age, req_salary
```
let req_name=requestData.name;
let req_age=+requestData.age;
let req_salary=+requestData.salary;
```
5. Проверить, что name в ответе равно name из request (name забрать из request.)
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
7. Вывести в консоль параметр salary из request.
```
console.log("Salary from Request: "+ requestData.salary);
```
8. Вывести в консоль параметр salary из response.
```
console.log("Salary from Response: "+ responseData.salary);
```
9. Вывести в консоль 0-й элемент параметра salary из response.
```
console.log("Salary [0] from Response: "+ responseData.salary[0]);
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
console.log("Salary [1] from Response: "+ responseData.salary[1]);
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
console.log("Salary [2] from Response: "+ responseData.salary[2]);
```
<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/Console1_Task-4.png">
</p> </div>
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)

```
pm.test("Salary [0] from Response = Salary from Request", function () {
    pm.expect(responseData.salary[0]).to.eql(req_salary);
});
```

13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("Salary [1] from Response = Salary from Request*2", function () {
    pm.expect(+responseData.salary[1]).to.eql(req_salary*2);
});
```

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("Salary [1] from Response = Salary from Request*2", function () {
    pm.expect(+responseData.salary[1]).to.eql(req_salary*2);
});
```
15. Создать в окружении переменную name.
16. Создать в окружении переменную age.
17. Создать в окружении переменную salary.
<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/Env_Var.png">
</p> </div>
18. Передать в окружение переменную name.

```
pm.environment.set("name", req_name);
```
19. Передать в окружение переменную age.

```pm.environment.set("age", req_age);
```
20. Передать в окружение переменную salary.

```
pm.environment.set("salary", req_salary);
```
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.

```
console.log("Salary output with a loop")
for  (i=0; i<3;i++)
{console.log("Salary ["+i+"]:"+responseData.salary[i]);}
```

### Тесты пройдены :ok_hand:

<div id="screen" align="center" dir="auto">
<p dir="auto"> <img src="https://github.com/NatashaSmolyak/Postman/blob/main/assets/HW_2_Task_4.png">
</p> </div>