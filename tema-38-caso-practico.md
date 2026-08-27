# Tema 38 — Casos Prácticos

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
>
> **Formato**: 3 casos prácticos sobre supuestos reales del Ayuntamiento de Madrid. Cada caso suma **10 puntos**.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

Los tres casos giran sobre el supuesto de referencia del tema (ver tema-38-contenido.md, «Convenciones»): la **red DIMETRA-TETRA municipal**, gobernada desde el **CISEM**. El **Caso 1** trabaja la **operación sobre el terreno** —modos, cobertura, grupos y prioridades—; el **Caso 2**, la **seguridad** de la red frente a las vulnerabilidades divulgadas y el respaldo del ENS; y el **Caso 3**, el **régimen jurídico del espectro** y la decisión de evolución hacia la banda ancha crítica.

---

## Caso 1 — Incidente en un aparcamiento subterráneo del distrito de Salamanca

### Enunciado

A las 03:40 se recibe en el **CISEM** un aviso de incendio en el **nivel −3 de un aparcamiento subterráneo**. Se movilizan **dos dotaciones de Bomberos**, una **UVI móvil del SAMUR-Protección Civil** y una unidad de **Policía Municipal** que corta el tráfico en superficie. Los primeros datos técnicos son:

- La cobertura de la red municipal en el nivel −3 es **nula**; en el nivel −1 es marginal.
- El vehículo de mando de Bomberos queda estacionado en la rampa de acceso, con **cobertura buena**.
- El operador del CISEM ha creado el grupo `INC-0340-SALAMANCA` y lo ha cargado en los terminales de las unidades intervinientes.
- Los agentes de Policía Municipal en superficie llevan **portátiles de 1 W**; los equipos embarcados son de **10 W**.
- Durante la intervención, la red del centro de la ciudad registra una ocupación alta por otro operativo simultáneo.

Se pide un informe técnico-operativo.

### Cuestiones

**Cuestión 1 — Modos de operación y cobertura (3 puntos).** Indique en qué modo debe trabajar cada colectivo y por qué, y qué equipo hay que desplegar para que el CISEM no pierda a las dotaciones que descienden al nivel −3. Distinga con precisión entre las dos figuras que la norma prevé para ampliar el modo directo.

**Cuestión 2 — Grupos de conversación (2 puntos).** Explique qué función del estándar ha usado el operador del CISEM para crear y cargar `INC-0340-SALAMANCA`, por qué esa función es imposible en radio convencional y qué ocurre con un terminal que se afilia al grupo cuando la conversación ya ha empezado.

**Cuestión 3 — Prioridades y saturación (3 puntos).** Con la red del centro saturada por otro operativo, explique los tres escalones de prioridad que garantizan que este incidente entre igualmente, y qué sucede exactamente si un bombero pulsa el botón de emergencia.

**Cuestión 4 — Dimensionado (2 puntos).** Si la estación base que cubre la zona tiene **3 portadoras** y dedica un intervalo al canal de control, ¿cuántas conversaciones simultáneas admite en esa célula? Razone por qué el número de **grupos** que pueden convivir no está limitado por esa cifra.

### Solución orientativa

