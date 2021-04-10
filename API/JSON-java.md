####JSON-Java (org.json) 
легковесная функциональная библиотека для работы с JSON, 
которая дополнительно умеет преобразовывать JSON в XML, 
HTTP header, Cookies и др. В отличие от Jackson или Gson, 
JSON-Java преобразует json-строку не в объект пользовательского класса 
(способ Data bind), а в объекты своей библиотеки JSONObject,
JSONArray (способ Tree Model).

#####Зависимость

    <dependency>
        <groupId>org.json</groupId>
        <artifactId>json</artifactId>
        <version>20200518</version>
    </dependency>

Для корректного преобразования в строку с помощью org.json 
в класс необходимо добавить геттеры.

####Синтаксис

    public static void main(String[] args) {

        /* JSONObject из json-строки строки */
        JSONObject jsonContact = new JSONObject("{\"phone\":\"+7(924)111-111-11-11\"}");

        /* JSONArray из ArrayList */
        List<String> list = new ArrayList<>();
        list.add("Student");
        list.add("Free");
        JSONArray jsonStatuses = new JSONArray(list);

        /* JSONObject напрямую методом put */
        final Person person = new Person(false, 30, new Contact("11-111"), "Worker", "Married");
        JSONObject jsonObject = new JSONObject();
        jsonObject.put("sex", person.isSex());
        jsonObject.put("age", person.getAge());
        jsonObject.put("contact", jsonContact);
        jsonObject.put("statuses", jsonStatuses);

        /* Выведем результат в консоль */
        System.out.println(jsonObject.toString());

        /* Преобразуем объект person в json-строку */
        System.out.println(new JSONObject(person).toString());
    }


Доп. ссылки, более детально о возможностях JSON-Java:

https://www.baeldung.com/java-org-json (Eng.)

https://github.com/stleary/JSON-java (Eng.)

https://habr.com/ru/company/luxoft/blog/280782/ (Rus.)

https://javadevblog.com/primer-raboty-s-json-org-v-java-razbor-i-sozdanie-json.html (Rus.)

