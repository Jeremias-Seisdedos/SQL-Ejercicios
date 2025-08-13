# Ejercicio Practico

## Ejercicio 1: Contar cuántas películas empiezan con la letra S.


```sql
SELECT COUNT(title) FROM film WHERE title LIKE 'S%'
```


## Ejercicio 2: Sumar la duración en minutos de todas las películas clasificadas para PG-13.


```sql
SELECT SUM(length) FROM film WHERE rating='PG-13'
```

## Ejercicio 3: Mostrar todos los emails de los clientes junto con la suma de todas las películas que rentaron.


```sql
SELECT c.email, COUNT(rental_date) AS peliculas_rentadas FROM customer AS c
JOIN rental r ON c.customer_id=r.customer_id
GROUP BY c.email
ORDER BY c.email ASC
```

## Ejercicio 4: Mostrar el número de teléfono de la dirección que tiene el código postal más grande.

```sql
SELECT phone,address,postal_code FROM address WHERE postal_code=(SELECT MAX(postal_code) FROM address)

```

## Ejercicio 5: Mostrar la dirección, el distrito y el nombre de la ciudad del primer cliente inactivo.

```sql
SELECT a.address ,a.district, ci.city  FROM customer as cu
JOIN address a ON a.address_id=cu.address_id
JOIN city ci ON ci.city_id= a.city_id
WHERE cu.active=0
LIMIT 1

```
