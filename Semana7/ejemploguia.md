
## Usando el concepto OOP en la práctica Typescript

La idea de este artículo es modificar una pequeña parte del software virtual aplicando el concepto OOP. En este artículo, asumo que está familiarizado con OOP y las definiciones de clases, objetos, métodos y atributos. Tomaré las primeras etapas del software de flujo de audio como ejemplo.
Empezaremos con lo siguiente:

Una clase Album y una clase Track, y otro archivo para reproducir pistas.

```JavaScript
export class Album {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}

export class Track {
  name: string;
  length: number;
  album: Album;

  constructor(name: string, length: number, album: Album) {
    this.name = name;
    this.length = length;
    this.album = album;
  }
}
.
// meanwhile in another file ...

function play() {
    // Finds the track 
    // Play it
}

```

Empezaremos a aplicar los conceptos OOP, pero seguiremos siendo simples, especialmente porque el objetivo aquí es entender estos conceptos en lugar de construir APIs de flujo de audio reales.

## Encapsulación
Todos los atributos de la clase de pista pueden ser accedidos por cualquiera, vamos a cambiar esto envolviéndolos. La encapsulación es un mecanismo para ocultar información que son miembros de una clase, como propiedades y métodos, mediante el uso de modificadores públicos, protegidos y privados.

Los miembros comunes son accesibles en cualquier lugar, y este es el modificador predeterminado.

Los miembros protegidos son visibles en la clase que los declara y sus subclases.

Los miembros privados sólo son visibles en la clase que los declara.
Para encapsular todos estos atributos, seguimos estos pasos:
add Modifier private
añadir _ antes del nombre de la propiedad, por ejemplo _name
implementa los accesores get y set. Estos métodos se invocan cada vez que se intenta obtener o establecer un valor de propiedad.
La configuración de todas las propiedades a las propiedades privadas de la clase de pista será la siguiente:

```JavaScript
export class Track {
  private _name: string;
  private _length: number;
  private _album: Album;

  constructor(name: string, length: number, album: Album) {
    this._name = name;
    this._length = length;
    this._album = album;
  }

  get name(): string {
    return this._name;
  }

  set name(name: string) {
    this._name = name;
  }

  get length(): number {
    return this._length;
  }

  set length(length: number) {
    this._length = length;
  }

  get album(): Album {
    return this._album;
  }

  set album(album: Album) {
    this._album = album;
  }
}

```

## Abstracción
La abstracción es ocultar detalles complejos al usuario, por ejemplo, para conducir un coche, usted no necesita saber cómo funciona su motor, por lo que en el coche es abstracción y le proporciona una interfaz (volante, pedal, cambio de marchas, etc.) que sólo necesita saber cómo operar.
Vea cómo se reproduce una pista. Primero encuentra la pista y luego la reproduce. ¿Parece bastante simple, ahora Supongamos que tenemos que hacer lo mismo en todas partes cuando tenemos que reproducir una pista, lo que sería redundante, pero hay otros problemas, cada persona que escribe código para reproducir la pista necesita saber cómo hacerlo, y si algo cambia en la reproducción de la pista? Tenemos que cambiarlo en muchos lugares.
Esta es una oportunidad lógica Abstract a, y lo hacemos moviéndolo dentro de la clase de pista. Ahora, cada vez que una pista necesita ser reproducida, cualquiera simplemente invoca el método de reproducción sin conocer sus detalles:

```JavaScript
export class Track {
  private _name: string;
  private _length: number;
  private _album: Album;

  constructor(name: string, length: number, album: Album) {
    this._name = name;
    this._length = length;
    this._album = album;
  }

  get name(): string {
    return this._name;
  }

  set name(name: string) {
    this._name = name;
  }

  get length(): number {
    return this._length;
  }

  set length(length: number) {
    this._length = length;
  }

  get album(): Album {
    return this._album;
  }

  set album(album: Album) {
    this._album = album;
  }

    function play() {
        // Play it
    }
}

// To instantiate and play a track
const album = new Album("Rocks");
const track = new Track("Combination", 264, album);

track.play();

Derecho de herencia
¿Supongamos que ahora nuestro software de streaming de audio necesita añadir soporte para podcasts que tienen episodios, cómo vamos a hacer esto? Simplemente podemos a ñadir una clase de podcast y un atributo de tipo a la clase de pista:
export class Podcast {}

export class Track {
  private _name: string;
  private _length: number;
    private _type: string; // track or episode
  private _album?: Album;
  private _podcast?: Podcast;


    ...
}

```

