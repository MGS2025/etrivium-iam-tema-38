# Tema 38 — Validación

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
>
> **Versión**: v1.0 — **Pendiente de validación por María, Ana y el IAM**
> **Fecha**: 2026-08-27

---

## 1. Cobertura del temario oficial

El enunciado oficial (BOAM 10.032, tema 38) es el **único de los cuarenta que se dedica a un solo sistema con nombre propio**, y por tanto no enumera materias. El esqueleto de partida (`Test_Prompting/temas agosto/38.md`) sí lo hace, y se ha seguido **literalmente**:

| Bloque del esqueleto | Sección | Estado |
|---|---|---|
| Introducción y fundamentos de los sistemas móviles de radiocomunicación | §1 | ✅ Completo |
| Arquitectura y componentes de la red TETRA | §2 | ✅ Completo |
| Capa física y transmisión radio en TETRA | §3 | ✅ Completo |
| Servicios y seguridad en sistemas TETRA | §4 | ✅ Completo |
| Ámbito público, normativa y evolución tecnológica | §5 | ✅ Completo |

**Mapeo del esqueleto: sin ningún ajuste.** Los **5** bloques de primer nivel del esqueleto se corresponden con las 5 secciones; sus **17** subapartados, con la numeración `N.M`; y sus **16** epígrafes de tercer nivel, con la numeración `N.M.K`. Es el **cuarto esqueleto de la serie de agosto que encaja sin retoques en los tres niveles**, tras el T34, el T35 y el T37, y no repite el problema de mapeo de los Temas 27, 30 y 33 —que sigue pendiente de decidir de forma uniforme para toda la serie—.

## 2. Contenido teórico

- **5 secciones · 17 subsecciones · 16 epígrafes numerados** (numeración de tres niveles, coherente con el resto de la serie técnica).
- **≈ 22.800 palabras** medidas con `wc -w`. Es el **cuarto tema más extenso de la serie**, por detrás de T32 (≈25.000), T33 (≈24.500) y T37 (≈23.000), y por delante de T34 (≈21.500), T30 (≈21.400) y T29 (≈21.200).
- **4 tipos de callout**: `[DATO CLAVE EXAMEN]` (50), `[EJERCICIO RESUELTO]` (6), `[EJEMPLO AYTO MADRID]` (14) y `[REFERENCIA CRUZADA]` (13).
- **Caso de referencia transversal**: la **red DIMETRA-TETRA municipal** gobernada desde el **CISEM**, que atraviesa las cinco secciones y enlaza con los tres casos prácticos.
- **Sin fragmentos de código**, como en T26, T28, T29, T30, T31, T32, T33, T34 y T35. Decisión deliberada y evidente en este tema: el enunciado no menciona ningún lenguaje y lo memorizable son **cifras de la capa física, bandas de frecuencia, siglas, números de norma y preceptos legales**, concentrados en tablas y en los diagramas D9, D10, D12 y D16.
- Cierre con un bloque de **«los ocho datos que no se pueden fallar»**, no numerado, a modo de resumen memorístico.
- **Dos advertencias abren el tema**, por decisión editorial: (a) que este es un tema **de datos exactos**, porque al versar sobre un sistema concreto el examen puede bajar al detalle numérico; y (b) que **el SIRDEE no es TETRA sino TETRAPOL**, que es la confusión más penalizada de la materia.

## 3. Fuentes