- **C1**: (§2.2.2, §2.2.3) El **mando del incidente, la Policía Municipal en superficie y el CISEM** trabajan en **TMO**, que es donde hay despacho, grabación y visión de posiciones. Las **dotaciones que descienden al nivel −3** deben pasar a **DMO**, porque no hay cobertura de red; entre ellas se oirán, pero el CISEM no. Para recuperar el enlace hay que configurar el **vehículo de mando estacionado en la rampa como DM-GATE**, es decir, **pasarela**: recibe en modo directo y **reinyecta la comunicación en la red troncalizada**, devolviendo al CISEM la audición, la posibilidad de hablar con el interior y la grabación. Si el alcance del modo directo no bastara para cubrir todo el nivel −3, se añadiría un **DM-REP** —o se emplearía un equipo **DM-REP/GATE**— para ampliar el alcance **dentro** del modo directo antes de reinyectar. **La distinción es la clave de la cuestión**: un **DM-REP** solo haría que las dotaciones se oyeran más lejos entre sí, **sin que el CISEM se enterara de nada**. Debe mencionarse además que el **portátil de 1 W** del agente tiene bastante menos alcance que el **equipo embarcado de 10 W**, lo que refuerza el papel del vehículo como nodo.
- **C2**: (§4.1.1) La función es la **DGNA** (*Dynamic Group Number Assignment*): permite **crear un grupo nuevo y cargarlo por el aire** en los terminales seleccionados desde la consola, sin tocar los equipos. Es imposible en radio convencional porque allí **el grupo es una frecuencia física** y cambiar la organización obligaría a **reprogramar equipo por equipo**. En TETRA el grupo es una **entidad lógica** identificada por su **GSSI**. Un terminal que se afilia con la llamada ya iniciada se incorpora a ella gracias a la **entrada tardía** (*late entry*), posible porque la **trama 18 de cada multitrama** está reservada a señalización y permite avisar al terminal sin interrumpir el tráfico.
- **C3**: (§4.1.2) Los tres escalones son: **(1) prioridad de acceso**, que ordena la **cola** cuando varias peticiones compiten por el mismo canal, sin cortar a nadie; **(2) prioridad con desalojo** (*pre-emptive priority*), que **corta** una comunicación en curso de prioridad inferior cuando **no hay ningún canal libre**; y **(3) llamada de emergencia**, el nivel máximo. Al pulsar el botón de emergencia se produce: establecimiento **inmediato** en el grupo de emergencia con máxima prioridad y desalojo; **alarma visual y sonora** en la consola del CISEM con la **identidad** del usuario y, si el terminal la envía, su **posición**; y apertura de un **canal de voz abierto** que, en las configuraciones habituales, no exige que el agente pulse el PTT, de modo que si está incapacitado el centro **oye igualmente** lo que ocurre. Conviene añadir que este comportamiento **no se puede replicar con telefonía móvil comercial**, porque en una red pública el Ayuntamiento no decide a quién se desaloja.
- **C4**: (§1.2, §3.4) **3 portadoras × 4 intervalos = 12 canales físicos**; menos **1** dedicado al canal de control principal → **11 conversaciones simultáneas** en esa célula. El número de **grupos** no está limitado por esa cifra porque un grupo **solo consume canal mientras alguien transmite**, y solo en las **células donde hay afiliados**: pueden convivir decenas de grupos afiliados mientras no hablen más de once a la vez. Se valorará que se mencione que el dimensionado de una red de emergencia se hace por **transmisiones simultáneas previstas en la hora punta de la célula más cargada**, con margen para el escenario de gran emergencia, y no por número de usuarios.

### Criterios de evaluación

| Cuestión | Elemento | Puntos |
|---|---|---|
| 1 | Asignar TMO a superficie y DMO al subsuelo, con justificación | 1,0 |
| 1 | Identificar el **DM-GATE** como la solución, y explicar por qué el DM-REP **no** resuelve el problema | 1,5 |
| 1 | Mencionar el DM-REP/GATE o la diferencia de alcance entre 1 W y 10 W | 0,5 |
| 2 | Identificar la **DGNA** y explicar el contraste con la radio convencional | 1,0 |
| 2 | Explicar la **entrada tardía** y el papel de la trama de control | 1,0 |
| 3 | Enumerar y distinguir los **tres escalones** de prioridad | 1,5 |
| 3 | Describir el efecto completo del **botón de emergencia** | 1,0 |
| 3 | Señalar que la prioridad no es replicable en una red comercial | 0,5 |
| 4 | Cálculo correcto: 12 canales físicos − 1 de control = **11** | 1,0 |
| 4 | Razonar que el grupo solo consume canal al transmitir, y solo donde hay afiliados | 1,0 |
| | **Total** | **10** |

---

## Caso 2 — Informe de seguridad sobre una oferta de renovación de terminales

### Enunciado

El Ayuntamiento licita la renovación de **1.200 terminales** de la red municipal. Una de las ofertas presenta las siguientes características, y se solicita informe técnico de la unidad TIC:

