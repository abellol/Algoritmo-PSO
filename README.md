# Algoritmo PSO
### Integrantes: 
| Nombre | ID |
|---|---|
| Alejandro Bello | 1013037759 |
| Malcolm Carrillo | 1010962608 |
| Rafael Chirivi | 1034661580 |

<details><summary>Get ready to see the great logo: </summary><p>
<div align='center'>
<figure> <img src="https://i.postimg.cc/NFbwf57S/logo-def.png" alt="Defensa Civil" width="400" height="auto"/></br>
<figcaption><b> "we are programmers, not designers" </b></figcaption></figure>
</div>
</p></details><br>

### Planteamiento del problema 
El PSO u optimización por enjambres de partículas, es un algoritmo y metaheurística que maximiza o minimiza funciones de "caja negra" lo que significa que aunque puntos pueden ser evaluados, no se conoce la expresión que la define: bajo este supuesto, optimizar la función consumiría una cantidad de recursos de tiempo y memoria importantes, sin embargo, lo que propone el algoritmo es realizar un "lanzamiento" de un selecto grupo de partículas que se espera encuentren la optimización deseada a partir de una posición aleatoria, para luego verse afectadas por una velocidad, inercia, aceleración, y dos variables que serán la mejor posición local, y la mejor posición global. Mientras mas lanzamientos se realizan, el enjambre tenderá a seguir una misma ruta en donde se ha encontrado una máximo o mínimo, y si bien al tratarse de un metaheurística no asegura una optimización global al estar atado a parámetros establecidos por el usuario y procedimientos propios del código, ofrece una alternativa útil para funciones "fitness" por los valles y colinas que presentan y por donde las partículas desarrollan sus trayectorias.

### Diagrama de clases
Acá presentamos la abstracción general de las clases que interactúan para darle forma al algortimo PSO, con sus respectivo métodos para poder obtener el resultado eserado según los parametros que se ingresen

```mermaid
classDiagram
    Enjambre o-- Particula
    Optimizacion <|-- Enjambre
    class Particula{
      -int cantidad_variables
      -float limiteSup
      -float limiteInf
      -float posicion
      -float velocidad
      -FuncionObjetivo
      -init()
      -evaluarParticula()
      -moverParticula()
      -actualizarParticula()
      -getFuncionObjetivo()
    }
    class Enjambre{
      -int cantidad_particulas
      -int cantidad_variables
      - float limiteSup
      -float limiteInf
      -list Particulas
      -_init_()
      -mostrarParticulas()
      -evaluarEnjambre()
      -moverEnjambre()
      -optimizar()
    }
    class Optimizacion{
      +verbose
      +list parametros
      +generarEnjambre()
      +reiterarOptimizacion()
      +_str_()
      +plot()
    }
```

### Diagrama de flujo
EL siguiente diagrama de flujo muestra el funcionamiento general del Algoritmo, incluyendo los procesos que se llevan a cabo con cada particula para llegar al resultado que se espera.

```mermaid
flowchart TD
    A[Inicio] --> B[Asignar posiciones y velocidades aleatorias iniciales]
    B --> C{Repetir}
    C --> D[Actualizar velocidad de cada partícula]
    D --> E[Actualizar posición de la partícula]
    E --> F[Calcular valor de fitness en la nueva posición]
    F --> G[Actualizar mejor personal de la partícula]
    G --> H[Actualizar mejor global del sistema]
    H --> I{¿Queda alguna partícula?}
    I -- Sí --> D
    I -- No --> J[Devolver el mejor global]
    J --> K[Fin]
```
### Alcance esperado
La optimización de funciones matemáticas complejas puede ser algo complejo, sin embargo, mediante este algortimo es posible estimar `maximos` y `minimos`.
Algunos [ejemplos](https://www.geogebra.org/m/wdcms7bu) de funciones que pueden ser tratadas con este algoritmo.
