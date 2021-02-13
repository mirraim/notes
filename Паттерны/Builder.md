####Строитель 
это порождающий шаблон проектирования, который позволяет создавать сложные объекты пошагово. 
Строитель позволяет использовать один и тот же код построения объекта для получения разных представлений объектов.

Например у нас есть сложный объект, который для создания требует сложной пошаговой инициализации множества полей и,
что еще хуже и сложнее, вложенных объектов. 
Чтобы проинициализировать такой объект необходимо использовать очень большой конструктор с множеством параметров, 
который при использовании клиентом становится абсолютно нечитаемым и,
 чтобы контролировать вводимые параметры в том месте где определено их место - 
 требуется постоянно возвращаться к объявленному конструктору. Это определенно неудобно и приводит 
 к проблемам у потребителя такого кода.
  
 А что если нам для потребления объекта не нужно инициализировать все поля? 
 Напрашивается очевидный ответ перегрузить конструктор, 
 но так мы можем расплодить бесчисленное количество конструкторов, 
 которые могут потребляться один раз, т.е. простаивать.
  
  Именно для таких случаев используется шаблон Строитель. 
  Он предлагает решение такой проблемы путем вынесения конструирования объекта 
  за пределы его собственного класса (или за счет вложенного статического класса), 
  поручив это дело отдельным объектам, которые и называются строителями.
  
  Шаблон предлагает разбить процесс конструирования объекта на отдельные шаги. 
  Чтобы создавать объекты таким образом, нам нужно поочередно вызывать методы строителя. 
  При этом нам не нужно запускать все шаги, а только те, которые нужны для производства объекта определенной конфигурации.
  
     public class Employee {
         private String name;
         private String department;
         private String position;
         private double salary;
         private int experience;
         private int age;
         private Map<String, Integer> children;
     
        static class Builder {
            private String name;
            private String department;
            private String position;
            private double salary;
            private int experience;
            private int age;
            private Map<String, Integer> children;
     
            Builder buildName(String name) {
                this.name = name;
                return this;
            }
     
            Builder buildDepartment(String department) {
                this.department = department;
                return this;
            }
     
            Builder buildPosition(String position) {
                this.position = position;
                return this;
            }
     
            Builder buildSalary(double salary) {
                this.salary = salary;
                return this;
            }
     
            Builder buildExperiance(int experience) {
                this.experience = experience;
                return this;
            }
     
            Builder buildAge(int age) {
                this.age = age;
                return this;
            }
     
            Builder buildChildren(Map<String, Integer> children) {
                this.children = children;
                return this;
            }
     
            Employee build() {
                Employee employee = new Employee();
                employee.name = name;
                employee.department = department;
                employee.position = position;
                employee.salary = salary;
                employee.experience = experience;
                employee.age = age;
                employee.children = children;
                return employee;
            }
        }
     }
   
   Метод build() мы уже будем вызывать для того, чтобы вернуть готовый объект. 
   Его поведение схоже с терминальными операциями в Stream API, которые возвращают результат из потока, 
   а не поток, как это делают конвейерные методы. 
   
       Employee employee = new Builder().buildName("John")
                       .buildSalary(3000.00)
                       .buildPosition("Analyst")
                       .build();