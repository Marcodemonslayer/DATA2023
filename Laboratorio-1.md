Laboratorio 1
================
Marco Ocampo
2023-08-02

# Laboratorio 1

## Nombre: Marco Ocampo Sebastian

### Cargando librerías y archivos

    ## Warning: package 'tidyverse' was built under R version 4.3.1

    ## Warning: package 'readr' was built under R version 4.3.1

    ## Warning: package 'purrr' was built under R version 4.3.1

    ## Warning: package 'stringr' was built under R version 4.3.1

    ## Warning: package 'lubridate' was built under R version 4.3.1

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.2     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.2     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.1     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
    ## New names:

``` r
head(DATA)
```

    ## # A tibble: 6 × 10
    ##   COD_VIAJE CLIENTE   UBICACION CANTIDAD PILOTO     Q CREDITO UNIDAD   Año   Mes
    ##       <dbl> <chr>         <dbl>    <dbl> <chr>  <dbl>   <dbl> <chr>  <dbl> <dbl>
    ## 1  10000001 EL PINCH…     76002     1200 Ferna… 300        30 Camio…  2018     1
    ## 2  10000002 TAQUERIA…     76002     1433 Hecto… 358.       90 Camio…  2018     1
    ## 3  10000003 TIENDA L…     76002     1857 Pedro… 464.       60 Camio…  2018     1
    ## 4  10000004 TAQUERIA…     76002      339 Angel…  84.8      30 Panel   2018     1
    ## 5  10000005 CHICHARR…     76001     1644 Juan … 411        30 Camio…  2018     1
    ## 6  10000006 UBIQUO L…     76001     1827 Luis … 457.       30 Camio…  2018     1

``` r
print("El dataset completo tiene 2180 observaciones y 10 variables ya que elimine las columnas que no era consistentes con el resto y ademas tenían muchos NA values")
```

    ## [1] "El dataset completo tiene 2180 observaciones y 10 variables ya que elimine las columnas que no era consistentes con el resto y ademas tenían muchos NA values"

``` r
# Moda de las 3 variables solicitadas
print(moda_UBICACION)
```

    ## UBICACION 
    ##   "76002"

``` r
print(moda_Q)
```

    ##       Q 
    ## "281.5"

``` r
print(moda_CREDITO)
```

    ## CREDITO 
    ##    "30"

``` r
# Parque vehicular según SAT a diciembre del 2019

DATOS_SAT <- read_delim("INE_PARQUE_VEHICULAR_080120.txt", delim = "|")
```

    ## New names:
    ## • `` -> `...11`

    ## Warning: One or more parsing issues, call `problems()` on your data frame for details,
    ## e.g.:
    ##   dat <- vroom(...)
    ##   problems(dat)

    ## Rows: 2611540 Columns: 11
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: "|"
    ## chr (8): MES, NOMBRE_DEPARTAMENTO, NOMBRE_MUNICIPIO, MODELO_VEHICULO, LINEA_...
    ## dbl (2): ANIO_ALZA, CANTIDAD
    ## lgl (1): ...11
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
head(DATOS_SAT)
```

    ## # A tibble: 6 × 11
    ##   ANIO_ALZA MES   NOMBRE_DEPARTAMENTO NOMBRE_MUNICIPIO MODELO_VEHICULO
    ##       <dbl> <chr> <chr>               <chr>            <chr>          
    ## 1      2007 05    EL PROGRESO         "EL JICARO"      2007           
    ## 2      2007 05    ESCUINTLA           "SAN JOS\xc9"    2006           
    ## 3      2007 05    JUTIAPA             "MOYUTA"         2007           
    ## 4      2007 05    GUATEMALA           "FRAIJANES"      1997           
    ## 5      2007 05    QUETZALTENANGO      "QUETZALTENANGO" 2007           
    ## 6      2007 05    HUEHUETENANGO       "CUILCO"         1999           
    ## # ℹ 6 more variables: LINEA_VEHICULO <chr>, TIPO_VEHICULO <chr>,
    ## #   USO_VEHICULO <chr>, MARCA_VEHICULO <chr>, CANTIDAD <dbl>, ...11 <lgl>
