# Auditoría ASG y Refactorización Sostenible
## Fase 1: Inventario y Dimensión Ambiental (A)
### 1. Medición inicial. Utiliza herramientas gratuitas como Website Carbon Calculator o Lighthouse (pestaña de rendimiento en Chrome/Edge) para obtener la huella de carbono estimada por visita.
   Realize una auditoria con esas herramientas y algunas de los resultados son:
   
  |Medicion | Resultado |
| :--- | :--- |
| Peso total de la pagina | 6 MB |
| Peticiones HTTP | +110 |
| Tiempo de carga inicial | 4,8 s |
| Rendimiento Lighthouse | 72/100 |
| Accesibilidad Lighthouse | 72/100 |
| Huella estimada por visita | 1,1 g CO2 |

Con estos valores la web presenta un consumo muy superior para una pagina de comercio sencilla. Su peso total es elevado debido a:

* Imagenes de alta resolucion sin optimizar

* Scripts externos

* Recursos visuales

* Carga simultanea de multiples productos en la pagina principal

### 2. Identificación de Bloatware. Inspecciona la red (Network) en las herramientas de desarrollador del navegador. Identifica los 3 recursos más pesados que se descargan al abrir la web (imágenes sin comprimir, vídeos de fondo, librerías JavaScript pesadas, etc.).

  Tras analizar la web con la pestaña de Red de Chrome encontre recursos especialmente pesados que son:
   
  |Recurso | Problema detectado |
| :--- | :--- |
| Imagenes JPG de productos | No utilizan formatos modernos como WebP o AVIF |
| Carrusel Principal | Carga imagenes grandes incluso fuera de pantalla |
| Scripts JavaScript externos | Hay librerias cargadas y no siempre se usan |

Tambien encontre varias evidencias:

* Varias imagenes superan los 300 KB

* El carrusel principal descarga multiples banners al iniciar

* Existen peticiones bloqueantes de renderizado

* Se cargan elementos antes de ser necesario

