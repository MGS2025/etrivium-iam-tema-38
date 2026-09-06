# Tema 38 — Changelog

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).

---

## v1.2 — 2026-09-06 — Marcado del apartado complementario

**Estado**: pendiente de validación por el IAM.

**Motivo**: criterio de literalidad del título fijado por el IAM (Jesús Cuadrado, 02-09-2026).

### Alcance

- El apartado final que **el enunciado oficial del tema no nombra** queda marcado como **material complementario**, en el índice y al principio del propio apartado, con la advertencia de que lo exigible es lo que enumera el título.
- **Sin cambios de contenido**: el apartado se mantiene íntegro.

---

## v1.1 — 2026-09-06 — Ficha de extensión y tiempo de estudio

**Estado**: sin cambios de contenido. Solo se añade información sobre el propio tema.

**Motivo**: petición del IAM (Jesús Cuadrado, 02-09-2026) al validar el Tema 30. Acepta la extensión de los temas «compuestos» a condición de que se informe de «su extensión en palabras y tiempo estimado de estudio». Al revisarlo se vio que ese dato solo aparecía en 16 de los 40 temas, y que faltaba justo en los más largos.

### Alcance

- Ficha bajo la cabecera del tema, y al final de la pestaña Índice donde esa pestaña existe:
  - **Extensión**: ~23.500 palabras · 18 diagramas · 60 preguntas de test
  - **Tiempo estimado de estudio**: 21-23 horas (primera vuelta completa, sin contar repasos)
- La cifra de palabras de la tabla de entregables se sincroniza con la ficha, para que el tema no muestre dos recuentos distintos.
- Las horas salen de una fórmula común a los 40 temas, para que sean comparables entre sí: contenido a 1.500 palabras/hora (ritmo de estudio activo), diagramas a una hora por cada cinco y test a dos minutos por pregunta. Se publica como intervalo de dos horas.
- Generado con `_tools-qa/ficha_estudio.py`, idempotente y reejecutable tras cualquier regeneración con `build_tNN.py`.

---

## v1.0 — 2026-08-27 — Primera versión

Generación completa del tema desde el esqueleto oficial `Test_Prompting/temas agosto/38.md`, siguiendo el patrón de la serie técnica (plantilla de referencia: **T34**, por ser la que incorpora el conversor corregido).

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | 5 secciones · 17 subsecciones · 16 epígrafes · **≈ 22.800 palabras** |
| Diagramas SVG inline | **18** |
| Banco de test | **60 preguntas** A/B/C, balanceadas **20/20/20** |
| Casos prácticos | **3**, de 10 puntos cada uno |
| Fuentes | 29 Tier 1 · 12 Tier 2 · 3 Tier 3 · 4 categorías descartadas (Tier 4) |
| Pestañas del `index.html` | 8 (Inicio, Contenido, Índice, Diagramas, Test, Casos, Validación, Fuentes) |

### Decisiones de generación

1. **Estructura literal del esqueleto, sin ajustes.** Los 5 bloques, los 17 subapartados y los 16 epígrafes del esqueleto se corresponden uno a uno con los tres niveles de numeración. Es el **cuarto esqueleto de la serie de agosto que encaja sin retoques**, tras T34, T35 y T37, y no repite el problema de mapeo de T27, T30 y T33.

2. **⚠️ Hallazgo normativo de la verificación de fuentes: el CNAF vigente ya no es el de 2021.** Al contrastar las bandas contra el BOE —y no contra fuentes secundarias— se detectó que la **Orden ETD/1449/2021, de 16 de diciembre**, que citan todos los temarios en circulación, fue **derogada con efectos de 18 de julio de 2026** por la **Orden TDF/732/2026, de 10 de julio** (BOE núm. 173, de 17-7-2026, 349 páginas), que incorpora las previsiones de la **CMR-2023**, en vigor en su mayoría desde el 1 de enero de 2025. El tema cita ya la orden vigente. **Debe revisarse si otros temas de la serie citan el CNAF derogado** — el T33 es el candidato más probable.

