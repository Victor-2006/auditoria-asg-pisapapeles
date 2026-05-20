# Auditoría ASG y Refactorización Sostenible
**Web auditada:** https://www.pisapapeles.es/
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

### Captura Lighthouse
<img width="1919" height="945" alt="image" src="https://github.com/user-attachments/assets/11ad0371-d677-49be-a89f-71edea913395" />

### Captura Website Carbon
<img width="1917" height="942" alt="image" src="https://github.com/user-attachments/assets/7c2429d1-6f27-45af-ac29-2c621bfe427e" />

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

### Captura Network
<img width="1919" height="943" alt="image" src="https://github.com/user-attachments/assets/843e16bd-4851-441b-9c54-fe27013e1bd7" />

Tambien encontre varias evidencias:

* Varias imagenes superan los 300 KB

* El carrusel principal descarga multiples banners al iniciar

* Existen peticiones bloqueantes de renderizado

* Se cargan elementos antes de ser necesario

# FASE 2: Dimensión Social y Equidad (S)

## 2.1 Test de accesibilidad

Se utilizó Lighthouse para analizar accesibilidad

| Indicador | Resultado |
|---|---|
| Accesibilidad | 72/100 |
| Contraste | Mejorable |
| Navegación teclado | Parcial |


## 2.2 Identificación de barreras

### Problema 1: imágenes sin atributos ALT

### Problema detectado:

Algunas imágenes carecen de descripción.

### Impacto:

Los lectores de pantalla no pueden interpretar el contenido.

### Ejemplo:
En este ejemplo el juego ITS BANANAS no tiene una alt correcta
<img width="1919" height="942" alt="Captura de pantalla 2026-05-20 132318" src="https://github.com/user-attachments/assets/6d61a3b9-1295-4ce6-be77-a78ca73fdeb4" />

### Solución:
Yo por lo menos pondria el nombre del juego de mesa
<img width="1919" height="989" alt="Captura de pantalla 2026-05-20 132543" src="https://github.com/user-attachments/assets/ab15db96-1722-4bb7-8b62-33abefe46ada" />

### Problema 2: bajo contraste

### Problema:

Texto con colores poco visibles.

### Impacto:

Dificulta la lectura a personas con baja visión.

### Solución:

- Mejorar colores
- Cumplir WCAG AA
- Ratio mínimo 4.5:1
