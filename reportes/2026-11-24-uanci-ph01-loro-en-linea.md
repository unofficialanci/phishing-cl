# Campaña «Loro en Línea»: un operador que te acompaña mientras te roba

**Actor:** UANCI-PH01 · Tricahue

**TLP:CLEAR** · CC BY 4.0 · Publicado: 2026-11-24 · Ficha del actor: [`actores/UANCI-PH01`](../actores/UANCI-PH01/)

**Por qué «Loro en Línea»:** el tricahue es un loro bullicioso que "habla". En esta campaña hay una persona al otro lado que conversa con la víctima mientras está en línea y la guía, pantalla por pantalla, hasta sacarle la clave y el segundo factor.

## Resumen

- **Tricahue roba tarjetas, claves de banca en línea y códigos de segundo factor** (SMS, BE Pass, coordenadas, clave dinámica) a usuarios chilenos.
- **No es un sitio automático: hay un operador humano en vivo.** Ve lo que la víctima hace en tiempo real y le envía pantallas ("clave incorrecta", "ingresa el código que te llegó") hasta tener lo necesario para usar el código antes de que venza.
- **Ha cambiado de señuelo al menos dos veces:** tiendas falsas de suplementos en redes sociales (desde marzo de 2026, y siguen activas) y ofertas o renovaciones falsas de Entel, Movistar y WOM (desde julio de 2026). Las dos terminan en una página de pago falsa con selector de bancos.
- **Se le conocen 68 sitios desde marzo de 2026**, casi todos en dominios desechables que rota cada pocos días. **63 están publicados** en este repositorio. Unos pocos quedan fuera a propósito, porque podrían afectar a terceros.
- **Origen probable:** Chile (operador local), confianza alta. **Zona de operación:** indicios de actividad desde la Región del Biobío, confianza media.

## Cómo engaña a la víctima

**1. El enganche** (ha ido rotando):

- **Tiendas falsas de suplementos deportivos** (proteínas, creatina) promocionadas en TikTok e Instagram con precios "de mayorista". El carrito ofrece dos formas de pago:
  - **Transferencia** a cuentas de terceros, con un temporizador de "stock reservado" para meter prisa.
  - **Tarjeta**, que lleva a una página de pago falsa (ver el paso 2).
- **Telcos falsas** (Entel, Movistar, WOM): renovación de equipo, oferta o recarga. El sitio imita un proceso de compra completo: eliges el teléfono y el plan, ingresas tu RUT, correo y dirección, y eliges la fecha de entrega. Así el sitio parece legítimo y, de paso, se queda con tus datos personales.
- **Otras marcas, de forma puntual:** un portal de empleos y una empresa de envíos.

**2. El pago falso.** Al pagar, la víctima llega a una página que imita una pasarela de pago o el pago **Compraquí de BancoEstado**, con un selector para "elegir tu banco": BancoEstado, Banco de Chile, Santander, BCI, Falabella, Itaú, Ripley, Scotiabank y otros. Cada banco tiene su propia copia de la página de ingreso y de la pantalla del segundo factor.

**3. El operador en vivo.** Desde aquí actúa una persona:
- Recibe al instante lo que la víctima escribe y ve su pantalla.
- La deja en una sala de espera ("Estamos procesando tu pago") mientras usa los datos en el banco real.
- Le envía la pantalla que necesite en cada momento: "clave incorrecta, inténtalo de nuevo", "ingresa el código que te enviamos", la tarjeta de coordenadas o la clave dinámica.
- Puede abrir un chat falso de soporte para calmarla si duda.

Cuando la víctima termina, el operador ya usó el código para entrar a su banca, hacer transferencias o agregar la tarjeta a otro medio de pago.

## Cómo monta la infraestructura

- **Dominios desechables** baratos (`.online`, `.shop`, `.store`, `.site`, `.live`) y algunos `.cl` parecidos a marcas de pago, casi todos en **hosting compartido**. A veces aloja el kit en sitios WordPress legítimos que compromete.
- **Nombres en familias.** Repite el mismo nombre con variaciones cuando le bajan un sitio:
  - pago de BancoEstado: `compre-aqui`, `compreme-aqui`, `compraraqui`, `comprameaqui`, `aquicompre`, `compraqui-web`…
  - telcos: `renueva-<telco>`, `equipo-<telco>`, `portal-<telco>`, `mundo-<telco>`, `promocion-<telco>`…
  - pasarelas genéricas: `tu-portal`, `tu-metodo`, `tu-comercio`, `comercio-online`…
- **Dos etapas.** El sitio de la telco y el de pago son dominios distintos, pero suelen compartir servidor y registrador, y caen juntos.
- **Rotación rápida.** Cada sitio dura entre días y pocas semanas. El actor tiene dominios de reserva y vuelve con otro nombre de la misma familia.

## Cronología

