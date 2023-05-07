
```
<?xml version="1.0" encoding="UTF-8"?>
<bookstore>
  <book category="COOKING">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="CHILDREN">
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
  <book category="WEB">
    <title lang="en">XQuery Kick Start</title>
    <author>James McGovern</author>
    <author>Per Bothner</author>
    <author>Kurt Cagle</author>
    <author>James Linn</author>
    <author>Vaidyanathan Nagarajan</author>
    <year>2003</year>
    <price>49.99</price>
  </book>
  <book category="WEB">
    <title lang="en">Learning XML</title>
    <author>Erik T. Ray</author>
    <year>2003</year>
    <price>39.95</price>
  </book>
</bookstore> 
```
### 1.	Mostrar los títulos de los libros con la etiqueta "titulo".
```
for $title in /bookstore/book/title/text()
return $title
```
### 2.	Mostrar los libros cuyo precio sea menor o igual a 30. Primero incluyendo la condición en la cláusula "where" y luego en la ruta del XPath.
```
for $book in /bookstore/book
where $book o/price <= 30
return $book
```
### 3.	Mostrar sólo el título de los libros cuyo precio sea menor o igual a 30.
```
for $book in /bookstore/book[price<=30]
return $book/title                       
```
### 4.	Mostrar sólo el título sin atributos de los libros cuyo precio sea menor o igual a 30.
```
for $book in /bookstore/book[price<=30]
return $book/title/text()
```
### 5.	Mostrar el título y el autor de los libros del año 2005, y etiquetar cada uno de ellos con "lib2005".
```
for $book in /bookstore/book 
where $book/year = 2005 
return <lib2005>{$book/author/text()}, {$book/title/text()}</lib2005>                                      
```
### 6.	Mostrar los años de publicación, primero con "for" y luego con "let" para comprobar la diferencia entre ellos. Etiquetar la salida con "publicacion".
```
for $year in /bookstore/book/year
return $year

--con let--

let $year := /bookstore/book/year
return $year
```
### 7.	Mostrar los libros ordenados primero por "category" y luego por "title" en una sola consulta.
```
for $book in /bookstore/book
order by $book/@category and $libro/title
return $book
```
### 8.	Mostrar cuántos libros hay, y etiquetarlo con "total".
```
let $book := /bookstore/book
let $count := count($book)
return <total>{$count}</total>
```
### 9.	Mostrar los títulos de los libros y al final una etiqueta con el número total de libros.
```
let $total := count (/bookstore/book),
    $titles := (
      for $book in /bookstore/book/title 
      return $book/text()) 
return 
      <resultado>
        {$titles}
        <total_libros>{$total}</total_libros>
      </resultado>
```
### 10.	Mostrar el precio mínimo y máximo de los libros.
```
let $price := /bookstore/book/price
return (max($price), min($price))
```
### 11.	Mostrar el título del libro, su precio y su precio con el IVA incluido, cada uno con su propia etiqueta. Ordénalos por precio con IVA.
```
  for $book in /bookstore/book
  let $price := $book/price * 0.04
  return
   <titulo>{$book/title/text()}</titulo>|<precio>{$book/price/text()}</precio>|<precio_iva>{$book/price * 0.04}</precio_iva>
```
### 12.	Mostrar la suma total de los precios de los libros con la etiqueta "total".
```
let $total := sum(/bookstore/book/price)
return <total>{ $total }</total>

```
### 13.	Mostrar cada uno de los precios de los libros, y al final una nueva etiqueta con la suma de los precios.
```
let $books := /bookstore/book
for $book in $books
return <precio>{ $book/price/text() }</precio>|<total>{ sum($books/price) }</total>
```
### 14.	Mostrar el título y el número de autores que tiene cada título en etiquetas diferentes.
```
for $book in bookstore/book
  return <title>{ $book/title/text() }</title>|<num_autor>{ count($book/author) }</num_autor>
```
### 15.	Mostrar en la misma etiqueta el título y entre paréntesis el número de autores que tiene ese título.
```
```
### 16.	Mostrar los libros escritos en años que terminen en "3".
```
```
### 17.	Mostrar los libros cuya categoría empiece por "C".
```
```
### 18.	Mostrar los libros que tengan una "X" mayúscula o minúscula en el título.
```
```
### 19.	Mostrar el título y el número de caracteres que tiene cada título, cada uno con su propia etiqueta.
```
```
### 20.	Mostrar todos los años en los que se ha publicado un libro eliminando los repetidos. Etiquétalos con "año".
```
```
### 21.	Mostrar todos los autores eliminando los que se repiten y ordenados por el número de caracteres que tiene cada autor.
```
```
### 22.	Mostrar los títulos en una tabla de HTML.
```
```
