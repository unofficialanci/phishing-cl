# phishing-cl 🇨🇱

Indicadores abiertos de **phishing contra usuarios y marcas de Chile**: bancos,
telcos, retail, pasarelas de pago y servicios básicos.

La idea es simple: muchas empresas no tienen un equipo de inteligencia y se
enteran del phishing con su marca cuando ya hay víctimas. Aquí se publica, lo
antes posible, lo que detectamos para que cualquiera pueda **bloquearlo,
reportarlo o avisar a sus clientes**.

👉 **[Últimas detecciones](ULTIMOS.md)**

## Estructura

```
phishing-cl/
├── ULTIMOS.md            últimas 50 detecciones, legibles (URLs desactivadas)
├── feeds/                todo junto, para cargar en tus herramientas
│   ├── activos.txt         solo dominios activos, uno por línea
│   ├── todos.csv           histórico completo
│   └── iocs.stix2.json     STIX 2.1 con indicadores y actores
├── marcas/               una carpeta por marca suplantada
│   └── <marca>/            README.md · activos.txt · iocs.csv
├── actores/              una carpeta por actor (UANCI-PH01, UANCI-PH02…)
│   └── <actor>/            README.md · activos.txt · iocs.csv
└── reportes/             informes puntuales (casos, olas de un actor)
```

### ¿Trabajas en una de las marcas?

Ve directo a **[`marcas/`](marcas/)** y sigue la carpeta de tu empresa: ahí
están solo tus dominios, con su propio `activos.txt` para bloquear.

### ¿Quieres entender quién está detrás?

En **[`actores/`](actores/)** cada actor tiene un código `UANCI-PHnn` (PH =
phishing), un nombre de ave chilena que resume cómo opera (**Tricahue**,
**Mirlo**…) y una ficha con cómo engaña a la víctima, qué marcas usa y cómo se
aloja. Un mismo actor suele suplantar varias marcas a la vez y va rotando:
seguirlo por actor permite anticipar la próxima marca.

## Feeds para integrar

| Fichero | Para qué |
|---|---|
| [`feeds/activos.txt`](feeds/activos.txt) | Dominios **activos**, uno por línea. Listo para DNS sinkhole, proxy o firewall. |
| [`feeds/todos.csv`](feeds/todos.csv) | Histórico completo con marca, actor, tipo, fechas y estado. |
| [`feeds/iocs.stix2.json`](feeds/iocs.stix2.json) | Bundle STIX 2.1 (indicadores + actores como *intrusion-set*) para MISP, OpenCTI y otras plataformas TI. |
| `marcas/<marca>/activos.txt` | Igual que el anterior, filtrado por marca. |
| `actores/<actor>/activos.txt` | Igual, filtrado por actor. |

Descarga directa:

```
https://raw.githubusercontent.com/unofficialanci/phishing-cl/main/feeds/activos.txt
https://raw.githubusercontent.com/unofficialanci/phishing-cl/main/marcas/bancoestado/activos.txt
```

### Campos de los CSV

| Campo | Contenido |
|---|---|
| `dominio`, `url` | Dónde está el phishing. |
| `ip` | **Contexto, no para bloquear.** Muchos sitios están en hosting compartido y bloquear la IP afectaría a terceros legítimos. |
| `marca` | Marca suplantada, normalizada (una por sitio). |
| `detalle_marca` | Matiz de la marca cuando aplica (p. ej. "Entel (paso de pago Webpay)"). |
| `actor` | Actor al que se atribuye (`UANCI-PHnn` o `sin-atribuir`; ver [`actores/`](actores/)). |
| `tipo` | Qué intenta robar: credenciales bancarias, tarjeta, segundo factor… |
| `primera_deteccion` | Cuándo lo vimos por primera vez. Vacío si no se conoce. |
| `estado` | `activo` o `caido` en el último export. |
| `publicado` | Cuándo se aprobó su publicación. |
| `nota` | Advertencias útiles, p. ej. *subdominio inyectado: NO bloquear el dominio raíz*. |

## Cómo se detecta

Monitoreo de Certificate Transparency y de buscadores de infraestructura, más
análisis del contenido. **Cada entrada la revisa una persona antes de
publicarse.** Los métodos concretos de detección no se publican a propósito:
los operadores también leen.

## Colabora

- ¿Viste un phishing contra una marca chilena? Abre un *issue* con la
  plantilla **Reportar phishing**.
- ¿Un dominio es tuyo y es legítimo, o ya está limpio? Usa la plantilla
  **Solicitar corrección** o lee [CORRECCIONES.md](CORRECCIONES.md). Los
  falsos positivos se retiran rápido.

## Uso y licencia

- Datos (`feeds/`, `marcas/`, `actores/`, `reportes/` y `ULTIMOS.md`) bajo
  **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es)** (texto
  completo en [`LICENSE`](LICENSE)): úsalos, incluso comercialmente, citando la
  fuente: *"phishing-cl (github.com/unofficialanci/phishing-cl)"*.
- Clasificación **TLP:CLEAR**: se pueden compartir sin restricciones.
- Se ofrecen "tal cual", sin garantía. Verifica antes de tomar acciones
  irreversibles.
- No se publican datos de víctimas.

## Reporta también aquí

Si encuentras un sitio, repórtalo donde bloquean en los navegadores:
[Google Safe Browsing](https://safebrowsing.google.com/safebrowsing/report_phish/),
[Netcraft](https://report.netcraft.com/report),
[PhishTank](https://phishtank.org/), y al
[CSIRT de Gobierno](https://www.csirt.gob.cl/).
