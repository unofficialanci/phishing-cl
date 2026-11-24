# Campaña «Nido Ajeno»: deudas falsas sobre subdominios ajenos

**Actor:** UANCI-PH02 · Mirlo

**TLP:CLEAR** · CC BY 4.0 · Publicado: 2026-11-24 · Ficha del actor: [`actores/UANCI-PH02`](../actores/UANCI-PH02/)

**Por qué «Nido Ajeno»:** el mirlo chileno pone sus huevos en nidos de otras aves para que se los críen. Esta campaña hace lo mismo con los dominios: se instala en zonas DNS de empresas que no tienen nada que ver y vive de su reputación.

## Resumen

- **Mirlo** cobra **deudas que no existen** (telefonía, peajes TAG, electricidad, gas) y vende **promociones falsas** (viajes, puntos, supermercado) a usuarios chilenos.
- **La víctima paga de verdad.** Paga en una pasarela de pago real, pero el cobro va a una cuenta del operador y no a la empresa que cree estar pagando. No hay robo visible de la tarjeta, así que muchas víctimas no notan el fraude hasta que reclaman la "deuda" o revisan el comprobante.
- **Monta sus sitios en subdominios inyectados** en zonas DNS de pequeñas empresas, casi todas mexicanas, que no tienen relación con él ni saben que las usa.
- **Está activo al menos desde mayo de 2026.** Hasta hoy suma **41 sitios publicados** en este repositorio, sobre **más de 25 dominios de terceros** y **9 marcas chilenas**.
- **Rota rápido.** Cada sitio dura pocos días y, cuando le bajan un servidor, monta la infraestructura de nuevo en **menos de 12 horas**.

## Cómo engaña a la víctima

**Deuda falsa** (Telsur/GTD, TAG Total, CGE, Metrogas):

1. La víctima llega a una página de "Pago de cuentas" o "Sucursal virtual" que copia la de la empresa, casi siempre desde un enlace por SMS, correo o un anuncio.
2. Ingresa su RUT. Cualquier RUT devuelve al instante una "deuda" pendiente, con un documento fechado el mismo día.
3. Al pagar, el sitio genera en segundo plano un cobro por ese monto en una cuenta del operador y lleva a la víctima a una pasarela de pago real para pagarlo. Lo más común es Webpay, pero también se han visto casos con MercadoPago.
4. El pago se procesa normalmente, pero **a nombre de un comercio o una cuenta que no es la empresa suplantada**.

**Promociones falsas** (Falabella, Cencosud, Líder): el mismo esquema, con viajes, canje de puntos u ofertas en lugar de una deuda.

**Banca falsa** (desde noviembre de 2026, BancoEstado): páginas que roban RUT, clave, teléfono y tarjeta, enlazadas desde sus sitios de deuda falsa. Un operador las revisa en tiempo real. Es una variante del mismo actor, con otro kit.

## Cómo monta la infraestructura

- **Subdominios inyectados en zonas ajenas.** El actor agrega registros DNS a dominios legítimos de pymes (por ejemplo `pagos.<marca>.cl.<dominio-de-una-pyme>.com.mx`). No toca el sitio web, el correo ni el dominio raíz; solo agrega el subdominio y lo apunta a su servidor. **El dueño del dominio también es víctima.**
- **Un proveedor común.** Casi todas las zonas afectadas están alojadas en un mismo proveedor mexicano de hosting y DNS, repartidas en muchos servidores distintos. Lo más probable es que el acceso venga de credenciales del panel de hosting robadas a los clientes (por ejemplo, con malware *infostealer*) o de una falla en ese proveedor.
- **Servidores propios de bajo costo.** Los subdominios apuntan a VPS que el actor arrienda y cambia con frecuencia. Algunas zonas se reutilizan durante semanas o meses, y a veces deja subdominios listos días antes de usarlos.
- **Nombres con la marca como prefijo**, a menudo con errores de tipeo (`telsur` → `teslur`, `tutslur`; `cencosud` → `cenosud`). Ese patrón sirve para reconocerlos (ver más abajo).

## Cronología

| Fecha | Qué pasó |
|---|---|
| **Mayo-junio 2026** | Primera fase conocida: subdominios de Telsur, CGE, Vespucio Sur, Banco Ripley, Hites, Tarjeta Cencosud y Tarjeta ABC en una misma zona mexicana. Cada sitio vive entre 3 y 6 días. |
| **Agosto-octubre 2026** | Aparece TAG Total (peajes de autopistas) con el mismo backend de cobro, y Falabella y Cencosud con promociones falsas. El actor cambia de proveedor de servidores. |
| **5-10 nov 2026** | Ola de Telsur/GTD en varias zonas nuevas, con rotación casi diaria. |
| **11-12 nov 2026** | Cae su servidor principal; en menos de 12 horas el kit reaparece en otra zona y otro servidor. |
| **12-18 nov 2026** | Nueva ola de TAG Total y Telsur, y clones de Metrogas ("Sucursal virtual"). |
| **21 nov 2026** | Variante de banca falsa de BancoEstado, enlazada desde un sitio de Telsur. |
| **24 nov 2026** | 2 sitios activos (TAG Total y BancoEstado). Se siguen vigilando sus servidores y las zonas que ya usó. |