3. **Notas UN citadas literalmente del PDF del BOE.** De la extracción con `pdftotext -layout` proceden: la **UN-28** («la banda 235-399,9 MHz está destinada a uso exclusivo del Estado para sistemas del Ministerio de Defensa **con excepción de las subbandas 380-385 MHz y 390-395 MHz** que… se destinan para redes de servicios de seguridad de las FCSE y redes de servicios de emergencia»), y la **UN-31**, que es donde el CNAF **cita TETRA por su nombre**: las subbandas **410-415,3 y 420-425,3 MHz** «se destinan a sistemas digitales de acceso aleatorio de canales (**TETRA y otros**)» con canalización de **25 kHz** y separación dúplex de **10 MHz**. También los bloques de **PPDR de banda ancha**: 452-457,5 / 462-467,5 MHz y, en 700 MHz, **733-736 / 788-791 para ámbito nacional** y **698-703 / 753-758 para ámbito autonómico y local**.

4. **Ley 11/2022 verificada sobre el texto consolidado del BOE.** De ahí, literales: el **art. 4.1** («sólo tienen la consideración de **servicio público** los servicios regulados en este artículo», y el artículo es el de seguridad nacional, defensa, **seguridad pública**, seguridad vial y **protección civil»**), el **art. 85.1** (dominio público estatal), el **art. 88** con sus tres modalidades de uso y sus cuatro formas de título, y sobre todo el **art. 88.5.b)**: el uso privativo para autoprestación se otorga por autorización individual «**salvo en el caso de Administraciones públicas, que requerirán de afectación demanial**». Ése es el dato jurídico más específico del tema: **la red TETRA de un ayuntamiento se ampara en una afectación demanial**, no en una concesión. Y el **art. 94.1**: cinco años, hasta el 31 de diciembre del año natural en que se cumplan, renovables por períodos de cinco.

5. **ENS verificado contra el PDF del BOE.** Denominación y tabla de aplicación literales de **`mp.com.4`, «separación de flujos de información en la red»**, con su requisito **`.2`** («si se emplean comunicaciones inalámbricas, será en un segmento separado»), sus refuerzos **R1 VLAN / R2 VPN / R3 medios físicos / R4 puntos de interconexión** y el dato de examen de que **no aplica en categoría BÁSICA**. También el bloque **`mp.if.1` a `mp.if.7`** —con `mp.if.4`, energía eléctrica, como respaldo de las baterías de los emplazamientos— y `op.cont.1-4`, `mp.si.2`, `mp.eq.4` y `op.exp.10`.

6. **Seguridad de TETRA leída de fuente técnica primaria y libre.** El informe **TTR 001-11 v4.1.0 de la TCCA** (17-8-2023) proporcionó, sin necesidad de comprar la norma ETSI: las **clases de seguridad SC1, SC2, SC3 y SC3G**; la distinción entre **claves estándar** (SCK, DCK, CCK, GCK), usadas con el **TEA set A**, y **claves extendidas** (SCKX, DCKX, CCKX, GCKX), usadas con el **TEA set B** y el conjunto de autenticación **TAA2** con clave **K2**; el **modo de repliegue de SC3 a SC2** cuando una célula pierde el enlace con el centro de autenticación; y el cifrado de identidades **ESI** y **MAE**.

7. **Las dos divulgaciones de seguridad tratadas como contenido de primer nivel, con fechas y CVE.** **TETRA:BURST** (agosto de 2023, USENIX Security): **CVE-2022-24402**, la reducción deliberada de la clave de **TEA1** a **~32 bits** efectivos —que la TCCA justifica en el **Acuerdo de Wassenaar**—; **CVE-2022-24401**, el oráculo de descifrado por el **tiempo de red no autenticado**; **CVE-2022-24403**, desanonimización; **CVE-2022-24404**, maleabilidad. Y **2TETRA:2BURST** (Black Hat USA, **7 de agosto de 2025**): **CVE-2025-52944** (**el protocolo no autentica los mensajes**), **CVE-2025-52943** (**soportar TEA1 junto a otros algoritmos compromete también a los demás** — la de mayor consecuencia práctica), **MBPH-2025-001** (la corrección del ETSI para CVE-2022-24401 es ineficaz) y **CVE-2025-52940/41/42**, que alcanzan al **cifrado extremo a extremo**, incluida una variante debilitada de **AES-128 con 56 bits efectivos**.

8. **La confusión SIRDEE / TETRA elevada a advertencia estructural.** El **SIRDEE**, la red de emergencia del Estado en servicio desde el año 2000, está construido sobre **TETRAPOL** —FDMA, 12,5 kHz, GMSK— y **no sobre TETRA**. Es la trampa más rentable del tema y aparece tres veces: en las «Convenciones», en §5.1 y en el bloque de cierre, además de en la pregunta 49 del test.

