# UANCI-PH02 · Mirlo

*Deudas y promociones falsas con cobro en tiempo real.* Cobra deudas falsas (telefonía, peajes TAG, electricidad, gas) o vende promociones falsas (viajes, puntos, supermercado) y cobra en el momento con la tarjeta de la víctima: paga de verdad, pero al operador. Se monta sobre subdominios inyectados en zonas DNS de pymes, sobre todo mexicanas, apuntando a VPS de bajo costo. El dominio raíz suele ser legítimo y no sabe que lo usan: bloquea el subdominio, no la zona.

Desde noviembre de 2026 también usa **páginas falsas de banca** (BancoEstado) que roban RUT, clave, teléfono y tarjeta, enlazadas desde sus sitios de deuda falsa y montadas con el mismo método de subdominios inyectados.

**Por qué Mirlo:** el mirlo chileno (*Molothrus bonariensis*) es un parásito de nidos: pone sus huevos en nidos ajenos para que otros pájaros los críen. Este actor hace lo mismo: inyecta sus subdominios en zonas DNS de terceros y vive de la infraestructura de otros.

**43** sitios · **1** activos · 2026-11-05 → 2026-11-24

Marcas suplantadas: [Banco Santander](../../marcas/santander/), [BancoEstado](../../marcas/bancoestado/), [CGE](../../marcas/cge/), [Cencosud](../../marcas/cencosud/), [Falabella](../../marcas/falabella/), [Líder](../../marcas/lider/), [Metrogas](../../marcas/metrogas/), [TAG Total (Unired)](../../marcas/tag-total/), [Telsur (GTD)](../../marcas/telsur/)

- Bloquear: [`activos.txt`](activos.txt)
- Histórico: [`iocs.csv`](iocs.csv)

| Detectado | Dominio | Marca | Tipo | Estado |
|---|---|---|---|---|
| 2026-11-24 | `telsurenlinea2[.]gotammaintenance[.]com[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-24 | `mitelsur[.]inomodul[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-22 | `telsurenlinea[.]daremexicali[.]org` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-21 | `estadoenlinea[.]dizukmex[.]com[.]mx` | BancoEstado | credenciales bancarias y tarjeta | 🔴 activo |
| 2026-11-18 | `tutslur[.]cdisatelite[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-18 | `telsurechile[.]cecoban[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-18 | `servicios[.]actanonverba[.]mx` | Telsur (GTD) | redirector hacia el kit | caido |
| 2026-11-17 | `telsurchile[.]beautyl[.]com[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-17 | `tagtotal[.]elcaporalmx[.]com` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-16 | `tutelsurenlinea[.]cippsa[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-14 | `tutelsur[.]avdisenoyarquitectura[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-13 | `tutelsurenlinea[.]germen[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-13 | `45[.]61[.]161[.]236` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-12 | `viajespromocionales[.]accels[.]mx` | Falabella | pago con tarjeta | caido |
| 2026-11-12 | `tutelsurenlinea[.]dyaagencia[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-12 | `tagtotal[.]perfax[.]com[.]mx` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-12 | `puntoscen[.]mnlvqz[.]com` | Cencosud | pago con tarjeta | caido |
| 2026-11-12 | `normas[.]contornoestudio[.]com` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-12 | `normas[.]arnom[.]com[.]mx` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-12 | `consultas[.]boutiquemonet[.]com` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-12 | `consultar[.]1-asesoria-contable[.]mx` | TAG Total (Unired) | pago de deuda falsa | caido |
| 2026-11-06 | `telsurpagos[.]wikumx[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-06 | `telefoniadelsur1[.]aupaireducare[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| 2026-11-05 | `teslurenlinea[.]adconga[.]com[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| — | `tutelsurenlinea[.]accels[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| — | `tutelsur[.]openstudiomexico[.]com` | Telsur (GTD) | pago de deuda falsa | caido |
| — | `travelfalabella[.]mnlvqz[.]com` | Falabella | pago con tarjeta | caido |
| — | `travel3[.]mnlvqz[.]com` | Falabella | pago con tarjeta | caido |
| — | `telsurpagos[.]acap[.]com[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| — | `telsur[.]adconga[.]com[.]mx` | Telsur (GTD) | pago de deuda falsa | caido |
| — | `seguros[.]asser[.]com[.]mx` | Metrogas | pago de deuda falsa | caido |
| — | `promocionesdeviajes[.]newpoint[.]com[.]mx` | Falabella | pago con tarjeta | caido |
| — | `promociones[.]viajesyprogramas[.]com` | Falabella | pago con tarjeta | caido |
| — | `pautas[.]arnom[.]com[.]mx` | TAG Total (Unired) | pago de deuda falsa | caido |
| — | `pagos[.]cge[.]sucursal[.]cl[.]beautyl[.]com[.]mx` | CGE | pago de deuda falsa | caido |
| — | `lider1serviciosenlinea[.]aupaireducare[.]mx` | Líder | pago con tarjeta | caido |
| — | `falabellapromociones[.]newpoint[.]com[.]mx` | Falabella | pago con tarjeta | caido |
| — | `diagnostico[.]contornoestudio[.]com` | TAG Total (Unired) | pago de deuda falsa | caido |
| — | `diagnostico-ti[.]arnom[.]com[.]mx` | TAG Total (Unired) | pago de deuda falsa | caido |
| — | `bsantanderpersonas[.]acap[.]com[.]mx` | Banco Santander | credenciales bancarias | caido |
| — | `asesoria[.]fftechequipment[.]com` | Metrogas | pago de deuda falsa | caido |
| — | `asesoria[.]acap[.]com[.]mx` | Metrogas | pago de deuda falsa | caido |
| — | `acceso1santander[.]cl[.]accels[.]mx` | Banco Santander | credenciales bancarias | caido |
