# Throw a Bird

## División en Tres Aves (Split)

Se asignó la tecla barra espaciadora en settings.py y se creó el método _split_bird() en PlayState.
Al presionarse, este método genera dos nuevas instancias de la clase Bird exactamente en la misma posición que el ave original.
Para la trayectoria, se calcula el ángulo actual del vector de velocidad y se le suma/resta una nueva constante SPLIT_ANGLE (15 grados) para disparar las dos nuevas aves hacia arriba y hacia abajo, manteniendo intacta al ave principal.
## Condición de Colisión

Se agregó un bool (self.can_split). el bool toma el valor True justo en el momento en que se suelta el ave de la honda.
En cada paso de físicas (fixed_update), el motor revisa si el ave está tocando algún otro cuerpo. Si choca con cualquier cosa que no sea la zona del aire, el bool toma valor False, bloqueando el uso del poder a partir de ese momento.
## Control del Marcador y Fin del Turno

Se modificó el método _update_idle(), que es el que decide cuándo se acaba el turno.
Ahora, en lugar de revisar solo la velocidad del ave principal, itera sobre todas las aves activas buscando la velocidad (lineal y angular) más alta. El contador de "fin de turno" solo avanza si absolutamente todas las aves están por debajo del umbral de reposo, si alguna se sigue moviendo, el turno continúa.