- **Tier 1**: 10 referencias de normativa española y europea + 13 especificaciones del ETSI/TCCA + 6 de otras organizaciones (CEPT/ECC, Comisión Europea, 3GPP, UIT).
- **Tier 2**: 12 referencias de investigación de seguridad, documentación de organismos gestores y datos oficiales de despliegue, todas fechadas.
- **Tier 3**: 3 referencias de contexto municipal. **Tier 4**: 4 categorías de fuentes consultadas y **descartadas** como fuente de contenido, con el motivo.
- **Verificación contra fuente primaria** (no de memoria ni de fuentes secundarias):
  - **CNAF**: PDF oficial del BOE descargado y extraído con `pdftotext -layout` (349 páginas). De ahí procede el hallazgo del punto 8.1 y el texto literal de las notas **UN-28**, **UN-31**, **UN-27** y **UN-77**, así como los bloques de PPDR de banda ancha de 452 MHz y de 700 MHz.
  - **Ley 11/2022**: texto consolidado del BOE en PDF. De ahí, literales, los arts. **4.1**, **85.1**, **88** (apartados 1, 3, 5 y 6), **91** y **94.1**.
  - **ENS**: PDF oficial del BOE (`BOE-A-2022-7191`). De ahí, literales, la medida **`mp.com.4`** con sus cuatro refuerzos y su tabla de aplicación, el bloque **`mp.if.1` a `mp.if.7`** y las medidas `op.cont.1-4`, `mp.si.2` y `mp.eq.4`.
  - **Seguridad de TETRA**: informe **TTR 001-11 v4.1.0 de la TCCA** (17 de agosto de 2023), de acceso libre, extraído a texto. De ahí las **clases de seguridad SC1, SC2, SC3 y SC3G**, la distinción entre **claves estándar y claves extendidas**, el **modo de repliegue de SC3 a SC2** y el cifrado de identidades **ESI** y **MAE**.
  - **Vulnerabilidades**: página de divulgación de **Midnight Blue** para *2TETRA:2BURST*, con los seis identificadores y sus fechas, y la posición oficial de la **TCCA** sobre ambas divulgaciones.

## 4. Test (60 preguntas)

- **60 preguntas** de 3 opciones (A/B/C), formato oficial de la oposición, con penalización de **1/3** en el motor de corrección.
- **Distribución de la respuesta correcta: 20 A / 20 B / 20 C**. La secuencia de letras se fijó **antes** de redactar (lección de T23); una única pregunta (P40) se desvió de la secuencia planificada, **lo detectó el script de verificación antes de publicar** y se corrigió permutando el texto de las opciones.
- Reparto por materia: **P1-P9** fundamentos de la PMR y del *trunking* · **P10-P22** arquitectura y componentes · **P23-P33** capa física y transmisión radio · **P34-P48** servicios y seguridad · **P49-P60** ámbito público, normativa y evolución.
- Verificación automática: 60 preguntas, 3 opciones únicas por pregunta, **coincidencia exacta** entre el texto de la opción correcta y el de la solución, explicación y referencia a epígrafe y fuente en las 60.
- **Criterio de redacción de los distractores**: en las preguntas de cifras, los distractores son **cifras reales de otro concepto del propio tema** (por ejemplo, la duración de la multitrama como distractor de la hipertrama, o los 4,615 ms de la trama de GSM), no números inventados. Es lo que hace que la pregunta discrimine.

## 5. Casos prácticos (3)

Los tres se sitúan en el Ayuntamiento de Madrid y comparten el sistema de referencia del tema:

1. **Incidente en un aparcamiento subterráneo del distrito de Salamanca** (§1.2, §2.2, §3.4 y §4.1): elección de TMO y DMO, distinción entre **DM-REP y DM-GATE**, DGNA y entrada tardía, los tres escalones de prioridad y el efecto completo del botón de emergencia, y cálculo de la capacidad de una célula de 3 portadoras.
2. **Informe de seguridad sobre una oferta de renovación de 1.200 terminales** (§4.3 y §5.2): rechazo de TEA1 con las dos divulgaciones aplicables, exigencia de **SC3** con autenticación mutua y de **OTAR**, refutación de la afirmación de que el cifrado de interfaz aire protege «de punta a punta», y respaldo normativo del ENS incluida la prohibición de compartir segmento con la ofimática.
3. **Renovación del título habilitante y decisión de evolución** (§3.1, §5.1, §5.2 y §5.4): corrección de la idea de «frecuencias concedidas a perpetuidad», **afectación demanial** del art. 88.5.b), elección de banda según el **servicio** y no según el solicitante, seis argumentos contra la sustitución por telefonía comercial con el **apagón del 28-4-2025** como evidencia, y vía de evolución realista con el espectro PPDR que la norma ya tiene reservado.