## Marcas suplantadas

| Marca | Sitios | Qué ofrece el sitio falso |
|---|---|---|
| [Telsur (GTD)](../marcas/telsur/) | 17 | Pago de deuda falsa |
| [TAG Total (Unired)](../marcas/tag-total/) | 9 | Pago de deuda de peajes falsa |
| [Falabella](../marcas/falabella/) | 6 | Viajes y promociones falsas |
| [Metrogas](../marcas/metrogas/) | 3 | Pago de deuda falsa |
| [Banco Santander](../marcas/santander/) | 2 | Credenciales bancarias |
| [BancoEstado](../marcas/bancoestado/) | 1 | Clave y tarjeta |
| [Cencosud](../marcas/cencosud/) | 1 | Canje de puntos falso |
| [CGE](../marcas/cge/) | 1 | Pago de deuda falsa |
| [Líder](../marcas/lider/) | 1 | Promoción falsa |

Las marcas de la primera fase (Vespucio Sur, Banco Ripley, Hites y Tarjeta ABC) no tienen sitios en el feed porque ya no resuelven y no se pudo capturar su contenido.

## Cómo reconocerlo

- **Mira el final de la dirección, no el principio.** En `pagos.telsur.cl.ejemplo.com.mx`, el sitio real es `ejemplo.com.mx`: el `telsur.cl` del comienzo es solo decoración.
- **Una deuda que aparece con cualquier RUT es falsa.** Las empresas no muestran deudas a quien no se identifica.
- **Revisa a quién le pagas.** En la pasarela de pago y en el comprobante figura quién recibe el dinero (el comercio o el vendedor que cobra). Si no es la empresa que crees estar pagando, detente.
- **Paga siempre desde el sitio o la app oficial**, escribiendo tú la dirección, nunca desde un enlace recibido.

## Recomendaciones

**Si pagaste en uno de estos sitios:** llama a tu banco para desconocer el cargo y pedir el bloqueo de la tarjeta; si pagaste por MercadoPago, reclama también ahí desde el detalle de la compra. Guarda el comprobante y la dirección del sitio, y haz la denuncia (PDI Cibercrimen o Fiscalía).

**Equipos de seguridad y proveedores de DNS o proxy:**
- Carguen [`actores/UANCI-PH02/activos.txt`](../actores/UANCI-PH02/activos.txt) o el feed general [`feeds/activos.txt`](../feeds/activos.txt).
- **Bloqueen el subdominio, no el dominio raíz:** la pyme dueña del dominio es legítima. La columna `nota` del CSV lo marca en cada caso.
- No bloqueen por IP: algunas son de hosting compartido.

**Marcas suplantadas:** avisen a sus clientes que no cobran deudas por enlaces, y revisen el detalle de cada sitio en su carpeta de [`marcas/`](../marcas/).

**Dueños de dominios (sobre todo pymes con hosting en México):**
- Revisen su zona DNS y busquen subdominios que no crearon, sobre todo los que contengan nombres de empresas chilenas.
- Cambien la clave del panel de hosting, activen el segundo factor y revisen si algún equipo de la empresa tiene malware.
- Si encuentran su dominio en este repositorio, borren el registro y avísennos con la plantilla [**Solicitar corrección**](../CORRECCIONES.md) para marcarlo como limpio.

## Atribución y confianza

- **Alta:** los sitios de Telsur y TAG Total comparten el mismo backend de cobro, el mismo método de subdominios y los mismos servidores.
- **Media-alta:** Falabella, Cencosud, Líder, Santander, Metrogas y CGE comparten con ellos zonas inyectadas, servidores o la misma plantilla.
- **Media:** la variante de BancoEstado usa otro kit, pero llega enlazada desde un sitio de Telsur del actor y usa el mismo método de subdominios y el mismo patrón de servidor.
- Desconocemos el origen geográfico del operador. No hay relación conocida con otros actores de este repositorio.

## Qué no publicamos

A propósito, este informe no incluye:
- las firmas técnicas con que detectamos el kit, porque los operadores también leen;
- los datos de las cuentas que reciben el dinero ni de los intermediarios de pago que usa el operador, que se entregaron por los canales correspondientes;
- datos de víctimas.

Si eres una institución afectada o investigas el caso, escríbenos por un *issue* y coordinamos el canal.

## IoC

- Sitios de este actor: [`actores/UANCI-PH02/iocs.csv`](../actores/UANCI-PH02/iocs.csv)
- Solo activos: [`actores/UANCI-PH02/activos.txt`](../actores/UANCI-PH02/activos.txt)
- STIX 2.1 (actor como *intrusion-set*): [`feeds/iocs.stix2.json`](../feeds/iocs.stix2.json)
