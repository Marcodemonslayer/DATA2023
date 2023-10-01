LABORATORIO 5
================
Marco Ocampo
2023-10-01

``` r
library(tidyverse)
library(readxl)
library(lubridate)
```

``` r
### PARTE 1: PREDICCION DEL ECLIPSE

ECLIPSE <- ymd_hms("2017-08-21 18:26:40")

ECLIPSE <- with_tz(ECLIPSE, tzone = "America/New_York")

print(ECLIPSE)
```

    ## [1] "2017-08-21 14:26:40 EDT"

``` r
Dias_SYNODIC <- 29*86400
Horas_SYNODIC <- 12*3600
Minutos_SYNODIC <- 44*60
Segundos_SYNODIC <- 3

SYNODIC <- Dias_SYNODIC+Horas_SYNODIC+Minutos_SYNODIC+Segundos_SYNODIC

SAROS <- 223

TOTAL <- ECLIPSE+(SAROS*SYNODIC)
print("El eclipse será en: ")
```

    ## [1] "El eclipse será en: "

``` r
print(TOTAL)
```

    ## [1] "2035-09-01 22:09:49 EDT"

``` r
### PARTE 3: SIGNO ZODIACAL

signo_zodiacal <- function(cumpleaños){
  
  fecha <- dmy(cumpleaños)
  mes <- month(cumpleaños)
  dia <- day(cumpleaños)
  
  if (mes==1){
    signo <- ifelse(test = dia<20,
                    yes = 'capricornio',
                    no = 'acuario')
  } else if(mes==2){
    signo <- ifelse(test = dia<19,
                    yes = 'acuario',
                    no = 'piscis')
  } else if(mes==3){
    signo <- ifelse(test = dia<21,
                    yes = 'piscis',
                    no = 'aries')
  } else if(mes==4){
    signo <- ifelse(test = dia<20,
                    yes = 'aries',
                    no = 'tauro')
  } else if(mes==5){
    signo <- ifelse(test = dia<21,
                    yes = 'tauro',
                    no = 'geminis')
  } else if(mes==6){
    signo <- ifelse(test = dia<21,
                    yes = 'geminis',
                    no = 'cancer')
  } else if(mes==7){
    signo <- ifelse(test = dia<23,
                    yes = 'cancer',
                    no = 'leo')
  } else if(mes==8){
    signo <- ifelse(test = dia<23,
                    yes = 'leo',
                    no = 'virgo')
  } else if(mes==9){
    signo <- ifelse(test = dia<23,
                    yes = 'virgo',
                    no = 'libra')
  } else if(mes==10){
    signo <- ifelse(test = dia<23,
                    yes = 'libra',
                    no = 'escorpio')
  } else if(mes==11){
    signo <- ifelse(test = dia<22,
                    yes = 'escorpio',
                    no = 'sagitario')
  } else if(mes==12){
    signo <- ifelse(test = dia<22,
                    yes = 'sagitario',
                    no = 'capricornio')
  }
  
  return(signo)
  
}
signo_zodiacal('07-08-2001')
```

    ## [1] "leo"

``` r
library(nycflights13)
Vuelos <- flights

Vuelos$dep_time2 <- format(strptime(sprintf('%04d', 
                                                flights$dep_time), 
                                        format = '%H%M'),
                               '%H:%M')
Vuelos$arr_time2 <- format(strptime(sprintf('%04d', 
                                                flights$arr_time), 
                                        format = '%H%M'),
                               '%H:%M')
Vuelos$sched_dep_time2 <- format(strptime(sprintf('%04d', 
                                                      flights$sched_dep_time), 
                                              format = '%H%M'),
                                     '%H:%M')
Vuelos$sched_arr_time2 <- format(strptime(sprintf('%04d', 
                                                      flights$sched_arr_time), 
                                              format = '%H%M'),
                                     '%H:%M')
Vuelos
```

    ## # A tibble: 336,776 × 23
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # ℹ 336,766 more rows
    ## # ℹ 15 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>, dep_time2 <chr>,
    ## #   arr_time2 <chr>, sched_dep_time2 <chr>, sched_arr_time2 <chr>
