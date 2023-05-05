--1. Muestra el nombre de todos los bailes.--

for $baile in //bailes/baile/nombre/text()
return $baile

--2. Muestra el nombre y precio de todos los bailes.--

for $baile in //bailes/baile
return 
<baile>
  <nombre>{$baile/nombre/text()}</nombre>
  <precio>{$baile/precio/text()}</precio>    
</baile>

--3. Muestra el nombre y precio de todos los bailes donde su precio es mayor que 40.--

for $baile in //bailes/baile
where $baile/number(precio) > 40
return 
<baile>
  <nombre>{$baile/nombre/text()}</nombre>
  <precio>{$baile/precio/text()}</precio> 
</baile>

--4. Mostrar los bailes ordenados por nombre.--

for $baile in //bailes/baile/nombre/text()
order by $baile
return $baile

--5. Mostrar los nombres de los bailes que contienen una a.--

for $baile in //bailes/baile/nombre/text()
where contains($baile, "a")
return $baile

--6. Mostrar el nombre de los bailes donde el apellido del profesor sea Lozano.--

for $baile in //bailes/baile
where ends-with($baile/profesor, "Lozano")
return $baile/nombre/text()

--7. Mostrar todos los bailes, excepto el 3 y 5.--

for $baile in //bailes/baile
where $baile/@id != 3 and $baile/@id != 5
return $baile

--8. Mostrar profesores que den clases de bailes por una cuota mensual.--

for $baile in //bailes/baile
where $baile/precio/@cuota = "mensual"
return $baile/profesor/text()

--9. Mostrar el nombre de los bailes de la sala 1, que se pague con euros y el precio sea menor a 35.--

for $baile in //bailes/baile
where $baile/sala/text() = "1" and $baile/precio/@moneda = "euro" and $baile/number(precio) < 35
return $baile/nombre/text()
                                                                                                
--10. Obtener el precio del baile con el precio más caro.--
                                                                                                
max(
  for $baile in //bailes/baile
  return $baile/precio/text()  
)     
                                                                                                
--11. Obtener el precio y el nombre del baile con el precio más caro.--

let $max := max(
  for $baile in //bailes/baile
  return $baile/precio/text()  
)
for $baile in //bailes/baile
where $baile/precio = $max
return 
<baile>
  <nombre>{$baile/nombre/text()}</nombre>
  <precio>{$baile/precio/text()}</precio>
</baile>

--otra opción--

for $baile in //bailes/baile/precio
where $baile = max(//precio)
return $baile/text() | $baile/../nombre/text()

--12.Obtener el precio del baile con el precio más barato.--

min(
for $baile in //baile/baile
return $baile/precio/text()
)

--13.Obtener el precio y el nombre del baile con el precio más barato.--

let $min := min(
  for $baile in //bailes/baile
  return $baile/precio/text()  
)
for $baile in //bailes/baile
where $baile/precio = $min
return 
<baile>
  <nombre>{$baile/nombre/text()}</nombre>
  <precio>{$baile/precio/text()}</precio>
</baile>

--14.Obtener la suma del precio por el número de plazas de todas las clases. Resultado: 29250.--

sum(
  for $baile in //bailes/baile
  return $baile/precio * $baile/plazas
)

--15.Obtener el dia, mes y año de los bailes mensuales, tanto del comienzo como del final.--

for $baile in //baile
where $baile/precio/@cuota = "mensual"
return 
<baile>
  <comienzo>
    <dia>{day-from-date($baile/comienzo)}</dia>
    <mes>{month-from-date($baile/comienzo)}</mes>
    <anio>{year-from-date($baile/comienzo)}</anio>
  </comienzo>
  <fin>
    <dia>{day-from-date($baile/fin)}</dia>
    <mes>{month-from-date($baile/fin)}</mes>
    <anio>{year-from-date($baile/fin)}</anio>
  </fin>
</baile>

--16.Obtener los bailes que tengan mas de 100 dias de diferencia.--

for $baile in //baile
where days-from-duration(xs:date($baile/fin)-xs:date($baile/comienzo)) > 100
return $baile

--17. Obtener la diferencia de dias del comienzo del baile con la fecha actual.--

for $baile in //baile
return days-from-duration(current-date()-xs:date($baile/comienzo))
                                                                                                
                                                                                                
