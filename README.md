# Practice_Postam

HW_2 Postman

http://162.55.220.72:5005/first
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
--- let jsonData = pm.response.json()

4. Проверить, что name в ответе равно name s request (name вбить руками.)
--- pm.test("user_name", function () {
    pm.expect(jsonData.name).to.eql("Diana");
});

5. Проверить, что age в ответе равно age s request (age вбить руками.)
--- pm.test("user_age", function () {
    pm.expect(jsonData.age).to.eql("29");
});

6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
--- pm.test("user_salary", function () {
    pm.expect(jsonData.salary).to.eql(1000);
});

7. Спарсить request.
--- let req = request.data

8. Проверить, что name в ответе равно name s request (name забрать из request.)
--- pm.test("req_name", function () {
    pm.expect(req.name).to.deep.eql(jsonData.name);
});

9. Проверить, что age в ответе равно age s request (age забрать из request.)
--- pm.test("req_age", function () {
    pm.expect(req.age).to.deep.eql(jsonData.age);
});

10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
--- m.test("req_salary", function () {
    pm.expect(+req.salary).to.deep.eql(jsonData.salary);
});

11. Вывести в консоль параметр family из response.
--- console.log(jsonData.family)

12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
--- m.test("u_salary_1_5_year", function () {
    pm.expect((+req.salary) * 4).to.deep.eql(jsonData.family.u_salary_1_5_year);
});