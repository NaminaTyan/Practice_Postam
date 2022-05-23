# Practice_Postam

HW_2 Postman

http://162.55.220.72:5005/first
---

--- Создать коллекцию HW_2
--- Создать запрос с методом Get
--- Вставить в строку url http://162.55.220.72:5005/first

1. Отправить запрос.
--- Save
--- Sand

2. Статус код 200
--- Переключиться на Tests
--- Выбрать в сниппетах Status code: Code is 200
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
--- Save
--- Sand
--- Проверить в Test Results результат PASS

3. Проверить, что в body приходит правильный string.
--- Выбрать в сниппетах Responce body: Contains string

pm.test("Body matches string", function () {

    pm.expect(pm.response.text()).to.include("This is the first responce from server!");
    
});

--- Save
--- Sand
--- Проверить в Test Results результат PASS

http://162.55.220.72:5005/user_info_3
---
1. Отправить запрос.
--- Создать запрос с методом POST
--- Вставить в строку url http://162.55.220.72:5005/first
--- добавить в body - form-data: name, age, salary
--- Save
--- Sand

2. Статус код 200
--- Выбрать в сниппетах Responce body: Contains string

pm.test("Body matches string", function () {

    pm.expect(pm.response.text()).to.include("This is the first responce from server!");
    
});

--- Save
--- Sand
--- Проверить в Test Results результат PASS

3. Спарсить response body в json.

let jsonData = pm.response.json()

4. Проверить, что name в ответе равно name s request (name вбить руками.)

pm.test("user_name", function () {

    pm.expect(jsonData.name).to.eql("Diana");
    
});

5. Проверить, что age в ответе равно age s request (age вбить руками.)

pm.test("user_age", function () {

    pm.expect(jsonData.age).to.eql("29");
    
});

6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)

pm.test("user_salary", function () {
    
    pm.expect(jsonData.salary).to.eql(1000);

});

7. Спарсить request.
 
let req = request.data

8. Проверить, что name в ответе равно name s request (name забрать из request.)
 
pm.test("req_name", function () {

    pm.expect(req.name).to.deep.eql(jsonData.name);
    
});

9. Проверить, что age в ответе равно age s request (age забрать из request.)

pm.test("req_age", function () {

    pm.expect(req.age).to.deep.eql(jsonData.age);
    
});

10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

pm.test("req_salary", function () {

    pm.expect(+req.salary).to.deep.eql(jsonData.salary);
    
});

11. Вывести в консоль параметр family из response.

console.log(jsonData.family)

12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)

pm.test("u_salary_1_5_year", function () {

    pm.expect((+req.salary) * 4).to.deep.eql(jsonData.family.u_salary_1_5_year);
    
});

http://162.55.220.72:5005/object_info_3
---
1. Отправить запрос.
--- Создать запрос с методом GET
--- Вставить в строку url http://162.55.220.72:5005/object_info_3
--- добавить в body - form-data: name, age, salary
--- Save
--- Sand

2. Статус код 200

pm.test("Status code is 200", function () {

    pm.response.to.have.status(200);
    
});

3. Спарсить response body в json.

let jsonData = pm.response.json();

4. Спарсить request.

let req = pm.request.url.query.toObject()

5. Проверить, что name в ответе равно name s request (name забрать из request.)

pm.test("req_name", function () {

    pm.expect(jsonData.name).to.eql(req.name);
    
});

6. Проверить, что age в ответе равно age s request (age забрать из request.)

pm.test("req_age", function () {

    pm.expect(jsonData.age).to.deep.eql(req.age);
    
});

7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

pm.test("req_salary", function () {

    pm.expect(jsonData.salary).to.deep.eql(+req.salary);
    
});

8. Вывести в консоль параметр family из response.

console.log (jsonData.family)

9. Проверить, что у параметра dog есть параметры name.

pm.test("dog_name", function () {

    pm.expect(jsonData.family.pets.dog).to.have.property('name');
    
});

10. Проверить, что у параметра dog есть параметры age.

pm.test("dog_age", function () {

    pm.expect(jsonData.family.pets.dog).to.have.property('age');
    
});

11. Проверить, что параметр name имеет значение Luky.

pm.test("name_Luky", function () {

    pm.expect(jsonData.family.pets.dog.name).to.include('Luky');
    
});

12. Проверить, что параметр age имеет значение 4.

pm.test("age_4", function () {

    pm.expect(jsonData.family.pets.dog.age).to.include+('4');
    
});

http://162.55.220.72:5005/object_info_4
---
1. Отправить запрос.
--- Создать запрос с методом GET
--- http://162.55.220.72:5005/object_info_4
--- добавить в body - form-data: name, age, salary
--- Save
--- Sand

2. Статус код 200

pm.test("Status code is 200", function () {

    pm.response.to.have.status(200);
    
});

3. Спарсить response body в json.

let jsonData = pm.response.json();

4. Спарсить request.

let req = pm.request.url.query.toObject()

5. Проверить, что name в ответе равно name s request (name забрать из request.)

pm.test("req_name", function () {

    pm.expect(jsonData.name).to.deep.eql(req.name);
    
});

