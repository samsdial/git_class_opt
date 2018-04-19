Optime Univesity - Css 
===================

Bienvendido a la introducción de Css teorico practio.

Contenido
-------------

### Glosario de Css
- Sintaxis
- Selectores
- Herencia
- Texto

## Herenecia
Se refiere a la forma en que las propiedade fluyen a través de la página. Un elemento hijo generadodo tomará las caracteristicas del elemento padre a menos que se defina de otra forma
 
## Sintaxis
Css está compuesto por reglas de estilo

Selector, propiedad, valor

```css
h1 {
    color: red;
}
```
## Selectores 

- Selectores de tipo: apuntan a los tipos de elememots de la pagina
- Selectores de ID: Permite aplicar un estilo a un elemento HTML, que tenga un atirbuto ID

```css
#prueba {
    color: red;
}
```

- Selectores de Clase: Permite aplicar un estilo a un elemento HTML, que tenga un atirbuto class

```css
.prueba {
    color: red;
}
```
- Selectores descentientes: Se usa para seleccionar elementos de forma decendiente.

```css
.prueba p {
    color: red;
}
/*Afecta solo a los hijos (p) que esten en el div de clase prueba*/
```
## Texto
- font-family
    Especifica la familia fuente para el elemento
    familia funte(Arial) familia generica(Serif o Monospace)
    
    --Especificaciones--
    - Agregar más de una familia usando (,)
    - Registra un sistema de respaldo usando ("respaldo")
    
    --Buenas Practias--
    - Agregar una familia generica
    
- font-size
    Especifique el tamaño de una letra con valores nuemericos como px, em, rems
    Px = Pixels
    em = Tamaño de letra relaticva y permite que la mayoria de navegadores redimensionen el texto
    ** Para calcular el tamaño en em = pixels/16 