- Los terminales soportan **TEA1 y TEA2**, y se propone **configurar TEA1** «por ser el de exportación libre y estar disponible en todo el parque actual, dejando TEA2 activo por compatibilidad».
- La red operaría en **clase de seguridad SC2**, «para simplificar, evitando la carga del centro de autenticación».
- **No** se ofrece cifrado extremo a extremo. El fabricante alega que «el cifrado de interfaz aire ya protege la comunicación de punta a punta».
- **No** se incluye la capacidad de **distribución de claves por el aire**: la renovación de claves se haría recogiendo los terminales en el almacén una vez al año.
- El sistema se ha categorizado **MEDIA** conforme al ENS.
- Se propone conectar las **consolas de despacho** al mismo segmento de red que la ofimática municipal, «para simplificar el cableado».

### Cuestiones

**Cuestión 1 — Algoritmos de cifrado (3 puntos).** Valore la propuesta de configurar TEA1 y de mantener TEA2 «por compatibilidad». Cite las vulnerabilidades divulgadas que resultan aplicables y explique qué exigencia concreta debe incorporarse al pliego.

**Cuestión 2 — Clase de seguridad y gestión de claves (3 puntos).** Analice la elección de SC2 y la ausencia de distribución de claves por el aire. Indique qué clase debe exigirse y por qué, y qué relación existe entre autenticación y cifrado en TETRA.

**Cuestión 3 — Cifrado extremo a extremo (2 puntos).** Rebata la afirmación del fabricante. Explique qué protege cada capa y qué debe exigirse si finalmente se decide implantar cifrado extremo a extremo.

**Cuestión 4 — Respaldo normativo (2 puntos).** Cite las medidas del **ENS** que amparan cada una de las correcciones anteriores, incluida la relativa al segmento de red de las consolas.

### Solución orientativa

- **C1**: (§4.3.2) La propuesta es **inaceptable en sus dos extremos**. Primero, **TEA1 tiene una reducción deliberada de la longitud efectiva de clave a unos 32 bits** —de los 80 nominales—, lo que permite **romperla por fuerza bruta en minutos con hardware doméstico** (**CVE-2022-24402**, divulgada en agosto de 2023 dentro de **TETRA:BURST**); la TCCA ha confirmado que la reducción fue **intencionada**, para cumplir el **Acuerdo de Wassenaar** de control de exportación. Segundo, y más grave para esta oferta, la divulgación de **agosto de 2025** (**2TETRA:2BURST**, Black Hat USA, 7 de agosto) demostró con la **CVE-2025-52943** que, en redes **multicifrado**, **soportar TEA1 junto a otros algoritmos permite recuperar también la clave de los demás**: mantener TEA2 «por compatibilidad» con TEA1 activo **no salva nada**. La exigencia concreta del pliego debe ser **prohibir expresamente TEA1** —no desaconsejarlo— y exigir **capacidad de migración a TEA set B (TEA5, TEA6 y TEA7) y al conjunto de autenticación TAA2** en los terminales que se adquieran. Se valorará mencionar que **TEA5 y TEA6 usan claves de 192 bits** y que **TEA7, el civil, conserva una reducción efectiva a 56 bits** por el mismo régimen de exportación.
- **C2**: (§4.3.1, §4.3.2) **SC2 cifra con clave estática (SCK) precargada y no exige autenticación**: la misma clave para todos y durante mucho tiempo. Debe exigirse **SC3**, que emplea **clave derivada (DCK) más clave común (CCK)** y **requiere autenticación**, preferiblemente **mutua**. La relación entre ambas cosas es el núcleo de la respuesta: **la DCK se deriva del propio proceso de autenticación**, de modo que **una red que no autentica no puede usar claves derivadas** y queda condenada a la clave estática. Además, la **autenticación mutua** es la defensa frente a una **estación base falsa**. La ausencia de **OTAR** es igualmente inaceptable: renovar claves recogiendo 1.200 terminales una vez al año hace **inviable** reaccionar ante un compromiso de clave o ante la baja de un usuario, y contradice cualquier plan de gestión del ciclo de vida del material criptográfico. Debe exigirse **OTAR** y un **procedimiento documentado de inhabilitación remota** (*stun* y *kill*) para terminales perdidos o robados.
- **C3**: (§4.3.2, §4.3.3) La afirmación es **falsa**. El **cifrado de interfaz aire (AIE)** protege el tramo **terminal ↔ estación base** y **se descifra en la estación base**; a partir de ahí la comunicación circula por la infraestructura **en claro**, salvo cifrado adicional. Por tanto **no protege frente al operador de la red, frente al personal técnico con acceso a los equipos o a las grabaciones, ni frente a un compromiso de la infraestructura o de los enlaces de transporte**. El **cifrado extremo a extremo (E2EE)** cifra **en el terminal emisor y descifra en el receptor**, atravesando la red sin que ésta pueda leerlo; son **complementarios**, no alternativos. Si se implanta, **no basta con exigir «cifrado extremo a extremo»**: la **CVE-2025-52941** identificó una **variante debilitada de AES-128 con entropía efectiva reducida a 56 bits**, la **CVE-2025-52940** describió **repetición e inyección de voz** y la **CVE-2025-52942**, la **falta de protección antirrepetición en los SDS**. Hay que exigir, por tanto: **algoritmo y longitud de clave nombrados**, **protección frente a repetición**, **autenticación del contenido** y **derecho de auditoría de la implementación**. Debe advertirse también del coste honesto del E2EE: inutiliza las pasarelas telefónicas, la grabación centralizada en claro y la interconexión, salvo que se prevean puntos de descifrado autorizados.
- **C4**: (§5.2) Respaldo normativo en el **RD 311/2022 (ENS)**: **`mp.com.2`** (protección de la **confidencialidad**) y **`mp.com.3`** (protección de la **integridad y de la autenticidad**) amparan la exigencia de cifrado y autenticación del interfaz aire; **`mp.si.2`** (**criptografía**) y **`op.exp.10`** (**protección de claves criptográficas**) amparan la exigencia de OTAR y de una gestión de claves con ciclo de vida; y **`mp.com.4`** (**separación de flujos de información en la red**) **prohíbe** conectar las consolas al segmento ofimático: su requisito **`mp.com.4.2`** establece que «**si se emplean comunicaciones inalámbricas, será en un segmento separado**», y al estar el sistema categorizado **MEDIA** la medida exige además **[R1 o R2 o R3]**, es decir, segmentación lógica con **VLAN**, con **VPN** o con **medios físicos separados** —obsérvese que en categoría **BÁSICA** esta medida **no aplicaría**—. Se valorará mencionar `mp.com.1` (perímetro seguro) y `mp.eq.4` (otros dispositivos conectados a la red).

