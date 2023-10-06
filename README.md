## ArrayList

### a) Definición y creación de una colección
Definición:
ArrayList en Java es una implementación de la interfaz List que utiliza un arreglo dinámico para almacenar elementos. Proporciona métodos para manipular elementos dinámicamente.

**Constructores utiles**
```java
// Constructor vacío 
ArrayList<String> A = new ArrayList<>();

// Constructor con capacidad inicial
// ArrayList<T> A = new ArrayList<>(n) --> A = {null, null, ...} hasta n veces
ArrayList<String> A = new ArrayList<>(3); // A = {null, null, null}

// Constructor que acepta otra coleccion
ArrayList<String> B = new ArrayList<>();
ArrayList<String> A = new ArrayList<>(B);  // A = B
```

### b) Metodos/Propiedades Generales

**Tamaño**
```java
// size() es un metodo que devuelve el tamaño de la coleccion (sin tener en 
// cuenta si sus elementos tambien son colecciones, solo cuenta la "primera" 
// dimensión)
ArrayList<String> A = new ArrayList<>();

List<String> B = new List<>();
saludos.add("A"); // B = {"A"}
saludos.add("B"); // B = {"A", "B"}

A.add(B);
int tamanoA = A.size(); // --> tamanoA = 1
int tamanoB = B.size(); // --> tamanoB = 2
```
***
**Acceso por índice/Clave**
```java
// El acceso por índice nos permite crear 
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}

// String elementoA = A.get(indiceElementoA);
String elementoA = A.get(0); // Devolverá "A"
```

### c) Añadir Datos a la Colección

**Añadir Elementos desde el Constructor**
```java
ArrayList<String> A = new ArrayList<>(Arrays.asList("A","B","C")); // A = {"A" , "B", "C"}
```
***
**Añadir Elementos desde Otras Colecciones**
```java
ArrayList<String> B = new ArrayList<>();
B.add("A"); // B = {"A"}
B.add("B"); // B = {"A", "B"}

ArrayList<String> A = new ArrayList<>();
A.addAll(B); // A = {"A" , "B"}
```
***
**Añadir Elementos Mediante Código**
```java
ArrayList<String> A = new ArrayList<>();
A.add("A") // A = {"A"}

ArrayList<ArrayList<String>> B = new ArrayList<>();
B.add(A) // B = {{"A"}}
```
### d) Eliminar datos de la Colección

**Eliminar Elementos Mediante Código**
```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}

// Eliminación a través del elemento que contiene
A.remove("B"); // A = {"A", "C"}

// Eliminación a través del indice del elemento
A.remove(1); // A = {"A"}
```

> **Nota importante:** La eliminación a través del elemento **solo elimina el primer elemento** que coincida con el elemento a borrar: <br>```A = {"A", "B", "C", "B"} ---> A.remove("B") ---> A = {"A", "C", "B"}```

***

**Eliminar Elementos usando Otra Colección**

Haciendo uso del metodo _**removeAll**_ eliminamos **todos** los elementos que coincidan con la colección que le introducimos en el metódo.

```java
ArrayList<String> B = new ArrayList<>();
B.add("A"); // B = {"A"}
B.add("C"); // B = {"A", "C"}

ArrayList<String> A = new ArrayList<>();
A.addAll(B); // A = {"A", "C"}
A.add("B"); // A = {"A", "C", "B"}

A.removeAll(B); // A = {"B"}
```

***

**Eliminar Elementos usando un Predicado**

```java
ArrayList<int> A = new ArrayList<>();
A.add(1); // A = {1}
A.add(3); // A = {1, 3}
A.add(5); // A = {1, 3, 5}
A.add(7); // A = {1, 3, 5, 7}

// A.removeIf(element -> condicion) ---> condicion = true ---> elimina "element"
A.removeIf(element -> element > 5) // A = {1, 3}
```

### e) Recorrer la Colección

**Recorrer haciendo uso de un for**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}
A.add("D"); // A = {"A", "B", "C", "D"}

for(int i = 0; i < A.size(); i++){
    String elemento = A.get(i); // Siendo elemento el String devuelto de la colección
    System.out.println(elemento);
}
```

***

**Recorrer haciendo uso de un foreach**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}
A.add("D"); // A = {"A", "B", "C", "D"}

for(String s : A){
    System.out.println(s); // Siendo s el String devuelto de A
}
```

**Recorrer haciendo uso de Iterator**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}

Iterator<String> iteratorA = A.iterator(); // Creamos el iterador
while (iteratorA.hasNext()) {
    String elemento = iteratorA.next(); // Siendo elemento el String devuelto de A
    System.out.println(elemento);
}
```

***

**Recorrer haciendo uso de programacion funcional**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}

A.forEach(elemento -> {
    System.out.println(elemento); // Siendo elemento el String devuelto de A
});
```

> **Nota importante:** si se realiza alguna modificación sobre la lista o alguno de sus elementos mientras se recorre usando un _foreach_ o usando _Iterator_, se lanzará la una _**ConcurrentModificationException**_.

### f) Búsqueda de Elementos

**Realizar una búsqueda con un bucle (For/Foreach/Iterator)**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}

for(String elemento : A){
    if(elemento.equals("C")){
        // Se ha encontrado el elemento
    }
}
```

***

**Realizar una búsqueda con Expresiones Lambda (Stream)**

```java
ArrayList<String> A = new ArrayList<>();
A.add("A"); // A = {"A"}
A.add("B"); // A = {"A", "B"}
A.add("C"); // A = {"A", "B", "C"}

boolean encontrado = A.stream().anyMatch(elemento -> elemento.equals("C")); 
// Devuelve true si hay alguna coincidencia
```
***

**Realizar una búsqueda con Api Stream (Filtrado/Collect)**

```java
List<String> subLista = lista.stream().filter(condición).collect(Collectors.toList());

```

## HashMap