9. **Datos de despliegue reales, y marcados como ilustrativos.** Red municipal: plataforma **DIMETRA-TETRA**, **más de 3.000 efectivos** de seis servicios, contrato de mantenimiento y evolución de **cinco años** adjudicado en **marzo de 2026** con **disponibilidad 24×7**, y contrato de operación de redes de la D. G. de Policía Municipal aprobado en **julio de 2026** (**933.000 €**, tres años). Red autonómica: **113 estaciones base**, **5.316 terminales**, **ASEM 112**, casi **40 M€** a cinco años y **2.263 terminales nuevos** en 2025. Y el dato con más fuerza argumental del tema: durante el **apagón del 28 de abril de 2025** la red TETRA **siguió operativa** por el respaldo de baterías, hasta el punto de que en **mayo de 2026** la Comunidad dotó de terminal a **53 municipios pequeños**.

10. **Secuencia de letras del test fijada antes de redactar** (lección de T23). Resultado: **20/20/20**, con **una sola desviación** (P40), detectada por el script de verificación antes de publicar y corregida permutando el texto de las opciones.

11. **Distractores construidos con cifras reales de otro concepto del propio tema** —la multitrama como distractor de la hipertrama, los 4,615 ms de GSM, los 25 kHz de la portadora frente a los 6,25 kHz por canal— en lugar de con números inventados. Es lo que hace que la pregunta discrimine de verdad.

12. **Sin fragmentos de código**, como en T26 y T28-T35: lo memorizable son cifras de capa física, bandas, siglas, normas y preceptos.

### QA realizado

- **Integridad del test**: 60 preguntas, 3 opciones únicas, coincidencia exacta entre solución y opción, explicación y referencia en las 60. **20 A / 20 B / 20 C** verificado por script contra la secuencia planificada.
- **SVG**: **validación XML previa** de los 18 diagramas (lección del tercer falso OK de T32) y sonda `getBBox` sobre render real con los **tres** chequeos de `_tools-qa/qa_svg.py`: desborde del `viewBox`, colisión entre textos y **texto solapado con un `<rect>` que no lo contiene**.
- **Comprobación preventiva del cuarto modo de fallo silencioso** (T33/T34): `grep` para verificar que **ningún elemento SVG mezcla `class` con el atributo `fill`**, que es un fallo que ninguna sonda de geometría detecta. Salió vacío desde la primera generación, porque los diagramas se escribieron ya con esa regla.
- **Revisión visual de los 18 diagramas** por captura a 2×.
- **Motor de test probado sobre HTTP** (no sobre `file://`): renderizado, penalización, corrección y reinicio.
- **Markdown crudo filtrado al HTML**: recuento de filas `|---` y de asteriscos crudos sobre el `index.html` con `<script>`, `<svg>`, `<style>` y `<pre><code>` eliminados.
- **Ortografía**: hunspell es_ES sobre la prosa y, por separado, sobre el texto visible y los `aria-label` de los SVG, revisando **mayúsculas y minúsculas** (lección de T33, donde se colaron «MAS» por «MÁS»).
- **Referencias cruzadas**: 14 temas citados (T6, T22, T24, T26, T29, T31, T32, T33, T34, T35, T36, T37, T39 y T40), todos validados contra el temario oficial BOAM 10.032.

### Pendientes para QA / próxima iteración

- Validación de contenido por **María y Ana**, y de los **nueve puntos abiertos** por el **IAM** (ver `tema-38-validacion.md`), en especial el **hallazgo del CNAF derogado**, que afecta a otros temas de la serie, y el **nivel de detalle de los identificadores CVE** para un C1.
- Solicitar al IAM el **dato interno y actualizado de estaciones base y terminales de la red municipal**, que las fuentes públicas dan de forma dispar.
- **Reverificar los datos de despliegue antes de cada convocatoria**: son notas de prensa de 2024-2026 y envejecen rápido. El tema está redactado para que esas cifras sean ilustrativas y no memorizables.
- Vigilar la evolución de la **migración del SIRDEE a banda ancha** y de las decisiones sobre el espectro **PPDR de 700 MHz de ámbito autonómico y local**, que es el que afectaría a una eventual red municipal.