### Criterios de evaluación

| Cuestión | Elemento | Puntos |
|---|---|---|
| 1 | Identificar la reducción de clave de **TEA1** (CVE-2022-24402) y su origen en Wassenaar | 1,0 |
| 1 | Señalar que **soportar TEA1 compromete a los demás algoritmos** (CVE-2025-52943) | 1,0 |
| 1 | Exigencia de pliego: prohibir TEA1 y exigir migración a **TEA set B / TAA2** | 1,0 |
| 2 | Rechazar SC2 y exigir **SC3** con autenticación mutua | 1,0 |
| 2 | Explicar que la **DCK se deriva de la autenticación** | 1,0 |
| 2 | Exigir **OTAR** e inhabilitación remota, con justificación operativa | 1,0 |
| 3 | Distinguir con precisión **AIE** (se descifra en la BS) de **E2EE** | 1,0 |
| 3 | Exigencias concretas de E2EE y mención de los hallazgos de 2025 | 1,0 |
| 4 | Citar `mp.com.2`, `mp.com.3`, `mp.si.2` y `op.exp.10` | 1,0 |
| 4 | Citar `mp.com.4` con su requisito `.2` y el refuerzo exigible en categoría MEDIA | 1,0 |
| | **Total** | **10** |

---

## Caso 3 — Renovación del título habilitante y decisión de evolución

### Enunciado

El Área de Gobierno competente en seguridad y emergencias plantea a la unidad TIC tres asuntos que llegan a la vez:

1. **Vence el título habilitante** que ampara el uso de las frecuencias de la red municipal y hay que tramitar su renovación. Un informe interno afirma que «el Ayuntamiento tiene concedidas esas frecuencias a perpetuidad por su condición de Administración pública».
2. Se quiere **ampliar la red** para dar servicio también a los **servicios de limpieza viaria y de parques y jardines**, y se propone hacerlo «en la banda de emergencias, que es la nuestra».
3. Un proveedor propone **sustituir íntegramente la red TETRA por teléfonos móviles comerciales con una aplicación de *push-to-talk***, argumentando que «da mejor cobertura, más caudal y cuesta menos».