6. Проверить, что age в ответе равно age из request (age забрать из request.)

pm.test("req_age", function () {

    pm.expect(jsonData.age).to.deep.eql+(req.age);
    
});

7. Вывести в консоль параметр salary из request.

console.log(req.salary)

8. Вывести в консоль параметр salary из response.

console.log(jsonData.salary)

9. Вывести в консоль 0-й элемент параметра salary из response.

console.log(jsonData.salary[0])

10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.

console.log(jsonData.salary[1])

11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.

console.log(jsonData.salary[2])

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)

pm.test("req_salary[0]", function () {

    pm.expect(jsonData.salary[0]).to.deep.eql+(req.salary);
    
});

13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)

pm.test("req_salary[1]", function () {

    pm.expect(jsonData.salary[1]).to.deep.eql+(req.salary * 2);
    
});

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)

pm.test("req_salary[2]", function () {

    pm.expect(jsonData.salary[2]).to.deep.eql+(req.salary * 3);
    
});

15. Создать в окружении переменную name
--- Создаем новое окружение: выбираем Environments - Create new Environment - возвращаемся на вкладку запроса, выбираем созданное окружение

pm.environment.set('name', ' ')

16. Создать в окружении переменную age

pm.environment.set('age', ' ')

17. Создать в окружении переменную salary

pm.environment.set('salary', ' ')

18. Передать в окружение переменную name

pm.environment.set('name', 'Maximus')

19. Передать в окружение переменную age

pm.environment.set('age', '32')

20. Передать в окружение переменную salary

pm.environment.set('salary', '5000')

21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.

for (let el in jsonData.salary) {

    console.log(jsonData.salary[el]);
    
}

http://162.55.220.72:5005/user_info_2
---
1. Вставить параметр salary из окружения в request
--- Выбираем вкладку Bode - form data - в Key вставляем salary - в Value вставляем {{salary}}

2. Вставить параметр age из окружения в age
--- в Key вставляем age - в Value вставляем {{age}}

3. Вставить параметр name из окружения в name
--- в Key вставляем name - в Value вставляем {{name}}

4. Отправить запрос.
--- Save
--- Send

5. Статус код 200

pm.test("Status code is 200", function () {

    pm.response.to.have.status(200);
    
});

6. Спарсить response body в json.

let jsonData = pm.response.json()

7. Спарсить request.

let req = pm.request.url.query.toObject()

8. Проверить, что json response имеет параметр start_qa_salary

pm.test("start_qa_salary", function () {

    pm.expect(jsonData).to.have.property('start_qa_salary');
    
});

9. Проверить, что json response имеет параметр qa_salary_after_6_months

pm.test("qa_salary_after_6_months", function () {

    pm.expect(jsonData).to.have.property('qa_salary_after_6_months');
    
});

10. Проверить, что json response имеет параметр qa_salary_after_12_months

pm.test("qa_salary_after_12_months", function () {

    pm.expect(jsonData).to.have.property('qa_salary_after_12_months');
    
});

11. Проверить, что json response имеет параметр qa_salary_after_1.5_year

pm.test("qa_salary_after_1.5_year", function () {

    pm.expect(jsonData).to.have.property('qa_salary_after_1.5_year');
    
});

12. Проверить, что json response имеет параметр qa_salary_after_3.5_years

pm.test("qa_salary_after_3.5_years", function () {

    pm.expect(jsonData).to.have.property('qa_salary_after_3.5_years');
    
});

13. Проверить, что json response имеет параметр person

pm.test("person", function () {

    pm.expect(jsonData).to.have.property('person');
    
});

14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)

pm.test("start_qa_salary == salary", function () {

    pm.expect(jsonData.start_qa_salary).to.eql(+req.salary);
    
});

15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)

pm.test("qa_salary_after_6_months == salary * 2", function () {

    pm.expect(jsonData.qa_salary_after_6_months).to.eql(req.salary * 2);
    
});

16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)

pm.test("qa_salary_after_12_months == salary * 2.7", function () {

    pm.expect(jsonData.qa_salary_after_12_months).to.eql(req.salary * 2.7);
    
});

17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)

pm.test("qa_salary_after_1.5_year == salary * 3.3", function () {

    pm.expect(jsonData["qa_salary_after_1.5_year"]).to.eql(req.salary * 3.3);
    
});

18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)

pm.test("qa_salary_after_3.5_years == salary * 3.8", function () {

    pm.expect(jsonData["qa_salary_after_3.5_years"]).to.eql(req.salary * 3.8);
    
});

19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)

pm.test("u_name[1] == salary", function () {

    pm.expect(jsonData.person.u_name[1]).to.eql(+req.salary);
    
});

20. Проверить, что что параметр u_age равен age из request (age забрать из request.)

pm.test("u_age == age", function () {

    pm.expect(jsonData.person.u_age).to.eql(+req.age);
    
});

21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)

pm.test("u_salary_5_years == salary * 4.2", function () {

    pm.expect(jsonData.person["u_salary_5_years"]).to.eql(req.salary * 4.2);
    
});

22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.

console.log(Object.values(jsonData.person))