Esto es factible, pero es más difícil de mantener, y tenemos que considerar el comportamiento de type en esta clase, como el método play. Si tenemos que apoyar otro tipo de medios, tendremos que revisar todo de nuevo, y este método al menos viola los principios de dos sólidos, pero este es el tema de otro artículo.
¿Entonces, cómo podemos resolver este problema? Herencia de entrada: un mecanismo que nos permite crear jerarquías de clases donde las subclases pueden heredar propiedades y comportamientos de sus superclases. Esto es bueno para la reutilizabilidad.
Por lo tanto, la solución que propongo es la siguiente:
En primer lugar, cree una clase de audio cuyas propiedades y comportamientos son comunes en los conjuntos de pistas y dramas, que será nuestra superclase:

```JavaScript
export class Audio {
  private _name: string;
  private _length: number;

  constructor(name: string, length: number) {
    this._name = name;
    this._length = length;
  }

    /** getters and setters */

    function play() {
        // Play it
    }
}
```


A continuación, la clase Track se deriva de la clase audio, lo que significa que heredará las propiedades y el comportamiento de la clase audio:

```JavaScript
export class Track extends Audio {
  private _album: Album;

  constructor(name: string, length: number, album: Album) {
    super(name, length);
    this._album = album;
  }

  get album(): Album {
    return this._album;
  }

  set album(album: Album) {
    this._album = album;
  }
}

```
La palabra clave extends significa que la clase Track hereda de la clase audio, y debido a que Track extiende otra clase, tenemos que llamar a super en el constructor, incluso si no hay ninguna propiedad que pasar a la superclase. Además, super se puede utilizar para invocar métodos de clase padre.
Cabe señalar que superclass puede llamarse parent class, y las subclases también pueden llamarse child class.
Finalmente, creamos clases de podcasts e episodios que también ampliarán las clases de audio:

```JavaScript
export class Podcast {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}

export class Episode extends Audio {
  private _podcast: Podcast;

  constructor(name: string, length: number, podcast: Podcast) {
    super(name, length);
    this._podcast = podcast;
  }

  get podcast(): Podcast {
    return this._podcast;
  }

  set podcast(podcast: Podcast) {
    this._podcast = podcast;
  }
}

```


## Polimorfismo
Ahora Supongamos que, por alguna razón, cuando el usuario cierra el streamer y lo abre de nuevo, sólo los clips de podcast necesitan ser reproducidos donde dejaron de reproducirse, y las pistas deben comenzar desde cero. ¿Como usted sabe, el método de reproducción está en la clase de audio, por lo que es lo mismo para los episodios y pistas. Cómo podemos hacer esto? ¡Ven a salvarme!
El Polimorfismo es un concepto en el que un objeto puede tener muchas formas, y como la palabra implica, lo usaremos para hacer que los métodos de reproducción se comporten de manera diferente en la pista y la trama. En la práctica, lo hacemos Reescribiendo en la clase de episodio, lo que significa que Implementamos el método de juego en la clase de episodio de una manera diferente a implementar el método de juego en la superclase:

```JavaScript
export class Episode extends Audio {

    /** everything else remains the same */

    function play() {
      // Check where it left off
      // Play it
    }
}
```


Otra forma de implementar el Polimorfismo es sobrecargar métodos que tienen el mismo nombre, pero diferentes firmas, como diferentes tipos de datos o números de parámetros, pero que son diferentes en Typescript. Para sobrecargar métodos, debemos a ñadir parámetros opcionales o declaraciones de funciones sobrecargadas a la interfaz e implementar la interfaz.
Es decir, la idea es simplemente explicar lo que cada uno es y proporcionar un ejemplo. Me gustaría centrarme en estos cuatro conceptos y pasar por alto otros, por lo que todavía hay margen para mejorar esta implementación.