Además, se recuerda que durante el **apagón del 28 de abril de 2025** la red municipal de radio **siguió operativa** mientras otros servicios se degradaban.

### Cuestiones

**Cuestión 1 — Régimen jurídico del espectro (3 puntos).** Corrija la afirmación del informe interno. Determine la modalidad de uso, el título habilitante que corresponde, su fundamento legal exacto y su duración.

**Cuestión 2 — Elección de banda (2 puntos).** Valore la propuesta de dar servicio a limpieza y a parques en la banda de emergencias. Indique qué notas del CNAF resuelven la cuestión y qué banda correspondería.

**Cuestión 3 — Sustitución por telefonía comercial (3 puntos).** Elabore la respuesta técnica a la propuesta del proveedor, con al menos cinco argumentos, y sitúe el episodio del apagón en el razonamiento.

**Cuestión 4 — Evolución realista (2 puntos).** Proponga la vía de evolución que sí es defendible, citando los estándares aplicables y el espectro que la normativa española tiene reservado para ello.

### Solución orientativa

- **C1**: (§5.2) La afirmación es **incorrecta en los dos extremos**. El **espectro radioeléctrico es un bien de dominio público cuya titularidad y administración corresponden al Estado** (**art. 85.1** de la Ley 11/2022): el Ayuntamiento **no tiene concedidas** frecuencias, sino **derecho de uso** sometido a título habilitante. La modalidad es **uso privativo** (art. 88.1: explotación en exclusiva o por un número limitado de usuarios de determinadas frecuencias en un mismo ámbito físico) en régimen de **autoprestación**. El título habilitante que corresponde es la **afectación demanial**, conforme al **art. 88.5.b)**, que otorga el uso privativo para autoprestación mediante autorización individual «**salvo en el caso de Administraciones públicas, que requerirán de afectación demanial**»; **no** cabe la **concesión**, que además exigiría **ostentar la condición de operador de comunicaciones electrónicas** (art. 88.6). Y **no es a perpetuidad**: el **art. 94.1** fija que los derechos de uso privativo sin limitación de número se otorgan «hasta el **31 de diciembre del año natural en que cumplan su quinto año de vigencia**», **renovables por períodos de cinco años**. Deben citarse también las **condiciones asociadas** del art. 91 (uso eficaz y eficiente, características técnicas, no interferencia, exposición radioeléctrica) y la **tasa por reserva del dominio público radioeléctrico**.
- **C2**: (§3.1) La propuesta **no encaja**. La **nota UN-28** del CNAF reserva las subbandas **380-385 y 390-395 MHz** —excepción a la reserva de la banda 235-399,9 MHz al Ministerio de Defensa— a «**redes de servicios de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y redes de servicios de emergencia**», de conformidad con la Decisión CEPT **ECC/DEC(08)05**. Un servicio de **limpieza viaria** o de **parques y jardines** no es ninguna de las dos cosas. La banda que corresponde es la de la **nota UN-31**: las subbandas **410-415,3 y 420-425,3 MHz**, que el CNAF destina a «**sistemas digitales de acceso aleatorio de canales (TETRA y otros)**» con **canalización de 25 kHz** y **separación dúplex de 10 MHz**. El criterio a retener, y que la pregunta busca, es que **la banda la determina el SERVICIO, no la condición del solicitante**. Debe añadirse que el CNAF vigente es la **Orden TDF/732/2026, de 10 de julio**, que sustituyó a la Orden ETD/1449/2021 con efectos de **18 de julio de 2026**, y que la propia nota UN-28 exige un **plan exhaustivo de reutilización** por la saturación de la banda en entornos urbanos densos.
- **C3**: (§5.1, §5.3) La sustitución **no es defensible**, y los argumentos son al menos estos seis: **(1) Prioridad.** En una red comercial el Ayuntamiento **no decide a quién se desaloja**; TETRA ofrece prioridad de acceso, **prioridad con desalojo** y llamada de emergencia gobernadas por el titular de la red. **(2) Modo directo.** Un teléfono móvil **no puede** comunicarse con otro si cae la red; el **DMO** de TETRA sí, y es innegociable para bomberos y equipos de rescate. **(3) Inmediatez.** Establecimiento de llamada de grupo por debajo de **300 ms**, frente a segundos. **(4) Disponibilidad y control.** El titular decide dónde pone las estaciones base, cuánta batería instala y qué solapamiento de cobertura mantiene; con una red comercial se depende del respaldo de un tercero. **(5) Comunicación de grupo nativa**, con afiliación, DGNA y entrada tardía, frente a grupos de mensajería o multiconferencias de establecimiento lento. **(6) Terminal de trabajo**, con PTT, botón de emergencia, detección de «hombre caído», robustez y autonomía de jornada. El **apagón del 28 de abril de 2025** es la evidencia empírica que cierra el argumento: la red TETRA **siguió operativa** gracias al **respaldo energético de los emplazamientos** —baterías en los repetidores— mientras la telefonía convencional se degradaba, hasta el punto de que la Comunidad de Madrid, tras analizarlo, dotó en **mayo de 2026** de un terminal TETRA a **53 municipios pequeños** para garantizar su contacto con el 112. Se valorará que se enuncie la lección de fondo: **un servicio crítico solo es resiliente si lo son todas sus dependencias, empezando por la energía**, y que ello está respaldado por la medida **`mp.if.4`** del ENS.
- **C4**: (§5.4) La vía defendible es la **coexistencia por fases**, no la sustitución. Dos caminos complementarios: **(a) TEDS**, la aportación de datos de **TETRA Release 2** (**TR 102 580**), con anchos de canal de **25, 50, 100 y 150 kHz** y modulaciones **π/8-D8PSK, 4-QAM, 16-QAM y 64-QAM** con adaptación al enlace, que amplía la capacidad **manteniendo la misma red**, aunque exige más espectro por canal en una banda ya saturada; y **(b) la banda ancha crítica** del **3GPP**: **MCPTT**, normalizado en la **Release 13** culminada en **2016** (**TS 22.179**), más **MCVideo** y **MCData** de la Release 14, apoyados en **GCSE**, **eMBMS** y **ProSe**. El modelo operativo sería el que ya se aplica de hecho: **TETRA para la voz crítica y los datos cortos garantizados**, y **banda ancha para lo que necesita caudal** (vídeo, cartografía, imagen médica), con **terminales híbridos** e **interconexión en el centro de mando**. Y el dato que remata la respuesta: el **CNAF ya tiene reservado el espectro** para ello — **733-736 / 788-791 MHz** para el sistema PPDR de **ámbito nacional** y **698-703 / 753-758 MHz** para las redes de **ámbito autonómico y local**, además de **452-457,5 / 462-467,5 MHz** en aplicación de la Decisión **ECC/DEC(16)02**. Es decir: **el recurso está apartado; lo que está pendiente es la decisión**. Se valorará citar el precedente del **SIRDEE**, que desde julio de 2024 pilota su migración a **LTE manteniendo la red de banda estrecha** durante la transición.

