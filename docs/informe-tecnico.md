Informe técnico - Caracterización del modelo local

1. Información del entorno

| Dato | Valor |
|---|---|
| Perfil de hardware | Perfil B (8 GB) |
| RAM total del equipo | 7,0 GiB |
| Modelo y etiqueta | qwen2.5:0.5b |
| Tamaño en disco | 397 MB |

2. Latencia del modelo

Se realizaron cinco ejecuciones utilizando la API REST de Ollama con el siguiente prompt:

> Responde solo con una palabra: hola

Los tiempos obtenidos fueron:

| Ejecución | Latencia |
|---|---:|
| 1 | 3133 ms |
| 2 | 2733 ms |
| 3 | 2230 ms |
| 4 | 2357 ms |
| 5 | 2191 ms |

Latencia promedio

La latencia promedio de las cinco ejecuciones fue de:

2529 ms (2,53 segundos)

3. Consumo de memoria

Durante la inferencia, el comando `free -h` mostró:

RAM utilizada: 4,2 GiB

La memoria total disponible en el equipo es de 7,0 GiB.

4. Calidad percibida

Calificación: 2/5
El modelo genera respuestas coherentes para consultas simples, pero presenta dificultades para seguir instrucciones específicas de formato, como responder únicamente con una palabra. Durante las pruebas, ante la instrucción de responder solo con una palabra, en algunas ocasiones generó respuestas más extensas de lo solicitado.

5. Conclusión

El modelo `qwen2.5:0.5b` puede ejecutarse localmente en el equipo utilizando una cantidad moderada de memoria y presenta tiempos de respuesta adecuados para tareas sencillas. Sin embargo, debido a su reducido tamaño, presenta limitaciones en el seguimiento preciso de instrucciones y en la calidad de las respuestas.
