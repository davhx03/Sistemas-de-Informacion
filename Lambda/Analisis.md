# Funciones Lambda: ¿Qué son y cómo funciona esta tecnología?

Este video ofrece una explicación completa sobre **funciones Lambda**, características, casos de uso y una demostración práctica utilizando Amazon Web Services (AWS). El video resalta la importancia de las funciones lambda y se introduce el concepto de **"serverless" (sin servidores)**, aclarando que esto no implica la ausencia de servidores, sino que el desarrollador se libera de la responsabilidad de administrarlos, configurarlos o mantenerlos. Por ejemplo, Amazon provee **"containers" (paquetes de software aislados)** que se encargan de ejecutar el código, permitiendo al desarrollador centrarse exclusively en la lógica de la aplicación.

---

## Ventajas Clave y Casos de Uso

Una de las ventajas clave de Lambda es su **modelo de escalabilidad y costos**. La plataforma aprovisiona y escala los recursos automáticamente bajo demanda; a más requerimientos, más containers se despliegan. También existe un modelo de pago, el cual es estrictamente **por consumo**, basado en la cantidad de memoria utilizada durante la ejecución y el número total de veces que la función es invocada. En este orden de ideas, se da una alta rentabilidad de esta tecnología, ejemplificando cómo miles de ejecuciones pueden costar apenas centavos.

Se dan también algunos **casos de uso ideales** para Lambda:
* Integración con APIs de terceros.
* Procesamiento de archivos (reducción de imágenes, transcodificación de videos).
* Streaming de datos en tiempo real.

---

## Concepto Central y Ciclo de Vida

Profundizando un poco más en el concepto de lambda, se menciona que es la **unidad básica de la lógica** y una acción específica de negocios o la lógica funcional. Esta tiene un **tiempo máximo de ejecución** de hasta 15 minutos. En caso de necesitar procesar data o realizar procesos que requieran más tiempo, lo ideal es dividir en lotes para dividir la carga de trabajo.

El **ciclo de vida** de una función comienza con un "evento de activación" (como una petición HTTP o una tarea programada), que provoca que Amazon:
1.  Cree un container.
2.  Cargue el código.
3.  Lo ejecute.
4.  Al finalizar, deseche dicho container.

---

## Características Avanzadas y Recomendaciones

El video también presenta características de orquestación más avanzadas, como el **"reúso de containers"**. Si un nuevo evento llega poco después de una ejecución, Amazon puede reutilizar el container existente para mejorar el rendimiento. Si los eventos llegan de forma **concurrente**, Lambda simplemente inicializa nuevos containers para manejarlos en paralelo.

Se hace una recomendación crítica sobre la **"idempotencia"**: dado que Amazon garantiza la ejecución "al menos una vez" (pero no "exactamente una vez"), las funciones deberían diseñarse para que, si se ejecutan múltiples veces por error, no generen resultados indebidos, como un doble cobro en una transacción.

---

## Práctica
- Link: https://rm9pu11rz6.execute-api.us-east-2.amazonaws.com/default/Prueba_sisinfo
Code:
```
import json

def lambda_handler(event, context):
# TODO implement
return {
        'statusCode': 200,
        'body': json.dumps('Prueba Sisinfo :-)')
    }
```
