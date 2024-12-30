# TermoCPU
Simulador de termodinámica aplicada al enfriamiento de una CPU
# 
<span>![</span><span>Logo del Instituto Politécnico Nacional</span><span>]</span><span>(</span><span>https://raw.githubusercontent.com/Dav-Ort/TermoCPU/master/recursos/LogoIPN.png</span><span>)</span>
_La técnica al servicio de la patria_

Este proyecto fué realizado por el equipo de Física I para el Proyecto AULA para la materia Herramientas de Programación.

# Abstracto
El Sistema de Simulación de Refrigeración _TermoCPU_ es una aplicación de consola que simula el comportamiento térmico de un sistema de refrigeración líquida para CPU. La aplicación modela la interacción térmica entre dos componentes: la CPU y el líquido refrigerante (agua)

### Características Principales
- Simulación en tiempo real con actualizaciones cada segundo
- Monitoreo visual de temperaturas mediante barras de progreso
- Sistema de refrigeración activo/inactivo basado en umbrales
- Simulación de transferencia de calor entre componentes
- Sistema de alertas por temperaturas críticas
- Visualización en tiempo real mediante interfaz de consola

### Parámetros del Sistema

#### Temperaturas Iniciales
- CPU: 60.0°C
- Agua: 20.0°C

Si se desea jugar con la temperatura del CPU, se puede configurar en esta línea del código:

```csharp
static double tempCPU = 60.0;
```
Contenido en la línea 12

#### Umbrales y Límites
- Umbral de activación del refrigerante: 70.0°C
- Temperatura máxima de CPU: 90.0°C
- Temperatura mínima de CPU para desactivación: 30.0°C
- Ratio de calentamiento de CPU: 1.3°C/segundo

### Guía de Uso

#### Requisitos Previos
- .NET Framework 4.5 o superior
- Sistema operativo Windows/Linux/MacOS compatible
- Terminal con soporte para manipulación del cursor

#### Ejecución
1. Compile el programa usando el compilador de C#:
   ```bash
   csc Program.cs
   ```
2. Ejecute el programa resultante:
   ```bash
   ./Program.exe
   ```

#### Interpretación de la Interfaz
- La interfaz muestra tres barras de temperatura:
  - CPU: Rango de 30°C a 90°C, color rojo
  - Agua: Rango de 20°C a 80°C, color azul
- Las barras de progreso utilizan el siguiente formato:
  - `#`: Representa el grado de temperatura actual
  - `-`: Representa espacio hasta el máximo
  - Ejemplo: `[####----------------]`

### Comportamiento del Sistema

#### Sistema de Refrigeración
1. **Activación**: 
   - Se activa cuando la temperatura de la CPU alcanza 70°C
   - Comienza la transferencia de calor entre CPU y agua

2. **Proceso de Refrigeración**:
   - Transferencia de calor CPU → Agua: 2.6°C/segundo

3. **Desactivación**:
   - Se desactiva cuando la CPU alcanza 30°C
   - El sistema vuelve al estado de monitoreo

#### Mecanismos de Seguridad
- Prevención de temperaturas negativas
- Alerta de temperatura crítica al superar 90°C
- Finalización automática después de 50 iteraciones

### Limitaciones y Consideraciones
- La simulación está limitada a 50 iteraciones. Esto puede ser modificado cambiando el siguiente valor de la línea 22:
```csharp
static int maxIteraciones = 50;     //Número máximo de iteraciones
```
- Los valores de transferencia de calor son aproximaciones
- No se considera la influencia de factores externos como humedad, temperatura externa, y otros.
- La simulación no tiene en cuenta la carga de trabajo de la CPU, es un aproximado de trabajo regular de una CPU comercial regular.

### Personalización
Para modificar los parámetros de simulación, ajuste las siguientes variables:
```csharp
static double ratioCalentCPU = 1.3;      // Velocidad de calentamiento
static double umbralActRefrig = 70.0;     // Temperatura de activación
static double umbralMaxCPU = 90.0;        // Temperatura crítica
static double ratioMinCPU = 30.0;         // Temperatura de desactivación
```
La configuración de estos parámetros se encuentran a partir de la línea 15

### Finalización del Programa
- El programa se puede detener en cualquier momento presionando cualquier tecla. Si no, este se detendrá automáticamente
- Al finalizar, muestra un resumen del estado final del sistema
- Indica si la simulación terminó normalmente o con error por temperatura excesiva, según la temperatura configurada

### Recomendaciones de Uso
- Mantenga la ventana de terminal visible para observar la simulación en tiempo real
- No redimensione la ventana durante la ejecución para mantener la visualización correcta