Cada caso suma **10 puntos** repartidos en cuatro cuestiones, con solución orientativa y tabla de criterios de evaluación.

## 6. Diagramas (18 SVG)

Todos inline, sin dependencias externas, con `viewBox`, `role="img"` y `aria-label` descriptivo, paleta del Ayuntamiento y clases CSS con sufijo numérico único por diagrama.

| Bloque | Diagramas |
|---|---|
| §1 Fundamentos | D1 generaciones de la PMR · D2 convencional frente a troncalizado · D3 familia de normas |
| §2 Arquitectura | D4 topología de red · D5 las tres capas de la SwMI · D6 terminales e identidades · D7 TMO, DMO, repetidor y pasarela · D8 las seis interfaces |
| §3 Capa física | D9 el espectro según el CNAF · D10 FDMA + TDMA y la cadena de cifras · D11 modulación π/4-DQPSK · D12 jerarquía temporal · D13 canales lógicos |
| §4 Servicios y seguridad | D14 tipos de llamada y prioridades · D15 servicios de datos · D16 cadena de seguridad · D17 AIE frente a E2EE y cronología de las divulgaciones |
| §5 Ámbito público | D18 de TETRA a la banda ancha crítica |

**Los cuatro más rentables para el estudio**: **D9** (bandas y notas UN literales), **D10** (la cadena 25 kHz → 18 kbaudios → 36 kbit/s → 7,2 kbit/s), **D12** (jerarquía temporal) y **D16** (autenticación, claves y clases de seguridad).

## 7. Referencias cruzadas a otros temas

Se citan **14 temas** del temario oficial, todos validados contra el enunciado del BOAM 10.032:

| Tema citado | Motivo |
|---|---|
| T6 | Marco de transparencia y acceso, a propósito de la grabación de comunicaciones |
| T22 | Arquitecturas cliente/servidor, para las aplicaciones que usan la radio como canal de datos |
| T24 | Desarrollo para dispositivos móviles y diseño para enlaces de baja capacidad |
| T26 | Continuidad, copias de seguridad y recuperación |
| T29 | Gestión de incidencias y acuerdos de nivel de servicio |
| T31 | Dependencia de proveedor |
| T32 | Criptografía, autenticación, entropía de clave y ataques de repetición |
| T33 | Medios de transmisión, modulación digital, multiplexación y comunicaciones móviles |
| T34 | Modelo OSI y TCP/IP, transporte de IP sobre enlaces de baja capacidad |
| T35 | Cifrado por tramos frente a cifrado extremo a extremo (TLS) |
| T36 | Seguridad perimetral, acceso remoto seguro y VPN |
| T37 | Redes locales, técnicas de transmisión y métodos de acceso |
| T39 | ENS y ENI, neutralidad tecnológica y medidas de continuidad |
| T40 | Videoconferencia y colaboración, como justificación del salto de capacidad |

## 8. Puntos abiertos que deben confirmar María, Ana o el IAM

**8.1. Hallazgo normativo que conviene comunicar de inmediato: el CNAF de referencia ha cambiado.** Al verificar las bandas contra el BOE se detectó que la **Orden ETD/1449/2021** —el CNAF que citan todos los temarios en circulación— fue **derogada con efectos de 18 de julio de 2026** por la **Orden TDF/732/2026, de 10 de julio** (BOE núm. 173, de 17 de julio de 2026, 349 páginas), que incorpora la **CMR-2023**. El tema cita ya la orden vigente. **Debe revisarse si otros temas de la serie citan el CNAF derogado** —el T33 es el candidato más probable— y, en su caso, corregirlos.

**8.2. Profundidad del bloque de seguridad (§4.3).** Se ha desarrollado con detalle porque el enunciado del esqueleto dedica tres epígrafes de tercer nivel a la seguridad y porque las divulgaciones de 2023 y 2025 son material de actualidad con alta probabilidad de aparecer. **A validar**: si el nivel de detalle de los identificadores CVE es el adecuado para un C1 o si conviene dejarlos como contexto y memorizar solo el fenómeno (TEA1 debilitado, protocolo sin autenticación de mensajes).