| Fecha | Qué pasó |
|---|---|
| **Marzo 2026** | Primeras páginas de pago falsas con selector de bancos, incluido un clon de **Compraquí**. |
| **Marzo-octubre 2026** | Tiendas falsas de suplementos en redes sociales (al menos diez tiendas distintas), con cobro por transferencia o por la página de pago falsa. |
| **Junio 2026** | Ola de pasarelas de pago falsas y clones de Compraquí en dominios desechables. |
| **Julio 2026** | Aparece el señuelo de telcos: renovaciones falsas de Movistar y pasarelas genéricas (`tu-portal`, `tu-metodo`, `comercio-online`). |
| **Agosto 2026** | Renovación de equipos Entel, más clones de Compraquí (`compra-qui`, `compraraqui`, `comprar-aqui`) y ofertas de Movistar en dominios `.cl`. |
| **Septiembre 2026** | Más clones de Compraquí y de equipos Entel y Movistar; recargas falsas de WOM; un clon de pago para Banco de Chile. |
| **Octubre 2026** | `mundo-entel` y una nueva tienda falsa de suplementos, `suplestoop.cl`. |
| **4-21 nov 2026** | Nueva ola de clones de Compraquí (`compremeaqui`, `aquicompre`, `comprameaqui`, `compraraqui`) y `portal-entel`. |
| **14-24 nov 2026** | La tienda `suplestoop.cl` se reconstruye con un checkout de pago falso propio y precios muy por debajo del mercado. |
| **24 nov 2026** | 4 sitios activos: `compraraqui.shop`, `portal-entel.online`, `recargas-wom.online` y la tienda `suplestoop.cl`. |

## Marcas suplantadas

| Marca | Sitios | Qué hace el sitio falso |
|---|---|---|
| [BancoEstado](../marcas/bancoestado/) | 19 | Pago Compraquí falso: clave, tarjeta y segundo factor |
| Pasarelas de pago genéricas | 19 | Página de pago falsa con selector de bancos |
| [Movistar](../marcas/movistar/) | 11 | Renovación u oferta falsa de equipo |
| [Entel](../marcas/entel/) | 6 | Renovación falsa de equipo |
| [Tiendas falsas](../marcas/tiendas-falsas/) | 6 | Tienda de suplementos que cobra por transferencia o con un pago falso |
| [Banco de Chile](../marcas/banco-de-chile/) | 1 | Clave y segundo factor |
| [WOM](../marcas/wom/) | 1 | Recarga falsa |

Las páginas de pago incluyen copias de casi todos los bancos chilenos. En la tabla figura solo la marca principal de cada sitio.

## Cómo reconocerlo

- **Un pago que te pide la clave de tu banco y además un código** (SMS, BE Pass, coordenadas) para una compra común es una señal grave. Si después te dice "clave incorrecta" y te pide repetirla o te pide otro código, **detente: hay alguien del otro lado.**
- **"Estamos procesando tu pago" que no termina nunca** mientras te piden más datos es la sala de espera del operador.
- **Tiendas que solo existen en redes sociales**, con precios muy bajos, que piden transferir a la cuenta de un tercero o te ponen una cuenta regresiva para pagar.
- **Renovaciones de equipo o recargas que llegan por un anuncio o un enlace.** Entra tú mismo al sitio o la app de tu compañía.
- **Mira el dominio completo.** `compraraqui.shop` o `portal-entel.online` no son de BancoEstado ni de Entel.

## Recomendaciones

**Si ingresaste tus datos:** llama de inmediato a tu banco para bloquear la tarjeta y la clave, y revisa si agregaron un dispositivo, una tarjeta a otra billetera o destinatarios de transferencia nuevos. Cambia la clave desde el sitio oficial, guarda capturas y la dirección del sitio, y haz la denuncia (PDI Cibercrimen o Fiscalía).

**Equipos de seguridad y proveedores de DNS o proxy:**
- Carguen [`actores/UANCI-PH01/activos.txt`](../actores/UANCI-PH01/activos.txt) o el feed general [`feeds/activos.txt`](../feeds/activos.txt).
- **Bloqueen el dominio, nunca la IP:** casi todo está en hosting compartido con sitios legítimos.
- Vigilen las familias de nombres de arriba: la próxima variante suele ser otra combinación de las mismas palabras.

**Bancos y telcos suplantados:** avisen a sus clientes que no venden equipos ni cobran por enlaces de anuncios, y que ningún pago normal pide la clave de la banca más un código. Las carpetas de [`marcas/`](../marcas/) tienen los dominios de cada una.

**Plataformas y redes sociales:** las tiendas falsas se promocionan con perfiles y anuncios pagados. Un perfil "mayorista" nuevo, que solo acepta transferencia y con precios muy por debajo del mercado, merece revisión.

## Atribución y confianza

- **Alta:** los sitios de telcos y los de pago (Compraquí, pasarelas falsas, bancos) usan el mismo kit con operador en vivo, se enlazan entre sí (la telco deriva al pago) y comparten registrador y hosting.
- **Media-alta:** la fase de tiendas falsas de suplementos se liga a la de telcos por la misma página de pago con selector de bancos y el mismo modo de operar con un operador en vivo.
- **Origen:** Chile, confianza alta. **Zona:** Región del Biobío, confianza media. No publicamos el detalle de esa evaluación.
- No hay relación conocida con [UANCI-PH02 · Mirlo](../actores/UANCI-PH02/): opera, aloja y cobra de otra forma.

## Qué no publicamos

A propósito, este informe no incluye:
- las firmas técnicas con que detectamos el kit, porque los operadores también leen;
- nombres de personas o empresas, cuentas que reciben transferencias, perfiles de redes sociales ni números de contacto;
- las fuentes de la evaluación geográfica;
- datos de víctimas;
- unos pocos dominios que podrían afectar a terceros (por ejemplo, porque llevan el nombre de una empresa).

Si eres una institución afectada o investigas el caso, escríbenos por un *issue* y coordinamos el canal.

## IoC

- Sitios de este actor: [`actores/UANCI-PH01/iocs.csv`](../actores/UANCI-PH01/iocs.csv)
- Solo activos: [`actores/UANCI-PH01/activos.txt`](../actores/UANCI-PH01/activos.txt)
- STIX 2.1 (actor como *intrusion-set*): [`feeds/iocs.stix2.json`](../feeds/iocs.stix2.json)
