
Programación Orientada a Objetos usando Typescript

![1_n64atUMpf_v28pT7DwaVPg](https://user-images.githubusercontent.com/108378310/189501090-a0863e20-ef81-4f0c-9e32-fb37846b8c6d.jpg)


La codificación con objetos y clases facilita la vida de un desarrollador. La programación orientada a objetos es una metodología para simplificar el desarrollo de software, aplicaciones, paquetes, etc. Los principales pilares de la programación orientada a objetos son:

# Glosario

## 1. Abstraction
La abstracción es simplemente ocultar detalles internos y mostrar funcionalidades. Nos permite centrarnos en lo que hace un objeto en lugar de cómo lo hace.

La abstracción se puede lograr de dos maneras:

Usando clase abstracta
Usando la interfaz
Clase abstracta
Definimos una clase abstracta en mecanografiado usando una palabra clave abstracta antes de la palabra clave de clase.
No se puede crear una instancia de una clase abstracta. Pero otras clases pueden derivarse de él.
La clase que extiende una clase abstracta debe definir todos los métodos o propiedades abstractas.
La clase que extiende la clase abstracta debe llamar a super en el constructor.
Tomemos un ejemplo:

```JavaScript
 abstract class Children {
    name: string;
    
    constructor(name: string) {
        this.name = name;
    }

    display(): void{
        console.log(this.name);
    }

    abstract find(rollNo: number): Children;
}

class Student extends Children { 
    rollNo: number;
    
    constructor(name: string, rollNo: number) { 
        super(name); // must call super()
        this.rollNo = rollNo;
    }

    find(rollNo:number): Children { 
      /* 
      *
      *
      perfom db query to find 
      a student of the specific rollNo
      let the student be Luigi with roll no 101
      *
      *
      */
        let roll: number=101;
        let name: string = "Luigi";
        return new Student(name, roll);
    }
}

let emp: Children = new Student("John", 100);
emp.display(); 

let emp2: Children = emp.find(101);
emp2.display();

```

## 2. Inheritance (Herencia)

No es eficiente escribir bloques de códigos una y otra vez. A los desarrolladores les encanta la reutilización del código. La herencia proporciona reutilización de código a los desarrolladores. Es el mecanismo a través del cual una clase hereda o adquiere propiedades de otra clase.

La clase de la que se heredan las propiedades se denomina clase base/superior/padre y la clase que adquiere la propiedad se denomina clase derivada/secundaria/sub.

Tomemos un ejemplo de una organización que tiene gerentes y gerentes de área. Manager es la clase base con cuatro propiedades a saber. 'nombre', 'apellido', 'salario' y 'correo electrónico'. AreaManager también tendrá estas cuatro propiedades junto con una nueva propiedad llamada 'área'.

Está claro que si hacemos un conjunto de las propiedades de cada clase, AreaManager será un superconjunto de Manager. En otras palabras, las propiedades del administrador se pueden heredar al AreaManager.

![1_DFUlyiM5Zal6-JL8cdlPfw](https://user-images.githubusercontent.com/108378310/189501283-df5f301f-b3b9-4d2d-84fc-42e0eae5c8f7.png)


Entonces, para reutilizar los códigos/propiedades de Manager, podemos heredarlos dentro de AreaManager y se puede hacer usando la palabra clave extends.

nota: ' super ' es una palabra clave utilizada para llamar al constructor principal y su valor.

```JavaScript
// Base class
class Manager{               
  firstName : string;
  lastName : string;
  salary: number
  email: string;

  constructor(firstName: string, lastName: string, salary: number, email: string){
    this.firstName= firstName;
    this.lastName= lastName;
    this.email= email;
    this.salary= salary;
  }
}

//Derived class
class AreaManager extends Manager{ 
  area: string;
  constructor(firstName: string, lastName: string, salary: number, email: string, area: string){
    super(firstName, lastName, salary, email);
    this.area= area;
  }
}

const manager = new Manager("John", "Doe", 25000, "john@xyz.com");  
const areaManager = new AreaManager("Chun", "Li", 35000, "chun@xyz.com", "Los Angeles");

console.log(`Manager's name: ${manager.firstName} ${manager.lastName}`);
console.log(`Manager's salary: ${manager.salary}`);
console.log(`Area Manager's name: ${areaManager.firstName} ${areaManager.lastName}`);
console.log(`Area Manager's salary: ${areaManager.salary}`);
console.log(`Area Manager's area of duty: ${areaManager.area}`);
```
## 3. Polymorphism (Polimorfismo)
Poly significa muchos y el significado de morph es forma, por lo que el polimorfismo básicamente ejecuta una función de muchas maneras. El polimorfismo es otra forma después de la herencia para lograr la reutilización del código.

El polimorfismo se puede lograr mediante:

Sobrecarga de métodos
Anulación de métodos
Sobrecarga de métodos
En TypeScript podemos tener múltiples funciones con el mismo nombre usando diferentes tipos de parámetros y tipos de devolución. A diferencia de java, en mecanografiado el número de parámetros debe ser el mismo. Entendamos esto con dos ejemplos:

```JavaScript
class Example{
  
  /**
  function declaration
  **/
  add(a:string, b:string): string;
  add(a:number, b:number): number; // method add is overloaded by providinng different parameter type and return type
  
  /**
  function definition
  **/
  add(a:any, b:any):any{
    return a+b;
  }
  
}

let object= new Example();
  /**
  print to console
  **/
console.log(object.add("Hello ","John"));
console.log(object.add(1,1));
```

## 4. Encapsulation (Encapsulación)
Encapsular códigos y datos en una sola unidad se denomina encapsulación. Podemos lograrlo usando los modificadores de acceso. Por ejemplo, podemos crear una clase completamente encapsulada haciendo que todos sus miembros sean privados.


## 5. Class and 6. Object
Clases y Objetos
Consideremos una analogía de Juan que deseaba construir una casa. John primero se acercó a una arquitectura y la arquitectura le dio a John un plano de la casa antes de comenzar la construcción o la ocurrencia de la casa.

![1_cRVD88ogFfm05tBgrb0nxg](https://user-images.githubusercontent.com/108378310/189501557-4eb01b3b-3745-4bb0-ae78-226df74f9717.gif)

Aquí podemos relacionar el plano con una clase y después de la construcción, la casa será el objeto.

Observe que el plano no tiene ningún espacio en la superficie de la tierra, mientras que la casa tendrá algo de espacio en la superficie de la tierra. De manera similar, las clases no consumen espacio en la memoria, pero los objetos consumen algo de espacio en la memoria.

Tomemos un ejemplo usandotypescript:

```JavaScript
class Employee{
  name: string;
  age: number;
  constructor(n: string, a: number){
    this.name= n;
    this.age=a;
  }
}

let emp = new Employee("John", 24); // object emp instanciated of type Employee and hence consumed some space in the memory
console.log(emp.name); // accessed the property 'name' of the object emp of type Employee
console.log(emp.age);

//output:
//John
//24
```
En el ejemplo anterior, hemos definido una clase llamada Empleado que tiene dos miembros, uno es "nombre" de tipo cadena y otro es "edad" de tipo número. En la línea número 10 hemos instanciado un objeto llamado emp de tipo Empleado. Dado que emp es el objeto de tipo Empleado, debe tener la propiedad de nombre y edad. En las líneas 11 y 12 estamos accediendo a esas propiedades usando el operador punto (.).

Nota
 - Constructor es un tipo especial de método que inicializa el objeto. En el ejemplo anterior en la línea número 10, los dos argumentos a saber. “John” y 24 se pasan al constructor de la clase Empleado.

 - “this” es una variable de referencia que hace referencia al objeto actual.

# 7. Instance (Instancia)

La instancia de TypeScript es uno de los operadores, y se usa para determinar el constructor específico, y creará el objeto de las clases. Llamará a los métodos con la ayuda de una instancia como esa si usamos una interfaz que se puede implementar y extender a través de las clases.

# 8. Interface  (Interfaz)

Es una sintaxis para una clase.
Contiene sólo la declaración de métodos y propiedades. Las clases que implementan una interfaz deben implementar todos sus miembros y métodos.
No se puede instanciar.
Se utiliza para verificar el tipo de un objeto, ya sea que esté seguido por una estructura específica o no.
Las interfaces se pueden heredar de otras interfaces utilizando la palabra clave extends.
Las clases usan la palabra clave implements para implementar una interfaz.
Tomemos un ejemplo:

```JavaScript
interface IUser{
  name: string;
  email: string;
}

interface IEmployee extends IUser{
  employeeId: number;
}

class Employee implements IEmployee{
  name: string;
  email: string;
  employeeId: number;
  constructor(name: string, email: string, employeeId: number){
    this.name= name;
    this.email= email;
    this.employeeId= employeeId;
  }
}

```


# 9. Access Modifiers (Modificadores de acceso)
Para comprender la encapsulación, primero debemos comprender los modificadores de acceso. Hay tres tipos de modificadores de acceso en mecanografiado:

Public
Private
Protected

Public (Público)

De forma predeterminada, todos los miembros de una clase son públicos en mecanografiado, lo que significa que podemos acceder a ellos y modificarlos fuera de la clase. Tomemos un ejemplo:

![1_82gKfZ4L1VDEj9U4iXtzYA](https://user-images.githubusercontent.com/108378310/189503447-b65a3ed4-2720-421a-b32a-4552f5c8ad06.png)

Output

![1_GgZv-jeFcGLIVoemlt_BFA](https://user-images.githubusercontent.com/108378310/189503468-5813d497-1fef-4b23-b3aa-8d7047b70c68.png)

Private (Privado)
Los miembros privados pueden acceder o modificar dentro de la clase, pero no fuera de la clase. Tomemos un ejemplo:

![1_EnaOEB2ZZ_h1U93U-rB6hQ](https://user-images.githubusercontent.com/108378310/189503504-6fca9650-d6cc-4329-b933-2dd6f33b8400.png)

Output

![1_pm5nmIr4Ow76lFqpBDP9fw](https://user-images.githubusercontent.com/108378310/189503506-fbcd22c0-7085-42cd-8163-788df0bc36a1.png)

Aquí la edad es un miembro privado al que se accede mediante el método de visualización que se encuentra dentro de la clase Empleado.

Ahora veamos otro escenario:

![1_36FXJ38e4CuFKaQC-AebJg](https://user-images.githubusercontent.com/108378310/189503528-0c0d156a-3183-4e65-a333-f4ef03a80524.png)

Output

![1_EjkPMLr-yQpfT-UyPyfgEg](https://user-images.githubusercontent.com/108378310/189503601-5a7b115b-ff71-48df-b64b-1427db34dd2c.png)

Aquí estamos tratando de acceder a la edad fuera de la clase que no está permitida.


## 10. Constructors (Constructor)

Un constructor es una función especial de la clase que se encarga de inicializar las variables de la clase. TypeScript define un constructor usando la palabra clave constructor. Un constructor es una función y, por lo tanto, se puede parametrizar. La palabra clave this se refiere a la instancia actual de la clase.



