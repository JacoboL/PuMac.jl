# PuMAC

Paquete de julia de de apoyo para el uso de archivos csv

### Pre-requisitos 

Es necesario tener los paquetes 
`CSV`
`DataFrames`
`JLD`
`FileIO`

### Instalación 

```julia
using Pkg
Pkg.add(url = "https://github.com/JacoboL/PuMac.jl")
```
### Función

Para usar el paquete
```julia
using PuMac
```
#### Unir()

```julia
unir(archivos::Array, columnas::Array)
```
Une las `columnas` deseadas de los `archivos`.

```julia
unir(archivos::Array, columnas::Array, nombre_archivo::String)
```
Une las `columnas` deseadas de los `archivos` y el archivo es exportado a `nombre_archivo`.

```julia
unir(archivos::Array, columnas::Array, nombre_archivo::String, faltantes::Bool = false)
```
Une las `columnas` deseadas de los `archivos` y el archivo es exportado a `nombre_archivo`
los valores `faltantes` del archivo resultante seran ceros.

```julia
unir(carpeta::String, columnas::Array, nombre_archivo::String, faltantes::Bool = true)
```
Une las `columnas` deseadas de los archivos csv que esten en `carpeta`, el archivo sera exportado a `nombre_archivo`
 y los valores `faltantes` del archivo resultante seran missing de tipo Missing.

### Ejemplo 
>Supongamos que tenemos dos archivos csv, que contengan DataFrames
>
>`Archivo_1.csv`
```julia
4×2 DataFrame
 Row │ A        B      
     │ Float    String    
─────┼─────────────────
   1 │ 1        M      
   2 │ 2        F      
   3 │ 3        F      
   4 │ 4        M      
```
>`Archivo_2.csv`
```julia   
6×2 DataFrame
 Row │ C        D      
     │ Int      String    
─────┼─────────────────
   1 │ 1        Z      
   2 │ 2        Y      
   3 │ 3        X      
   4 │ 5        W      
   5 │ 8        V
   6 │ 13       U
```
>
>Entonces si usamos la función
```julia
Nuevo_DF = unir(["Archivo_1.csv", "Archivo_2.csv"], ["A", "C"], "NuevoCSV.csv")
```
>La función regresa un DataFrame y tambien crea un nuevo archivo de nombre NuevoCSV.csv que contiene la siguiente información 
```julia
6×3 DataFrame
 Row │ A        C   
     │ Any      Any    
─────┼──────────────
   1 │ 1        1
   2 │ 2        2
   3 │ 3        3
   4 │ 4        5
   5 │ missing  8
   6 │ missing  13    
```
>
### Licencia 

Este proyecto está bajo la Licencia MIT - mira el archivo [LICENSE.md](LICENSE.md) para detalle
