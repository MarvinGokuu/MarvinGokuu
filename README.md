# MARVIN DEV 🇸🇻

**Estudiante Autodidacta de Arquitectura de Sistemas (Kernel & Runtime de Alto Rendimiento)**  
*Java 25 · SIMD Vector API · Off-Heap · Concurrencia de baja latencia*

---

## Proyecto: Motor gráfico multiplataforma de bajo nivel (v1.0)

Desarrollo de un **kernel de infraestructura crítica** orientado a **alto rendimiento**, enfocado en:

- Acceso directo a memoria (off-heap)
- Procesamiento vectorizado (SIMD)
- Concurrencia sin bloqueos (wait-free / lock-free)
- Latencia mínima y alto throughput

El diseño prioriza el **uso eficiente de las capacidades reales del hardware**, reduciendo al mínimo el overhead del runtime.

---

## Métricas de rendimiento (2026)

| Componente              | Métrica        | Tecnología                                   | Aplicación |
|-------------------------|----------------|----------------------------------------------|------------|
| Acelerador de Datos     | 4.17 GB/s      | SIMD Vector API (256 bits, 8 carriles)       | Módulo de procesamiento |
| Bus Atómico             | ~1.52 ns       | Operaciones wait-free / VarHandle            | Sincronización |
| Throughput              | 650M ops/s     | Ring Buffer off-heap (Project Panama)        | Paso de mensajes |
| Seguridad de memoria    | Sin GC crítico | Off-heap controlado                          | Núcleo |
---

## Prueba: Throughput de memoria y cómputo (Acelerador de Datos)

| Aspecto medido      | Qué se está evaluando        | Detalle técnico |
|---------------------|------------------------------|-----------------|
| Inicialización      | Costes fuera de la medición  | Código caliente, sin warm-up incluido |
| Paralelismo         | Procesamiento vectorial      | SIMD 256 bits (8 × int32 por operación) |
| Memoria             | Acceso a RAM directa         | Off-heap, sin GC ni objetos |
| Patrón de acceso    | Eficiencia de caché          | Lectura secuencial, prefetch del CPU |
| Resultado           | Throughput efectivo          | 4.17 GB/s de lectura + cómputo |