### Criterios de evaluación

| Cuestión | Elemento | Puntos |
|---|---|---|
| 1 | Corregir la idea de «frecuencias concedidas»: dominio público estatal (art. 85.1) | 0,75 |
| 1 | Identificar **uso privativo en autoprestación** | 0,75 |
| 1 | Identificar la **afectación demanial** y citar el **art. 88.5.b)** | 1,0 |
| 1 | Duración del art. 94.1 (cinco años, renovables) | 0,5 |
| 2 | Descartar la banda de emergencias citando la **nota UN-28** | 1,0 |
| 2 | Proponer 410-415,3 / 420-425,3 MHz citando la **nota UN-31**, con 25 kHz y dúplex de 10 MHz | 1,0 |
| 3 | Aportar al menos cinco argumentos técnicos sólidos | 2,0 |
| 3 | Usar el apagón del 28-4-2025 como evidencia y enunciar la lección sobre dependencias | 1,0 |
| 4 | Describir **TEDS** con sus anchos de canal y modulaciones | 0,75 |
| 4 | Citar **MCPTT / Release 13 / TS 22.179** y el modelo de coexistencia | 0,75 |
| 4 | Citar el espectro PPDR reservado, distinguiendo el bloque **autonómico y local** | 0,5 |
| | **Total** | **10** |
