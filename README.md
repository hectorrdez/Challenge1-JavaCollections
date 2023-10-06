# ArrayList

a) Definición y creación de una colección
Definición:
ArrayList en Java es una implementación de la interfaz List que utiliza un arreglo dinámico para almacenar elementos. Proporciona métodos para manipular elementos dinámicamente.

**Constructores utiles**
```java
// Constructor vacío 
ArrayList<String> A = new ArrayList<>();

// Constructor con capacidad inicial
ArrayList<String> A = new ArrayList<>(10);

// Constructor que acepta otra coleccion
ArrayList<String> B = new ArrayList<>();
ArrayList<String> A = new ArrayList<>(B);
```

b) Metodos/Propiedades Generales

**Tamaño**
```java
// size() es un metodo que devuelve el tamaño de la coleccion (sin tener en cuenta si sus elementos tambien son colecciones, solo cuenta la "primera" dimensión)
ArrayList<String> A = new ArrayList<>();

List<String> B = new List<>();
saludos.add("A");
saludos.add("B");

A.add(B);
int tamanoA = A.size(); // --> tamanoA = 1
int tamanoB = B.size(); // --> tamanoB = 2
```

**Acceso por índice/Clave**
```java
// El acceso por índice nos permite crear 
ArrayList<String> A = new ArrayList<>();
A.add("A");

// String elementoA = A.get(indiceElementoA);
String elementoA = A.get(0); // Devolverá "A"
```

c) Añadir Datos a la Colección

**Añadir Elementos desde el Constructor**
```java
ArrayList<String> A = new ArrayList<>(Arrays.asList("A","B","C"));
```

**Añadir Elementos desde Otras Colecciones**
```java
List<String> B = new ArrayList<>();
A.addAll(B);
```

# HashMap