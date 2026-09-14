<h1 align='center'>Ayudantía 8  - POO Invierno</h1>
<h5 align='center'>Profesor: Cristhian Rabi<br>  Ayudante: Paulo Araya</h5>
<h6 align='center'>10 de Agosto de 2026</h6>
Los patrones de diseño son soluciones reutilizables para problemas recurrentes de diseño de software, que nos ayudan a estructurar mejor el código, hacerlo más flexible y más fácil de mantener. 

### Singleton:
El patron Singleton se trata de solo poder instanciar un objeto de una clase, es lo más parecido que se tiene a una variable global dentro de tu programa.

Sirve principalmente para mantener un único estado dentro de tu dominio, ej: para acceder a las mismas ArrayList que guardan tus objetos.

```java
public class Fiesta {
    private static Fiesta instancia;
    private ArrayList<String> invitados;

    private Fiesta() {
        invitados = new ArrayList<>();
    }

    public static Fiesta getInstancia() {
        if (instancia == null) {
            instancia = new Fiesta();
        }
        return instancia;
    }

    public void agregarInvitado(String nombre) {
        invitados.add(nombre);
    }

    public ArrayList<String> getInvitados() {
        return invitados;
    }
}

// main
Fiesta a = Fiesta.getInstancia(); // ambos apuntan al mismo objeto
Fiesta b = Fiesta.getInstancia();
a.agregarInvitado("Ana");
System.out.println(b.getInvitados()); // [Ana]
```

### Factory:
El patrón Factory centraliza la creación de objetos en un único lugar, delegando la decisión de qué clase especifica instanciar según algún parámetro o condición.

Sirve para abstraer la lógica compleja de elección y evitar que el resto del programa dependa de clases concretas, ej: dado un `String` tipo de figura, se retorna un `Circulo`, `Cuadrado` o `Triangulo` sin que quien llama conozca los detalles.

```java
public interface Figura {
    double getArea();
}

public class Circulo implements Figura {
    private double radio;
    public Circulo(double radio) { this.radio = radio; }
    public double getArea() { return Math.PI * radio * radio; }
}

public class Cuadrado implements Figura {
    private double lado;
    public Cuadrado(double lado) { this.lado = lado; }
    public double getArea() { return lado * lado; }
}

public class FiguraFactory {
    public static Figura crearFigura(String tipo, double param) {
        switch (tipo) {
            case "circulo":  return new Circulo(param);
            case "cuadrado": return new Cuadrado(param);
            default: throw new IllegalArgumentException("Tipo desconocido: " + tipo);
        }
    }
}

// main
Figura f = FiguraFactory.crearFigura("circulo", 2.0);
System.out.println(f.getArea());
```

### Strategy:
El patrón Strategy permite definir una familia de algoritmos intercambiables en tiempo de ejecución, encapsulando cada uno en una clase distinta que implementa una misma interfaz.

Sirve para evitar cadenas de `if/else` cuando un comportamiento puede variar, ej: un `Personaje` puede cambiar su forma de atacar (`Espada`, `Arco`, `Magia`) simplemente asignando otra estrategia.

```java
public class Personaje {
    private EstrategiaAtaque ataque;

    public void setAtaque(EstrategiaAtaque ataque) { this.ataque = ataque; }

    public void ejecutarAtaque() { ataque.atacar(); }
}
// strategy ============================================

public interface EstrategiaAtaque {
    void atacar();
}

public class AtaqueEspada implements EstrategiaAtaque {
    public void atacar() { System.out.println("espada"); }
}

public class AtaqueArco implements EstrategiaAtaque {
    public void atacar() { System.out.println("arco"); }
}

public class AtaqueMagia implements EstrategiaAtaque {
    public void atacar() { System.out.println("magia"); }
}

// main ================================================
Personaje p = new Personaje();
p.setAtaque(new AtaqueEspada());
p.ejecutarAtaque();        // espada
p.setAtaque(new AtaqueMagia());
p.ejecutarAtaque();        // magia
```

### Visitor:
El patrón Visitor permite agregar nuevas operaciones sobre un grupo de objetos sin modificar sus clases, separando el algoritmo de la estructura sobre la que actúa. 

Sirve para realizar distintas acciones sobre cada elemento de una colección, ej: un `Visitador` que exporta a JSON, calcula el área o dibuja, aplicado a las distintas figuras de un listado sin tocar sus clases.

```java
public interface Figura {
    void aceptar(Visitador v);
}

public class Circulo implements Figura {
    double radio;
    public Circulo(double r) { radio = r; }
    public void aceptar(Visitador v) { v.visitar(this); }
}

public class Cuadrado implements Figura {
    double lado;
    public Cuadrado(double l) { lado = l; }
    public void aceptar(Visitador v) { v.visitar(this); }
}

public interface Visitor {
    void visitar(Circulo c);
    void visitar(Cuadrado c);
}

public class VisitorArea implements Visitor {
    private static ArrayList<Double> areas = new ArrayList<>();
    
    public void visitar(Circulo c) {
        double area = Math.PI * c.radio * c.radio;
        System.out.println("Area circulo: " + area);
        areas.add(area);
    }
    public void visitar(Cuadrado c) {
        double area = c.lado * c.lado;
        System.out.println("Area cuadrado: " + area);
        areas.add(area);
    }
    
    // agregar clases aqui...
    
    private void mostrarPromedioAreas() {
        double suma = 0;
        for (double d : areas) {
            suma += d;
        }
        System.out.println("Promedio total: " + suma / areas.size());
        areas.clear();
    }
}

// Uso: se agregan operaciones sin modificar las clases de las figuras
ArrayList<Figura> figuras = new ArrayList<>();
figuras.add(new Circulo(2.0));
figuras.add(new Cuadrado(3.0));

Visitor v = new VisitorArea();
for (Figura f : figuras) {
    f.aceptar(v); // le pasamos el visitor
}
v.mostrarPromedioAreas();
```

> Fácilmente podríamos agregarle a cada clase un getArea(), pero cuando se tiene un código con más de 30 tipos de figuras, es mucho mejor tener un solo lugar para trabajar.