
# analisis de reto camilo valencia

ANÁLISIS DESARROLLO DE LA FASE 1
 
En esta primera fase se llevó a cabo el siguiente trabajo
•	Entradas, Procesos, salidas del reto, donde se sacaron los siguientes datos:

(Entradas):

 La presión atmosférica actual en (⁠presion_hpa⁠), que ingresa como un número decimal de tipo ⁠float⁠.
 La aceleración actual del cohete en metros sobre segundo al cuadrado (⁠aceleración⁠), que se maneja como un número decimal de tipo ⁠float⁠.
 La temperatura actual registrada en grados Celsius (⁠temp_celsius⁠), ingresada también como un número decimal de tipo ⁠float⁠.
 El contador discreto de segundos que van pasando (⁠tiempo⁠), que funciona como un número entero⁠.

 (Procesos):

 Cálculo de la altura: Transforma la presión que marcan los sensores en metros de altitud usando la fórmula barométrica.
 Detección de apogeo: Usa una variable para ir guardando la altitud anterior y ver el momento exacto en que empieza a bajar (⁠altitud_actual < altitud_previa⁠), detectando así el punto máximo sin necesidad de guardar un montón de datos en una lista.
 Estadísticas al vuelo: Va sumando las temperaturas y contando las muestras para sacar el promedio al final, además de registrar la aceleración más alta.
 Control de alertas: Revisa si la temperatura del motor o la estructura se sale de lo seguro.
 Fases del vuelo: Clasifica en qué momento estamos (si vamos subiendo, si ya pasamos el apogeo/caída libre, o si toca desplegar el paracaídas).

 (Salidas):

 Un reporte en la consola por cada segundo con el tiempo, la altitud, el estado del vuelo, la aceleración y la temperatura.
 Mensajes de advertencia inmediatos si la temperatura se pasa de los límites.
 Un resumen final cuando termina la simulación que muestra la altitud máxima (apogeo), la aceleración máxima y la temperatura promedio.

•	Diagrama de flujo del ejercicio
Adjunto el diagrama de flujos hecho en draw.io
#diagrama de flujo

 
•	Seudocódigo de las funciones

// Cálculo de altitud integrado en el flujo principal o por asignación directa
Si presión <= 0 Entonces
    altitud_actual <- 0.0
Sino
    altitud_actual <- 44330.0 * (1.0 - (presión / 1013.25) ^ 0.1903)
FinSi
// Detección de apogeo
Si tiempo > 0 Y NO apogeo_detectado Entonces
    Si altitud_actual < altitud_previa Entonces
        apogeo_detectado <- Verdadero
    FinSi
FinSi
// Evaluación de temperatura y alertas
Si temperatura > 85.0 O temperatura < -20.0 Entonces
    Escribir "¡ALARMA: ¡Temperatura fuera de rango seguro!"
Sino
    Escribir "Temperatura normal"
FinSi



