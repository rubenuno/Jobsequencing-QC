# Resolviendo el modelo de Ising y el problema de "Job Sequencing with Integer Lengths" con un ordenador de D-Wave
Vamos a utilizar un ordenador cuántico de D-Wave para resolver casos del modelo de Ising que se corresponden con instancias del problema del *Job Sequencing with Integer Lengths*. 

El problema a resolver se define como: Tenemos una lista de N trabajos para m clusters de computadores. Cada trabajo i tiene una longitud Li. Ademas, cada trabajo puede ser asignado a un computador de un cluster tal que, si cada grupo de trabajos en el cluster α es Vα, por tanto, la longitud de cada cluster se define como: 

<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/rubenuno/Jobsequencing-QC/master/images/image1.png">
</p>

son elegidos tal que el max(Mα) esta minimizado? Basicamente, esto significa que si ejecutamos todos los trabajos simultaneamente, todos los trabajos habrán terminado de ejecutarse en el menor tiempo posible. Esto es un problema NP-hard y hay una version (es max(Mα)≤M0?) que es NP-completa. Asumimos que Li∈ℕ. Para conseguir esto, empezaremos exigiendo que sin perdida de generalidad, M1≥Mα para cualquier valor de α, introducimos las variables xi,α que sera 1 si el trabajo i es añadido al computador α, y 0 en caso contrario, y las variables yn,α para α≠1 y n≥0, que es 1 si la diferencia M1−Mα=n. Por tanto, el hamiltoniano

<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/rubenuno/Jobsequencing-QC/master/images/image2.png">
</p>

se encarga de que cada trabajo se asigne unicamente a un computador, y que ningun computador pueda tener una longitud mayor que el computador 1. El usuario debe elegir el numero M, y esta relacionado con la cantidad de giros (spins) auxiliares necesario para imponer adecuadamente las limitaciones de longitud que M1≥Mα: en el peor de los casos, viene dado por Nmax(Li). Para encontrar la longitud maxima minimizada M1, usaremos: 

<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/rubenuno/Jobsequencing-QC/master/images/image3.png">
</p>

. De manera similar a encontrar los limites A/B en el problema de la mochila, para que este hamiltoniano encuentre la solucion al problema, necesitamos, en el peor de los casos 0<Bmax(Li)<A. Y usando el truco logaritmico, el numero de giros (spins) requeridos sera mN+(m−1)[1+logM].