**8.3. Frontera con el Tema 33.** El T33 cubre «comunicaciones móviles e inalámbricas» en general. Aquí se ha dado por sabida esa panorámica y se ha entrado directamente en el sistema. **A validar** que ese reparto es el que el IAM espera, y en particular quién explica los conceptos de FDMA, TDMA y CDMA: aquí se explican **solo en lo que TETRA los usa**.

**8.4. Frontera con el Tema 37.** El T37 cubre «redes locales… métodos de acceso». El criterio aplicado es el mismo que en T30 y T34: **el T37 describe los métodos de acceso al medio en redes locales**, y aquí se explica **el acceso múltiple radio**, que es otra cosa. **A validar** por ser una frontera que se ha revelado delicada en tres temas ya.

**8.5. Peso del bloque normativo (§5.2).** El régimen jurídico del espectro ocupa una parte apreciable del tema, y se ha desarrollado con literalidad de artículos porque es lo que distingue una respuesta buena de una excelente en un caso práctico de la Administración. **A validar** si ese peso es el correcto o si el IAM prefiere remitirlo a otro tema.

**8.6. Actualidad de los datos de despliegue.** Las cifras de la red municipal y de la autonómica proceden de notas de prensa oficiales de 2024 a 2026 y **envejecen rápido**. Están redactadas para ser **ilustrativas y no memorizables**, pero conviene **reverificarlas antes de cada convocatoria**. Se pide además al IAM, si es posible, **el dato interno y actualizado del número de estaciones base y terminales de la red municipal**, que las fuentes públicas dan de forma dispar.

**8.7. Tratamiento de los términos ingleses.** Se ha mantenido el término original entre paréntesis la primera vez (*trunking*, *push-to-talk*, *late entry*, *pre-emptive priority*) y después se ha usado la forma española. **Es la misma decisión pendiente de unificar que se anotó en el T35** para toda la serie.

**8.8. Escucha ambiente y geolocalización.** El tema describe estas funciones y advierte de que exigen procedimiento, autorización y registro por su impacto en derechos de los empleados públicos. **A validar** si conviene desarrollar más ese encuadre o si, al no existir tema dedicado a protección de datos en el temario oficial, es mejor dejarlo como advertencia.

**8.9. Nivel de detalle de la capa física.** §3 baja hasta los tipos de ráfaga y los canales lógicos. **A validar** si es proporcionado para un C1 o si basta con la cadena de cifras y la jerarquía temporal.

## 9. QA realizado antes de publicar

- **Integridad del test**: 60 preguntas, 3 opciones únicas por pregunta, coincidencia exacta entre solución y opción, explicación y referencia en las 60. Distribución **20/20/20** verificada por script contra la secuencia planificada.
- **SVG**: los 18 diagramas validados como **XML** antes de medir, y sonda `getBBox` sobre render real con los tres chequeos de `_tools-qa/qa_svg.py` (desborde del `viewBox`, colisión entre textos y texto solapado con un `<rect>` que no lo contiene).
- **Revisión visual** de los 18 diagramas por captura a 2×, que es la única forma de detectar los fallos que la geometría no ve.
- **Comprobación de que ningún elemento SVG mezcla `class` con el atributo `fill`**, que fue el cuarto modo de fallo silencioso descubierto en T33 y T34.
- **Markdown crudo filtrado al HTML**: recuento de filas `|---` y de asteriscos crudos en el `index.html` con `<script>`, `<svg>`, `<style>` y `<pre><code>` eliminados.
- **Motor de test probado sobre HTTP**, no sobre `file://`.
- **Ortografía** con hunspell es_ES sobre la prosa y, por separado, sobre el texto visible y los `aria-label` de los SVG, revisando **mayúsculas y minúsculas** por separado.
- **Referencias cruzadas** validadas una a una contra el temario oficial BOAM 10.032.
