# Tema 38 — Contenido Teórico

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
>
> **Bloque**: Parte II — Técnico
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha generación**: 2026-08-27
> **Fuentes**: Ver tema-38-fuentes.md · **Diagramas**: Ver tema-38-diagramas.md · **Cambios**: Ver tema-38-changelog.md
>
> *Extensión: ~20.000 palabras · 18 diagramas SVG embebidos · 4 tipos de callout transversales*

---

## Convenciones del documento

Este tema incluye cuatro tipos de **cajas callout** para facilitar el estudio:

> **[DATO CLAVE EXAMEN]** Información de alta densidad memorística, con alta probabilidad de aparecer en el test oficial: cifras de la capa física, siglas, números de norma, bandas de frecuencia y preceptos legales.

> **[EJERCICIO RESUELTO]** Problema con solución paso a paso: calcular una capacidad, dimensionar una cobertura, decidir un modo de operación, leer una tabla del CNAF.

> **[EJEMPLO AYTO MADRID]** Aplicación real de la teoría al entorno municipal (la red DIMETRA-TETRA del Ayuntamiento, el CISEM, la Policía Municipal, SAMUR-Protección Civil, Bomberos y el IAM).

> **[REFERENCIA CRUZADA]** Enlace conceptual a otros temas del temario oficial.

**Aviso sobre el enunciado, y conviene empezar por él.** El título oficial de este tema es el único de los cuarenta que se dedica **a un solo sistema concreto**. Los demás temas técnicos describen familias de tecnologías —sistemas operativos, bases de datos, redes locales—; aquí se pide **una tecnología con nombre propio, un fabricante de norma con nombre propio (el ETSI) y un conjunto cerrado de especificaciones**. Eso tiene dos consecuencias prácticas para quien estudia:

1. **El examen puede bajar al detalle numérico sin remordimiento.** En un tema de «redes locales» nadie pregunta el número exacto de bits de una ráfaga; en un tema de TETRA sí se pregunta cuántos intervalos hay por portadora, cuánto dura una multitrama o qué banda reserva el CNAF a los servicios de emergencia. **Este es un tema de datos exactos.**
2. **El enunciado incluye la traducción de las siglas y lo hace mal a propósito.** Dice «*Trans European Trunked Radio* **o** *TErrestrial Trunked RAdio*» porque **ambas expansiones han sido oficiales en momentos distintos**, y saber cuál es la vigente y por qué cambió es, en sí mismo, materia de pregunta. Se explica en §1.3.

**Fronteras con otros temas.** TETRA toca materias que el temario reparte en otros enunciados. El criterio seguido aquí es el siguiente:

| Materia | Dónde se estudia | Qué se hace en este tema |
|---|---|---|
| Medios de transmisión, modos de comunicación, comunicaciones móviles e inalámbricas en general | **Tema 33** | Se da por sabido. Aquí se aplica a un sistema concreto |
| Modelo OSI y pila TCP/IP | **Tema 34** | Solo se usa para situar las tres capas del interfaz aire de TETRA y el transporte de datos IP |
| Redes locales, tipología, técnicas de transmisión y métodos de acceso | **Tema 37** | El **acceso múltiple** (FDMA, TDMA) se explica aquí en lo que TETRA lo usa, no como teoría general |
| Seguridad perimetral, acceso remoto seguro y VPN | **Tema 36** | Aquí solo la seguridad **propia del interfaz aire** de TETRA y el cifrado extremo a extremo |
| Criptografía, firma electrónica y amenazas | **Tema 32** | Se dan por sabidos los conceptos de clave simétrica, autenticación y AES |
| Principios del ENS y del ENI | **Tema 39** | Aquí se citan las medidas concretas que un servicio de radio crítico debe cumplir |
| Videoconferencia y trabajo en grupo | **Tema 40** | Fuera de alcance |

**Y la advertencia que más puntos cuesta.** La red de radiocomunicaciones de emergencia **del Estado español**, el **SIRDEE**, **no es una red TETRA**: está construida sobre **TETRAPOL**, una tecnología distinta, propietaria en su origen, de acceso **FDMA** y canalización de **12,5 kHz**. Quien confunda ambas cosas responderá mal cualquier pregunta que cruce «TETRA» con «Fuerzas y Cuerpos de Seguridad del Estado». Se desarrolla en §5.1, y la comparación técnica está en §3.2.

Las fuentes se citan con etiquetas breves tipo `[EN392-2]`, `[CNAF]` o `[ENS]`; el registro completo está en `tema-38-fuentes.md`. **Las bandas de frecuencia y los preceptos legales de este tema se han verificado sobre el PDF del BOE**, no sobre fuentes secundarias, y de esa verificación salió un dato que casi ningún material recoge todavía: **el Cuadro Nacional de Atribución de Frecuencias vigente ya no es el de 2021**.

**Caso de referencia usado en todo el tema** (contexto Ayuntamiento de Madrid, supuesto simplificado): la **red DIMETRA-TETRA municipal**, gobernada desde el **Centro Integrado de Seguridad y Emergencias (CISEM)** de la calle Rufino Blanco, que da servicio a Policía Municipal, Bomberos, SAMUR-Protección Civil, Agentes de Movilidad, SAMUR Social y Parques y Jardines. Ese sistema único concentra todas las materias del tema: tiene **estaciones base y una infraestructura de conmutación** (§2), ocupa **espectro atribuido por el CNAF** (§3.1 y §5.2), transporta **voz de grupo y datos** (§4.1 y §4.2), está **cifrado y autenticado** (§4.3), debe **seguir funcionando cuando todo lo demás falla** (§5.3) y tiene por delante una **transición hacia la banda ancha crítica** (§5.4).

---
## 1. Introducción y fundamentos de los sistemas móviles de radiocomunicación

### 1.1. Concepto y evolución de la radiocomunicación móvil privada (PMR)

**Qué es la PMR y en qué se diferencia de un teléfono móvil.** La **radiocomunicación móvil privada** —**PMR**, del inglés *Private Mobile Radio*, también llamada *Professional Mobile Radio* y, en Estados Unidos, *Land Mobile Radio* (**LMR**)— es el conjunto de sistemas de radio diseñados para que **un colectivo cerrado de usuarios profesionales** se comunique entre sí, normalmente **en grupo**, sobre una red **propia** o dedicada. La diferencia con la telefonía celular pública no es de tecnología sino de **finalidad**, y de ella se derivan todas las decisiones de diseño:

- **La unidad de comunicación es el grupo, no el par.** En telefonía, lo natural es que A llame a B. En PMR, lo natural es que un agente hable **a todos los que están en su grupo** —una patrulla, una dotación de bomberos, el turno de una oficina—, que escuchan simultáneamente. La llamada individual existe, pero es la excepción.
- **La comunicación es *push-to-talk* y semidúplex.** Se aprieta un botón, se habla y se suelta; mientras uno habla, los demás escuchan. Esto no es una limitación: es lo que permite que un mando **oiga a todos sus efectivos** y que todos oigan lo que se ordena.
- **El establecimiento debe ser inmediato.** En una emergencia, esperar cinco segundos a que se establezca una llamada es inaceptable. El objetivo de diseño es **menos de 300 milisegundos**.
- **La red es propia y su disponibilidad es un requisito, no una expectativa.** El operador de una red PMR decide dónde pone las estaciones base, cuánta batería les instala y a quién da prioridad. Una red pública no ofrece ninguna de esas tres cosas.
- **El terminal es un instrumento de trabajo, no un objeto de consumo.** Robusto, con botón de emergencia, manejable con guantes, con autonomía de una jornada larga y audible en un entorno ruidoso.

> **[DATO CLAVE EXAMEN]** Las cuatro diferencias que definen la PMR frente a la telefonía celular pública: **(1) comunicación de grupo** como modo principal, **(2)** *push-to-talk* **semidúplex**, **(3) establecimiento de llamada inferior a 300 ms** y **(4) red propia con disponibilidad y prioridad garantizadas por su titular**. A ellas se añade una quinta, propia de los sistemas digitales modernos: **(5) funcionamiento sin infraestructura** (modo directo), imposible en telefonía celular.

**Las cuatro generaciones de la PMR.** La evolución de estos sistemas se cuenta bien en cuatro etapas, y cada una resuelve el problema que la anterior dejaba abierto.

**Primera etapa: la radio analógica convencional (desde los años treinta).** Cada colectivo tiene asignado **un canal fijo**, es decir, una pareja de frecuencias. Todos los equipos del colectivo están sintonizados en él permanentemente. La modulación es **analógica** —AM primero, **FM** después— y el sistema es de una sencillez absoluta: si el canal está libre, se habla; si está ocupado, se espera. Las limitaciones son igual de evidentes: **el canal está asignado aunque nadie hable** (el espectro se desperdicia), **no hay privacidad** (cualquiera con un receptor escucha), **no hay identificación** del que habla más allá de su voz y **no hay forma de hablar con otro colectivo** que esté en otro canal.

**Segunda etapa: el *trunking* analógico (años setenta y ochenta).** Se introduce la idea que da nombre al tema y que se explica en §1.2: en lugar de asignar un canal fijo a cada grupo, se crea una **bolsa común de canales** que el sistema reparte dinámicamente entre todos los grupos según quien vaya necesitando hablar. Aparecen sistemas como **MPT-1327**, norma británica que se difundió por Europa. Se gana muchísima eficiencia espectral, pero la voz sigue siendo analógica, con sus mismos problemas de calidad, privacidad e integración con datos.

**Tercera etapa: el *trunking* digital (años noventa).** La voz se **digitaliza** con un códec de baja tasa, y con ella llegan tres cosas que la radio analógica no podía dar: **cifrado real**, **integración de voz y datos** en la misma portadora y **mayor eficiencia espectral** —varios canales de conversación en el mismo ancho de banda—. Es la etapa en la que nacen **TETRA** en Europa (ETSI), **TETRAPOL** en Francia y **APCO Project 25 (P25)** en Estados Unidos, y algo más tarde **DMR** (*Digital Mobile Radio*), también del ETSI, para el segmento profesional de menor exigencia.

**Cuarta etapa: la banda ancha crítica (desde 2016).** Las funciones de misión crítica —el *push-to-talk* de grupo, la prioridad, el desalojo, el modo directo— se llevan a redes de **banda ancha** basadas en LTE y 5G mediante los estándares **MCPTT**, **MCData** y **MCVideo** del **3GPP**. No sustituyen a TETRA de un día para otro: conviven con él durante años. Se desarrolla en §5.4.

> **[DATO CLAVE EXAMEN]** Secuencia de las cuatro etapas de la PMR: **analógica convencional → *trunking* analógico (MPT-1327) → *trunking* digital (TETRA, TETRAPOL, P25, DMR) → banda ancha crítica (MCPTT del 3GPP)**. TETRA pertenece a la **tercera**. Una pregunta frecuente pide situar TETRA en esta escala o identificar el sistema **analógico** de la segunda: es **MPT-1327**, no TETRA.

**Un matiz de vocabulario que se pregunta.** Junto a **PMR** aparece **PAMR** (*Public Access Mobile Radio*): es la misma tecnología, pero explotada por **un operador comercial** que vende el servicio a terceros, en lugar de por el propio colectivo usuario. La distinción es jurídica más que técnica y tiene consecuencias directas en el título habilitante que hace falta para usar el espectro (§5.2). En el CNAF español ambas aparecen juntas, como «**sistemas móviles digitales de banda estrecha PMR/PAMR**» `[CNAF]`.

> **[REFERENCIA CRUZADA]** El **Tema 33** («Comunicaciones… comunicaciones móviles e inalámbricas») presenta el panorama general de los sistemas móviles, incluida la telefonía celular. Este tema **no repite** esa panorámica: entra directamente en el sistema que el enunciado nombra. Los conceptos de modulación digital y de multiplexación que aquí se dan por conocidos están en el **Tema 33**; los de capa física y capa de enlace, en el **Tema 34**.

**Dónde se usa hoy la PMR digital.** Conviene tener presente el mapa de usuarios, porque explica por qué el estándar tiene las funciones que tiene: **seguridad pública** (policía, bomberos, emergencias sanitarias, protección civil), **transporte** (metros, ferrocarriles, aeropuertos, puertos, autobuses urbanos, taxis), **energía y agua** (redes eléctricas, gasistas, empresas de abastecimiento), **industria** (minería, petroquímica, grandes plantas), **defensa** y **grandes eventos y recintos** (estadios, ferias, hospitales, centros comerciales). Según la **TCCA**, TETRA está desplegado en **más de 124 países** `[TCCA-GLOBAL]`.

### 1.2. Sistemas *trunked* o troncalizados: concepto y ventajas

**El problema que resuelve.** Imaginemos un ayuntamiento con **ocho colectivos** que necesitan radio: policía, bomberos, emergencias sanitarias, movilidad, limpieza, parques, obras y transporte. En un sistema **convencional**, a cada colectivo se le asigna **un canal fijo**: hacen falta ocho canales, y cada canal solo puede usarlo su colectivo. El resultado es doblemente malo: cuando el canal de la policía está saturado, el agente espera **aunque siete canales estén vacíos**; y cuando el canal de parques lleva dos horas en silencio, ese espectro está **inmovilizado** sin que nadie pueda aprovecharlo.

**La solución.** Un sistema **troncalizado** (*trunked*) mantiene los ocho canales, pero **no los asigna a nadie de forma permanente**. Los reúne en una **bolsa común** y los reparte **conversación a conversación**: cuando un agente aprieta el botón, un **canal de control** —una portadora que el sistema dedica exclusivamente a señalización— recibe la petición, comprueba a qué grupo pertenece el usuario, busca un canal de tráfico libre y **se lo asigna solo mientras dura esa transmisión**. Al soltar el botón, el canal **vuelve a la bolsa**.

> **[DATO CLAVE EXAMEN]** *Trunking* significa **asignación dinámica de canales bajo demanda desde una bolsa común**, gestionada por un **canal de control** dedicado. La palabra procede de la telefonía: un *trunk* es una **línea troncal** compartida entre muchos abonados. La traducción española normalizada es **«troncalización»** o «concentración de enlaces»; el CNAF usa la expresión «sistemas multicanales de **acceso aleatorio de frecuencias con concentración de enlaces (*trunking*)**» `[CNAF]`.

**Por qué funciona: el efecto de agrupamiento.** La ganancia no es una cuestión de mera comodidad, sino de **teoría de colas**. Un conjunto de recursos compartidos atiende mucha más demanda que la suma de recursos aislados equivalentes, porque los picos de unos coinciden con los valles de otros. Es el mismo principio por el que una cola única ante diez cajeros es más eficiente que diez colas de un cajero cada una. Aplicado a la radio, **ocho canales compartidos entre ocho colectivos dan un grado de servicio muy superior al de un canal dedicado por colectivo**, y permiten atender a **muchos más usuarios** con el mismo espectro.

> **[EJERCICIO RESUELTO]** **Comparar la capacidad de un despliegue convencional y uno troncalizado.**
>
> Un servicio municipal dispone de **4 portadoras** de 25 kHz en una zona. En **TETRA**, cada portadora se divide en **4 intervalos de tiempo**, de modo que ofrece **4 canales físicos**. La configuración estándar dedica **un intervalo al canal de control principal**.
>
> **Planteamiento convencional analógico**: 4 portadoras = **4 canales de voz**, cada uno asignado en exclusiva a un colectivo. Cuatro colectivos servidos, y ninguno puede usar el canal de otro.
>
> **Planteamiento troncalizado TETRA**: 4 portadoras × 4 intervalos = **16 canales físicos**; se resta **1** para el canal de control → **15 canales de tráfico simultáneos**, repartidos dinámicamente entre **todos** los colectivos y todos los grupos de conversación que se definan.
>
> **Resultado**: con el mismo espectro se pasa de **4 conversaciones simultáneas rígidas** a **15 conversaciones simultáneas flexibles**, casi **cuatro veces más**, y además el número de **grupos** que pueden definirse no está limitado por el número de canales: pueden existir decenas o centenares de grupos de conversación, porque un grupo **solo consume canal mientras alguien habla**. Esa última frase es la clave del modelo y la que más se pregunta.

**Las ventajas del *trunking*, ordenadas.** Conviene memorizarlas como lista cerrada:

1. **Eficiencia espectral**: se sirve a muchos más usuarios con el mismo número de frecuencias.
2. **Reducción del tiempo de espera**: la probabilidad de encontrar todos los canales ocupados baja drásticamente respecto al canal dedicado.
3. **Número de grupos ilimitado en la práctica**: los grupos son una **entidad lógica** del sistema, no una frecuencia física.
4. **Reconfiguración desde el centro de control**: se pueden crear, modificar o disolver grupos **en caliente** (la función **DGNA**, §4.1.1), algo imposible en radio convencional, donde habría que reprogramar cada equipo.
5. **Gestión de prioridades**: el sistema sabe quién pide el canal y puede **desalojar** a un usuario de menor prioridad para atender una emergencia (§4.1.2).
6. **Privacidad y control de acceso**: cada terminal se identifica ante el sistema; el que no está dado de alta no entra.
7. **Registro y trazabilidad**: toda transmisión queda asociada a una identidad y puede grabarse y auditarse.
8. **Integración de voz y datos** sobre la misma infraestructura.

**Y los inconvenientes, que también se preguntan.** El *trunking* introduce **dependencia de la infraestructura**: si cae el canal de control, o cae el nodo de conmutación, el sistema deja de asignar canales. Por eso todos los sistemas troncalizados serios incorporan **modos degradados**: el **repliegue local** (*fallback* o *local site trunking*), en el que una estación base aislada del resto de la red sigue dando servicio troncalizado **dentro de su propia célula**, y el **modo directo** (§2.2.2), en el que los terminales hablan entre sí **sin ninguna infraestructura**. También añade **complejidad y coste**: un sistema troncalizado necesita conmutación, gestión de abonados, canal de control y planificación, frente a la simplicidad de un repetidor convencional.

> **[EJEMPLO AYTO MADRID]** La red municipal es el ejemplo de manual de esta ventaja. Sobre **una única infraestructura**, el Ayuntamiento sirve a colectivos con necesidades muy distintas —**Policía Municipal**, **Bomberos**, **SAMUR-Protección Civil**, **Agentes de Movilidad**, **SAMUR Social** y **Parques y Jardines**— y a **más de 3.000 efectivos** `[TELEFONICA-2026]`. En un esquema convencional habrían hecho falta seis redes separadas, seis conjuntos de frecuencias y ninguna posibilidad de que un bombero y un sanitario hablaran entre sí en una intervención conjunta. Con troncalización, todos comparten los mismos canales físicos y el CISEM puede **crear sobre la marcha un grupo mixto** para una emergencia concreta.

### 1.3. Estandarización de TETRA por el ETSI: *Trans European* / *Terrestrial Trunked Radio*

**Quién hace la norma.** **TETRA es un estándar abierto del ETSI**, el *European Telecommunications Standards Institute*, el organismo europeo de normalización de las telecomunicaciones, con sede en Sophia Antipolis (Francia). El trabajo arrancó a finales de los años ochenta dentro de un comité técnico específico, y las primeras normas se publicaron en **1995**, con el despliegue comercial iniciándose a partir de **1997**.

**Lo que significa que sea «abierto», y por qué importa.** Un estándar abierto del ETSI define **interfaces**, no productos. Cualquier fabricante puede implementar la norma, y los equipos de fabricantes distintos deben entenderse. Esa es la diferencia decisiva frente a **TETRAPOL**, que nació como desarrollo **propietario** de una empresa francesa —hoy integrada en Airbus— y que solo más tarde se documentó públicamente. Para una Administración, la consecuencia es directa y muy citable en un pliego: con un estándar abierto **no queda cautiva de un proveedor**, puede licitar terminales e infraestructura por separado y puede sustituir un fabricante por otro. Para que esa promesa sea real, el ETSI publica además una norma de **pruebas de conformidad**, la **EN 300 394** `[EN394]`, y la industria organiza pruebas de interoperabilidad entre fabricantes.

> **[DATO CLAVE EXAMEN]** **TETRA = estándar abierto del ETSI. TETRAPOL = tecnología de origen propietario (Matra/EADS, hoy Airbus).** Es la diferencia que más se pregunta después de la del acceso al medio (TDMA frente a FDMA). El resto de sistemas: **P25** es norma de la **APCO** estadounidense; **DMR** es también del **ETSI**, pero orientado al segmento profesional de menor exigencia.

**Las dos expansiones de las siglas.** El enunciado oficial del tema recoge las dos, y esa duplicidad tiene una explicación histórica precisa:

- La denominación original fue **Trans European Trunked Radio**, «radio troncal transeuropea», coherente con un proyecto concebido para dar a Europa un sistema **común** de radio profesional, del mismo modo que el GSM le había dado un sistema común de telefonía móvil.
- Cuando el estándar empezó a adoptarse **fuera de Europa** —hoy, más de 124 países `[TCCA-GLOBAL]`—, el adjetivo «transeuropeo» dejó de tener sentido, y el ETSI pasó a expandir las siglas como **TErrestrial TRunked RAdio**, «radio troncal terrestre». El acrónimo se conservó; cambió lo que significa.

> **[DATO CLAVE EXAMEN]** **La expansión vigente es *TErrestrial Trunked RAdio*.** *Trans European Trunked Radio* es la **histórica**, y se abandonó por la difusión mundial del estándar. El adjetivo «terrestre» tiene además un valor descriptivo: distingue estos sistemas de los **móviles por satélite**. Una pregunta habitual pide la expansión correcta o el motivo del cambio.

**La familia de normas, que hay que saber nombrar.** El estándar no es un documento, sino una **serie**. Las piezas que se preguntan son estas:

| Serie | Contenido | Observaciones |
|---|---|---|
| **EN 300 392** | **TETRA V+D** (*Voice plus Data*): el modo troncalizado completo | Es el núcleo. La **parte 1** es el diseño general de red; la **parte 2**, el **interfaz aire**; la **parte 3**, la **ISI**; la **parte 4**, las pasarelas a PSTN/RDSI; la **parte 5**, el **PEI**; la **parte 7**, la **seguridad**; las partes 9 a 12, los **servicios suplementarios** |
| **EN 300 396** | **TETRA DMO** (*Direct Mode Operation*): el modo directo | Incluye el **repetidor DM-REP** y la **pasarela DM-GATE** |
| **EN 300 394** | **Pruebas de conformidad** | Lo que hace verificable la interoperabilidad multifabricante |
| **EN 300 395** | **Códec de voz** | Define el **ACELP** de TETRA |
| **EN 300 812** | **Módulo de identidad (SIM) de TETRA** | Equivalente funcional de la SIM de GSM |
| **TR 102 580** | **TEDS**, el servicio de datos mejorado de **TETRA Release 2** | Guía del diseñador de la alta velocidad de datos |
| **TS 104 053** | **Especificación de los algoritmos de cifrado** del interfaz aire | Su **parte 1** publicó en **febrero de 2025** el **TEA set A**, hasta entonces confidencial (§4.3.2) |

> **[DATO CLAVE EXAMEN]** Las dos series que hay que distinguir sin dudar: **EN 300 392 = V+D, modo troncalizado**; **EN 300 396 = DMO, modo directo**. Y dentro de la primera, las dos partes más citadas: **la parte 2 (interfaz aire)** y **la parte 7 (seguridad)**.

**Las dos *releases* del estándar.** TETRA se estructura en dos grandes revisiones funcionales:

- **TETRA Release 1** (la original, de 1995 en adelante) define **V+D**, el **modo directo**, los servicios suplementarios, la seguridad y los datos de baja velocidad. Es lo que está desplegado en la práctica totalidad de las redes en servicio, incluida la del Ayuntamiento de Madrid.
- **TETRA Release 2** (a partir de 2005-2007) añade tres bloques: **TEDS** (*TETRA Enhanced Data Service*), que multiplica la capacidad de datos con canales más anchos y modulaciones de orden superior; **códecs de voz mejorados** (AMR y códecs de banda ancha); y **mejoras de alcance**, para superar el límite de **58 km** de radio de célula heredado de la estructura de intervalos de la Release 1. Se desarrolla en §5.4.

> **[EJEMPLO AYTO MADRID]** Que TETRA sea un estándar abierto tiene una consecuencia contractual muy concreta en Madrid. La red municipal está construida sobre la plataforma **DIMETRA**, la implementación de TETRA de un fabricante, pero **el mantenimiento y la evolución del sistema se licitan como servicio**: en marzo de 2026, el Ayuntamiento adjudicó a Telefónica Soluciones el **mantenimiento integral y la evolución tecnológica de la infraestructura DIMETRA-TETRA**, por **cinco años**, con **disponibilidad 24×7** y una arquitectura que unifica el despacho y la grabación de las comunicaciones en una plataforma de alta disponibilidad `[TELEFONICA-2026]`. La norma abierta es lo que permite que el titular de la red y el operador del servicio sean entidades distintas, y que el segundo pueda cambiar sin cambiar la primera.

> **[REFERENCIA CRUZADA]** La lógica de la **normalización abierta frente a la solución propietaria** y sus efectos sobre la contratación pública aparece también en el **Tema 39**, a propósito del principio de **neutralidad tecnológica** del Esquema Nacional de Interoperabilidad, y en el **Tema 31**, a propósito de la dependencia de proveedor en servicios en la nube.
---
## 2. Arquitectura y componentes de la red TETRA

**Visión de conjunto antes de entrar en detalle.** Una red TETRA tiene **tres grandes bloques** y **un conjunto de interfaces normalizadas** que los unen:

1. La **SwMI** (*Switching and Management Infrastructure*), es decir, **toda la infraestructura fija**: estaciones base, nodos de conmutación, registros de abonados, gestión de red y despacho. Desde el punto de vista del terminal, **la SwMI es «la red»**.
2. Los **terminales de usuario** o **estaciones móviles** (**MS**, *Mobile Station*), en sus distintos formatos, más los elementos que extienden su alcance (repetidores y pasarelas de modo directo).
3. Los **equipos y sistemas conectados** a la red por línea: consolas de despacho, grabadores, sistemas de gestión de flotas, pasarelas telefónicas y aplicaciones de datos.

Y los une un **modelo de interfaces** que es la clave de la interoperabilidad y que se explica en §2.3.

> **[DATO CLAVE EXAMEN]** **SwMI** = *Switching and Management Infrastructure*, la infraestructura de conmutación y gestión. Es **el término oficial del estándar** para designar todo lo que no es terminal. **MS** = *Mobile Station*, el terminal. La comunicación entre ambos se produce por el **interfaz aire (I1)**.

### 2.1. Infraestructura de conmutación y gestión (SwMI)

La SwMI no es un equipo, sino un **subsistema completo** con funciones de radio, de conmutación, de bases de datos y de gestión. El estándar define su comportamiento **hacia fuera** —cómo se comporta en el interfaz aire, en la ISI y en la interfaz de gestión— pero deja a cada fabricante la libertad de organizarla internamente. De ahí que los nombres comerciales varíen: lo que se pregunta son las **funciones**, no los productos.

#### 2.1.1. Estaciones base (BS)

**Qué es y qué hace.** La **estación base** (**BS**, *Base Station*, también llamada **TBS** o *radio site*) es el punto donde la red pasa del cable a la radio. Contiene los **transceptores** (uno por portadora), los **amplificadores**, el **sistema radiante** (antenas, cables, combinadores y filtros) y la electrónica de control que gestiona el enlace con los terminales de su **célula**.

**Sus funciones concretas en TETRA:**

- **Radiar y recibir en las portadoras asignadas**, con la estructura TDMA de cuatro intervalos que se describe en §3.
- **Mantener el canal de control principal** (*Main Control Channel*, **MCCH**), la portadora e intervalo por los que difunde continuamente la información del sistema y por los que los terminales piden recursos. Un terminal recién encendido **busca ese canal** y se sincroniza con él.
- **Difundir la información de sistema** (SYSINFO): identidad de la red, de la célula, parámetros de acceso, clase de seguridad soportada, umbrales de reselección.
- **Asignar los canales de tráfico** que le indique el nodo de conmutación y gestionar el acceso aleatorio de los terminales.
- **Aplicar el cifrado de interfaz aire** (§4.3.2): el cifrado del interfaz aire se produce **entre la estación base y el terminal**, y por tanto **es la estación base la que cifra y descifra**.
- **Gestionar la movilidad dentro de su cobertura** y participar en el **traspaso** (*handover*) hacia células vecinas.
- **Sostener el modo de repliegue** (*local site trunking*) si pierde la conexión con el resto de la red: sigue dando servicio troncalizado **a los usuarios de su célula**, aunque sin acceso a los grupos ni a los servicios que dependen del núcleo.

> **[DATO CLAVE EXAMEN]** El **canal de control principal (MCCH)** es lo que distingue a un sistema troncalizado. Se transmite en el **intervalo 1 de la portadora principal** de cada célula (la denominada *main carrier*), y es por donde se difunde la información del sistema y se cursan las peticiones de recurso. **Sin canal de control no hay troncalización**; por eso los sistemas prevén el repliegue local y el modo directo.

**Configuraciones típicas.** Una BS puede tener **una sola portadora** (4 canales físicos, de los que uno es el de control → **3 de tráfico**) o **varias**. Cada portadora adicional aporta **4 canales de tráfico** más, porque el canal de control ya está servido. En emplazamientos de mucha carga se instalan cuatro, seis u ocho portadoras.

**Planificación de la cobertura.** El emplazamiento y la potencia de las estaciones base determinan la cobertura, y en un servicio de emergencia la cobertura **no se negocia**: hay que cubrir el 100 % del territorio de responsabilidad, y no solo al aire libre. Los tres problemas clásicos son:

- **La cobertura en interiores** (*indoor*), que en una ciudad es la mayoritaria: sótanos, aparcamientos, galerías de servicio, plantas bajas de edificios con estructura metálica.
- **La cobertura en túneles y subterráneos**, que exige soluciones específicas: **cable radiante** (*leaky feeder*), repetidores dedicados o estaciones base internas.
- **La cobertura de borde y la superposición** entre células, necesaria para que el traspaso sea limpio y para que la caída de una estación base no deje un agujero.

> **[EJEMPLO AYTO MADRID]** El caso del **subsuelo** es especialmente ilustrativo en Madrid, porque hay dos redes distintas que resolver. La red **municipal** debe dar servicio a Policía Municipal, Bomberos y SAMUR en aparcamientos, galerías y estaciones; y la **Comunidad de Madrid** ha ido desplegando **TETRA en la red de Metro**, con actuaciones específicas por tramos —en 2020 se adjudicó la instalación del sistema en el tramo Paco de Lucía-Puerta de Arganda de la **línea 9**, con **5,2 millones de euros** de inversión, para comunicar el Puesto de Mando con el personal de estaciones y los conductores `[METRO]`—. Que sean dos redes distintas plantea justo el problema que resuelve la **ISI** (§2.3.2): cómo hablan entre sí.

#### 2.1.2. Nodos de conmutación y control de red

**El corazón del sistema.** Por encima de las estaciones base se sitúa el **nodo de conmutación**, que los fabricantes llaman *switch*, **MSO** (*Mobile Switching Office*), **DXT** o de otras formas, y cuyas funciones el estándar atribuye genéricamente a la SwMI. Es donde se decide **quién habla con quién**.

**Funciones principales:**

- **Conmutación de las comunicaciones**: encaminar el audio de una llamada de grupo **a todas las células donde haya miembros de ese grupo afiliados**, y solo a ésas. Este punto es más sutil de lo que parece y merece detenerse: un grupo puede tener 400 miembros repartidos por toda la ciudad, pero si en un momento dado solo hay miembros afiliados en cuatro células, **solo se ocupan canales en esas cuatro**. El resto de la red queda libre.
- **Gestión de la movilidad**: registro de los terminales, seguimiento de en qué célula está cada uno, control del **traspaso** entre células y entre nodos.
- **Bases de datos de abonados y grupos**: el registro de identidades, sus atributos, sus permisos, su prioridad y su pertenencia a grupos. Es el equivalente funcional del HLR de la telefonía móvil.
- **Autenticación y gestión de claves**: el **centro de autenticación**, que custodia las claves maestras de los terminales y ejecuta el desafío de autenticación (§4.3.1), y la infraestructura de **distribución de claves por el aire** (**OTAR**).
- **Gestión de prioridades y de desalojo**: decidir a quién se le quita el canal cuando entra una emergencia.
- **Pasarelas** hacia la red telefónica pública, hacia la centralita corporativa y hacia redes de datos.
- **Interconexión con otras redes TETRA** por la **ISI**.

> **[DATO CLAVE EXAMEN]** En una llamada de grupo, **la red solo ocupa canal de tráfico en las células donde hay miembros del grupo afiliados**. Es la razón por la que un sistema TETRA puede soportar cientos de grupos con pocas portadoras, y una de las diferencias esenciales frente a la radio convencional, donde el grupo **es** una frecuencia y ocupa el canal siempre.

**Arquitectura distribuida y redundancia.** En redes grandes hay **varios nodos de conmutación** interconectados, de forma que la caída de uno no deja sin servicio a toda la red. La topología del transporte entre nodos y estaciones base —fibra propia, radioenlaces, líneas alquiladas— es una decisión de diseño crítica: **un sistema de radio crítico es tan disponible como su red de transporte**. En §5.3 se desarrollan los requisitos de disponibilidad.

> **[REFERENCIA CRUZADA]** El diseño de la red de transporte que une las estaciones base con los nodos —radioenlaces, fibra, topologías en anillo— pertenece al **Tema 33**; los mecanismos de redundancia y continuidad, al **Tema 26** (copias de seguridad y recuperación) y al **Tema 39** (medidas `op.cont` del ENS).

#### 2.1.3. Centros de gestión y administración del sistema

Este tercer bloque es el que más se olvida al estudiar y el que más aparece en los casos prácticos, porque es **donde trabajan las personas**.

**El sistema de gestión de red (NMS).** Supervisa el estado de todos los elementos: alarmas de estaciones base, ocupación de canales, calidad de los enlaces, estado de las baterías y de los grupos electrógenos, temperatura de los emplazamientos. Es el sistema desde el que se detecta que una estación base ha perdido el enlace **antes** de que un agente se quede sin cobertura. Se comunica con la SwMI por la **interfaz de gestión de red (I5)**.

**La gestión de abonados y de la flota.** Alta y baja de terminales, asignación de identidades, definición y modificación de **grupos de conversación**, perfiles de usuario, prioridades, y —función crítica— la **inhabilitación remota** de un terminal robado o perdido (*stun* temporal o *kill* permanente).

**Las consolas de despacho.** Son los puestos de operador de los centros de mando: permiten escuchar varios grupos a la vez, hablar en cualquiera de ellos, lanzar llamadas individuales, ver la **posición de los terminales** sobre un plano y atender las **alarmas de emergencia**. Se conectan a la SwMI por la **interfaz de línea** (§2.3.3).

**El registro y la grabación.** Todas las comunicaciones de un servicio de emergencia se **graban**, con su marca de tiempo y su identidad de origen, tanto por razones operativas (reconstruir una intervención) como jurídicas (prueba en un procedimiento). El grabador es un elemento de la infraestructura, no un añadido.

**La gestión de claves criptográficas.** Generación, custodia, distribución y renovación de las claves de cifrado, incluida la **distribución por el aire (OTAR)**. Es una función de seguridad de primer orden que el ENS recoge expresamente en la medida **`op.exp.10`, «protección de claves criptográficas»** `[ENS]`.

> **[EJEMPLO AYTO MADRID]** El **CISEM** —Centro Integrado de Seguridad y Emergencias, en la calle Rufino Blanco 2— es exactamente este tercer bloque hecho edificio. Desde él se coordinan **Policía Municipal (092), Bomberos, SAMUR-Protección Civil y Agentes de Movilidad**, con del orden de **3.000 incidentes diarios** `[CISEM]`. Y en el contrato de 2026 aparece explícitamente la evolución de esta capa: una arquitectura que **unifica el despacho y la grabación de comunicaciones en una plataforma de alta disponibilidad** `[TELEFONICA-2026]`. Obsérvese que lo que se moderniza no es la radio, sino **la capa de gestión y despacho**: es donde está el valor operativo del sistema.

> **[REFERENCIA CRUZADA]** La **grabación de las comunicaciones** y la **geolocalización de los terminales** son tratamientos de **datos personales** de empleados públicos: exigen base jurídica, información previa, plazos de conservación y medidas de seguridad. El marco está en el **Tema 6** (transparencia y acceso) y en el **Tema 32** (seguridad de la información); la protección de datos como tal no tiene tema propio en el temario oficial.

### 2.2. Terminales de usuario

#### 2.2.1. Equipos portátiles, móviles y fijos

**Los tres factores de forma.** El estándar habla genéricamente de **MS** (*Mobile Station*), pero en la práctica se distinguen tres:

| Tipo | Descripción | Potencia típica | Uso característico |
|---|---|---|---|
| **Portátil** (*handheld*, *portable*) | El equipo de mano, alimentado por batería, con antena corta | **1 W** o **3 W** | El agente a pie, el bombero, el sanitario |
| **Móvil** (*mobile*, embarcado) | Instalado en un vehículo, alimentado del sistema eléctrico y con antena exterior | **3 W** o **10 W** | Patrullas, ambulancias, autobombas |
| **Fijo** (*fixed station*, *desktop*) | De sobremesa, en una dependencia, con antena exterior y alimentación de red | **10 W** o más | Oficinas, retenes, puestos de mando avanzados |

> **[DATO CLAVE EXAMEN]** Las **clases de potencia** normalizadas para el terminal TETRA son **clase 1 = 30 W**, **clase 2 = 10 W**, **clase 3 = 3 W** y **clase 4 = 1 W** (existen clases adicionales de menor potencia). En la práctica, **portátiles de 1 y 3 W** y **móviles de 3 y 10 W**. La diferencia de potencia entre un portátil y un móvil explica por qué, en el borde de la cobertura, **el vehículo llega y el agente a pie no**: es el argumento técnico que justifica el uso de **pasarelas** (§2.2.3).

**Elementos comunes a todos ellos:**

- **Botón PTT** (*push-to-talk*), el elemento definitorio.
- **Botón de emergencia**, normalmente de color naranja o rojo y en posición destacada, que lanza una **alarma de emergencia** con prioridad máxima (§4.1.2).
- **Selector de grupo de conversación**, para moverse entre los grupos a los que el usuario está autorizado.
- **Pantalla y teclado**, para mensajes de estado, SDS y menús.
- **Receptor GNSS** integrado, que permite enviar la posición a la consola de despacho mediante SDS (§4.2.1).
- **Módulo de identidad y material criptográfico**, con las identidades del usuario y las claves.
- **Robustez ambiental** certificada (grados **IP** de estanqueidad, resistencia a caídas, rango de temperatura) y, en usos con riesgo de atmósfera explosiva, **certificación ATEX**.
- **Interfaz de datos (PEI)** para conectar un ordenador embarcado o una aplicación (§2.3.3).

**Las identidades del terminal, que se preguntan.** TETRA maneja un esquema de identidades propio:

- La **ITSI** (*Individual TETRA Subscriber Identity*) es la identidad individual completa del abonado. Se compone de la **MNI** (*Mobile Network Identity*, la identidad de la red, formada a su vez por el **MCC** —código de país— y el **MNC** —código de red—) más la **ISSI** (*Individual Short Subscriber Identity*), que es la parte corta que identifica al abonado **dentro** de su red.
- La **GTSI** (*Group TETRA Subscriber Identity*) es la identidad de **grupo**, y su parte corta es la **GSSI** (*Group Short Subscriber Identity*).
- La **TSI** (*TETRA Subscriber Identity*) es el término genérico que engloba a las anteriores.
- Sobre ellas puede aplicarse el **cifrado de identidades**: la **ESI** (*Encrypted Short Identity*), que sustituye la identidad corta por una versión cifrada en el aire para evitar el seguimiento de los usuarios (§4.3.2).
- Y, además de la identidad numérica, un **alias** alfanumérico legible («PM-Centro-12», «SAMUR-Jefe de Guardia») que es lo que se ve en la pantalla.

> **[DATO CLAVE EXAMEN]** **ITSI = MNI + ISSI**, donde **MNI = MCC + MNC**. La identidad **individual** corta es la **ISSI**; la de **grupo**, la **GSSI**. La **ESI** es la identidad corta **cifrada**, y es justamente el mecanismo cuyo diseño débil denunció la investigación **TETRA:BURST** en 2023 (§4.3.2).

#### 2.2.2. Modos de operación: modo troncalizado (TMO) y modo directo (DMO)

Este es **el epígrafe más preguntado de toda la sección** y conviene fijarlo con precisión.

**Modo troncalizado — TMO (*Trunked Mode Operation*).** Es el modo normal: el terminal **se comunica a través de la infraestructura**. Habla con una estación base, la estación base lo conecta con el nodo de conmutación y éste distribuye la comunicación a quien corresponda. Está normalizado en la serie **EN 300 392** (V+D).

- **Ventajas**: cobertura extensa (toda la red), acceso a **todos los grupos** y a todos los servicios, gestión de prioridades, grabación, despacho, geolocalización centralizada, interconexión telefónica y trazabilidad completa.
- **Requisito**: que haya **cobertura de la red**. Sin estación base al alcance, no hay TMO.

**Modo directo — DMO (*Direct Mode Operation*).** El terminal se comunica **directamente con otro terminal, sin infraestructura ninguna**, usando una frecuencia simplex acordada. Está normalizado en la serie **EN 300 396** `[EN396]`.

- **Ventajas**: funciona **allí donde no llega la red** —el interior de un edificio, un sótano, un túnel, una zona rural, una emergencia que ha dejado la infraestructura fuera de servicio— y **no consume recursos** de la red.
- **Limitaciones**: el alcance es el que da la potencia del terminal (**centenares de metros en ciudad, unos pocos kilómetros en campo abierto**); **no hay despacho ni grabación centralizada**; **no hay prioridades gestionadas** por la red; el grupo de conversación es el que se haya programado en los equipos; y la seguridad depende de **claves estáticas precargadas**, no de la autenticación con la red.

> **[DATO CLAVE EXAMEN]** **TMO = a través de la infraestructura (EN 300 392). DMO = terminal a terminal, sin infraestructura (EN 300 396).** El modo directo es una de las diferencias funcionales de fondo entre la PMR y la telefonía celular: un teléfono móvil **no puede** hablar con otro si cae la red; un terminal TETRA **sí**. Es exactamente por esto por lo que un servicio de emergencia no puede sustituir su red de radio por teléfonos móviles.

**El uso operativo real, que es lo que se pregunta en los casos prácticos.** Un servicio de emergencia usa **los dos modos a la vez**, y no de forma alternativa:

- El **mando y la coordinación general** van por **TMO**: es donde está el despacho, la grabación y el resto de la organización.
- La **coordinación dentro de la intervención** —la dotación que entra en un edificio en llamas, el equipo que baja a una galería— va por **DMO**, porque allí no hay cobertura y porque, aunque la hubiera, no tiene sentido ocupar canales de la red para hablar entre personas que están a veinte metros unas de otras.
- Muchos terminales permiten **vigilar el canal TMO mientras se opera en DMO**, o cambiar entre modos con un botón.

**El punto de fricción.** El DMO tiene un problema evidente: **quien está en DMO desaparece del sistema**. El despacho no lo oye, no puede llamarlo, no ve su posición y no queda grabado. La solución a ese problema es el objeto del epígrafe siguiente.

#### 2.2.3. Funciones de repetición y pasarela (*repeater* y *gateway*)

La norma **EN 300 396** define dos figuras que amplían el modo directo, y **hay que distinguirlas con precisión porque hacen cosas distintas**.

**El repetidor de modo directo — DM-REP.** Es un equipo que **recibe en una frecuencia de modo directo y retransmite en otra (o en la misma) con más potencia y desde mejor posición**, ampliando el alcance de una comunicación DMO. **No conecta con la red**: lo que entra en DMO sigue siendo DMO, solo que llega más lejos.

La norma distingue tipos `[EN396]`:

- **DM-REP de tipo 1**: capaz de soportar **una sola llamada** en el interfaz aire. Se subdivide en **tipo 1A**, que trabaja sobre **una única portadora**, y **tipo 1B**, que trabaja sobre **un par de portadoras separadas en dúplex**.
- **DM-REP de tipo 2**: capaz de soportar **dos llamadas** simultáneas en el interfaz aire.

**La pasarela de modo directo — DM-GATE.** Es un equipo que **une el mundo DMO con la red troncalizada**: recibe en modo directo y **reinyecta la comunicación en la red V+D**, y viceversa. Con ella, la dotación que trabaja en DMO dentro de un edificio **vuelve a ser visible y audible** para el despacho, y el mando puede hablar con ella desde el CISEM.

**Y el equipo que hace las dos cosas — DM-REP/GATE**, que combina la función de repetidor y la de pasarela.

> **[DATO CLAVE EXAMEN]** **DM-REP = repetidor: amplía el alcance dentro del modo directo, sin tocar la red.** **DM-GATE = pasarela: conecta el modo directo con la red troncalizada.** **DM-REP/GATE** hace ambas. Los tipos de repetidor son **1A** (una portadora, una llamada), **1B** (par de portadoras dúplex, una llamada) y **2** (dos llamadas). Confundir repetidor con pasarela es el error clásico de este epígrafe.

**Dónde se materializan estas funciones.** Normalmente **en el terminal móvil de un vehículo**: los equipos embarcados de gama profesional pueden configurarse para actuar como DM-REP o DM-GATE. Eso convierte al vehículo aparcado en la puerta de un edificio en **el nodo que da cobertura y conectividad a los que están dentro** —y explica por qué, en la práctica operativa, la ubicación del vehículo de mando no es una decisión menor—. También existen repetidores y pasarelas **transportables**, que se despliegan sobre el terreno en incidentes de larga duración.

> **[EJERCICIO RESUELTO]** **Elegir el modo y el equipo en una intervención real.**
>
> **Supuesto**: incendio en el sótano de un edificio de oficinas del distrito de Salamanca. Intervienen dos dotaciones de **Bomberos**, una **UVI móvil del SAMUR** y una unidad de la **Policía Municipal** que corta el tráfico. El sótano **no tiene cobertura** de la red municipal.
>
> **Paso 1 — Coordinación general.** El mando del incidente, el CISEM y las unidades en superficie trabajan en **TMO**, en el grupo de conversación creado para el incidente. Es donde hay despacho, grabación y visión de posiciones.
>
> **Paso 2 — Dentro del sótano.** Las dotaciones que descienden pasan a **DMO**, porque no hay cobertura. Entre ellas se oyen, pero el CISEM no.
>
> **Paso 3 — Recuperar el enlace.** El vehículo de bomberos aparcado en el portal se configura como **DM-GATE**. A partir de ese momento, lo que se habla en DMO en el sótano **entra en la red** y llega al mando y al CISEM, y lo que dice el mando llega al sótano. La intervención vuelve a estar grabada y coordinada.
>
> **Paso 4 — Si el sótano fuera muy extenso.** Si el alcance del modo directo no bastara para cubrir toda la planta, se añadiría un **DM-REP** —o se usaría un equipo **DM-REP/GATE**— para ampliar el alcance dentro del subsuelo **antes** de reinyectar en la red.
>
> **Conclusión y trampa habitual**: si en el paso 3 se hubiera puesto un **DM-REP** en lugar de un **DM-GATE**, la dotación se oiría mejor entre sí, **pero el CISEM seguiría sin enterarse de nada**. Repetidor y pasarela **no** son intercambiables.

### 2.3. Interfaces estándar de TETRA

**El modelo de referencia.** La guía del diseñador del ETSI `[ETR300-1]` define **seis puntos de referencia**, numerados de **I1 a I6**, que son los que hacen de TETRA un estándar abierto: cada uno delimita una frontera en la que dos elementos de fabricantes distintos deben entenderse.

| Interfaz | Denominación | Qué une | Norma principal |
|---|---|---|---|
| **I1** | **Interfaz aire** (*radio air interface*) | Terminal ↔ estación base, en **modo troncalizado** | **EN 300 392-2** |
| **I2** | **Interfaz de línea** (*line station interface*, LSI/LNI) | Estaciones y equipos conectados por línea ↔ SwMI | EN 300 392 |
| **I3** | **ISI** (*Inter-System Interface*) | Red TETRA ↔ **otra red TETRA** | **EN 300 392-3** |
| **I4** | **Interfaz de equipo terminal** (**PEI**, *Peripheral Equipment Interface*) | Terminal ↔ equipo de datos del usuario | **EN 300 392-5** |
| **I5** | **Interfaz de gestión de red** | SwMI ↔ sistema de gestión (NMS) | EN 300 392 |
| **I6** | **Interfaz aire de modo directo** | Terminal ↔ terminal, **sin red** | **EN 300 396** |

> **[DATO CLAVE EXAMEN]** Las seis interfaces, en orden: **I1 aire (TMO)**, **I2 línea**, **I3 ISI**, **I4 terminal/PEI**, **I5 gestión de red**, **I6 aire en modo directo**. Las **dos interfaces aire** son la **I1** (troncalizado) y la **I6** (directo), y están en normas distintas. A esto se añaden las **pasarelas a PSTN y RDSI** de la **EN 300 392-4**, que no son un punto I sino un elemento funcional.

#### 2.3.1. Interfaz aire (*air interface*)

**Es la norma central del estándar** y el objeto de la **EN 300 392-2** `[EN392-2]`. Define **todo lo que ocurre entre el terminal y la estación base**, y se organiza en tres capas, siguiendo el modelo de referencia de ISO:

1. **Capa física (capa 1)**: la portadora de **25 kHz**, la modulación **π/4-DQPSK**, la tasa de **18.000 símbolos por segundo**, la estructura **TDMA de cuatro intervalos**, los tipos de **ráfaga**, la sincronización, el control de potencia y la corrección de errores. Se desarrolla entera en **§3**.
2. **Capa de enlace de datos (capa 2)**: subdividida en **MAC** (*Medium Access Control*), que gestiona el acceso al medio y multiplexa los canales lógicos sobre los físicos, y **LLC** (*Logical Link Control*), que da el servicio de enlace fiable o no fiable a la capa superior. Aquí residen el **acceso aleatorio con resolución de colisiones** y el **cifrado de interfaz aire**.
3. **Capa de red (capa 3)**: donde viven los protocolos de **gestión de la movilidad** (**MM**), de **control de llamada** (**CMCE**, *Circuit Mode Control Entity*, para voz y datos por circuito), de **datos por paquetes** (**SNDCP**) y de **gestión del propio interfaz** (**MLE**).

> **[DATO CLAVE EXAMEN]** El interfaz aire de TETRA se estructura en **tres capas**: **física**, **enlace (MAC + LLC)** y **red (MM, CMCE, SNDCP, MLE)**. El **cifrado de interfaz aire se aplica en la capa 2**, entre terminal y estación base; el **cifrado extremo a extremo**, por encima, entre terminal y terminal (§4.3.3). Esa diferencia de nivel es la que explica **qué protege cada uno**.

> **[REFERENCIA CRUZADA]** La correspondencia entre estas tres capas y las siete del **modelo OSI** —y las cuatro de **TCP/IP**— es materia del **Tema 34**. Aquí basta con retener que TETRA implementa las tres capas inferiores y que, por encima de ellas, transporta **IP** cuando presta servicio de datos por paquetes (§4.2.2).

#### 2.3.2. Interfaz de interconexión entre sistemas (ISI)

**Qué problema resuelve.** Una red TETRA de un ayuntamiento y otra de una comunidad autónoma son **dos sistemas independientes**: distinta MNI, distintos abonados, distintas claves, distintos centros de mando. Cuando hay una emergencia que afecta a los dos, alguien tiene que poder hablar con alguien. La **ISI** (*Inter-System Interface*), normalizada en la **EN 300 392-3** `[EN392-3]`, es el punto de referencia que permite **interconectar dos redes TETRA** de forma normalizada.

**Qué permite:**

- **Llamadas individuales y de grupo entre abonados de redes distintas.**
- **Itinerancia** (*roaming*): que un terminal de la red A obtenga servicio en la cobertura de la red B, con las autorizaciones que se hayan acordado.
- **Transferencia de mensajes cortos** entre redes.
- **Servicios suplementarios** limitados a través de la interconexión.

**El problema práctico, que conviene decir con franqueza.** La ISI es la parte del estándar cuya **implantación real ha sido más desigual**. Durante años, los fabricantes la implementaron de forma parcial o con extensiones propias, de modo que muchas interconexiones entre redes se resolvieron con **pasarelas de audio** o **acoplamientos a nivel de despacho** —consolas que puentean grupos de dos redes— en lugar de con una ISI completa. Es un punto sensible en cualquier pliego: **conviene exigir la interconexión con requisitos funcionales verificables**, no con una simple mención a la norma.

> **[EJEMPLO AYTO MADRID]** En el territorio del municipio conviven, como mínimo, **tres sistemas de radiocomunicación de emergencia de titularidad distinta**: el **municipal** (DIMETRA-TETRA del Ayuntamiento), el **autonómico** (la red TETRA de la Comunidad de Madrid, con **113 estaciones base** y **5.316 terminales**, gestionada por la **ASEM 112** `[CM-TETRA]`) y el **estatal** (**SIRDEE**, que además **no es TETRA sino TETRAPOL** `[SIRDEE]`). Los dos primeros son interconectables por **ISI**, al menos en teoría; con el tercero **la ISI no sirve**, porque es otra tecnología, y la interoperabilidad tiene que resolverse forzosamente por **pasarelas** o por **acoplamiento de grupos en los centros de mando**. Es la razón técnica por la que la coordinación multiadministración en una emergencia grande sigue apoyándose en los centros 112 y no en la radio.

#### 2.3.3. Interfaz de línea (LNI) e interfaces de datos

**La interfaz de línea (I2).** Es el punto por el que se conectan a la SwMI **los equipos fijos que no llegan por radio**: consolas de despacho, estaciones fijas de dependencias, grabadores, pasarelas telefónicas y sistemas de gestión. Se la denomina **LSI** (*Line Station Interface*) o **LNI** (*Line connected Network Interface*) según la fuente; el enunciado del tema usa la segunda forma. Funcionalmente, permite que un operador del centro de mando tenga en su puesto **las mismas capacidades que un terminal de radio** —hablar en grupos, lanzar llamadas, recibir alarmas— pero con la ergonomía de un puesto de trabajo y sin ocupar recursos radio.

**La interfaz de equipo periférico — PEI (I4).** Normalizada en la **EN 300 392-5** `[EN392-5]`, es la que conecta **el terminal con un equipo de datos del usuario**: el ordenador embarcado de un vehículo, una impresora de denuncias, un lector de matrículas, un sensor de telemetría o una aplicación de gestión de flotas. Se basa en un juego de **comandos AT** extendidos —herencia directa del mundo de los módems— más los protocolos de transporte de datos. Es lo que convierte al terminal en un **módem de datos** además de en una radio.

**Y las pasarelas hacia otras redes.** La **EN 300 392-4** `[EN392-4]` define las pasarelas hacia la **red telefónica pública conmutada (PSTN)** y hacia **RDSI**, que permiten que un terminal de radio llame a un teléfono fijo o móvil, y al revés, con las restricciones de tarificación y autorización que fije el operador de la red.

> **[EJEMPLO AYTO MADRID]** El **PEI** es lo que hace posible una función cotidiana en la Policía Municipal: que el terminal embarcado transmita, sin intervención del agente, la **posición del vehículo** al sistema de gestión de flotas del CISEM, y que el ordenador del coche patrulla curse consultas a sistemas de información —matrículas, requisitorias— **usando la radio como canal de datos** cuando no hay cobertura de datos comercial o cuando se exige que el tráfico vaya por la red propia. La capacidad es modesta en TETRA Release 1 (§4.2.2), lo bastante para texto y consultas breves, y es justo el límite que **TEDS** (§5.4) vino a ampliar.

> **[REFERENCIA CRUZADA]** El uso del terminal como canal de datos para aplicaciones de gestión enlaza con el **Tema 24** (desarrollo para dispositivos móviles) y con el **Tema 22** (arquitecturas cliente/servidor y servicios web); la protección del tráfico de esas aplicaciones, con el **Tema 36**.
---
## 3. Capa física y transmisión radio en TETRA

**Advertencia de estudio.** Esta es la sección **más rentable en puntos por palabra** de todo el tema y la que exige memorización literal. Todo lo que sigue está en la **EN 300 392-2** `[EN392-2]`, y las bandas de frecuencia, en el **CNAF** `[CNAF]`. Conviene estudiarla con el **D9** (espectro), el **D10** (FDMA + TDMA), el **D11** (modulación) y el **D12** (jerarquía temporal) delante.

### 3.1. Espectro radioeléctrico y asignación de frecuencias

**El principio de partida.** El espectro radioeléctrico es un **bien de dominio público** cuya titularidad y administración corresponden al **Estado** —art. **85** de la Ley 11/2022 `[LGTel]`—. Ninguna Administración, ni siquiera un ayuntamiento, «tiene» frecuencias: **las usa al amparo de un título habilitante** otorgado por el Estado, con las condiciones que fije el CNAF. El régimen jurídico completo se desarrolla en §5.2; aquí interesa **qué bandas usa TETRA y con qué características técnicas**.

**Las bandas de TETRA en el mundo.** El estándar no está atado a una banda concreta: la **EN 300 392-2** define parámetros de capa física y la parte correspondiente de la serie **TS 100 392** enumera las bandas y separaciones dúplex admitidas. En la práctica, TETRA se despliega en:

| Rango | Uso característico |
|---|---|
| **380-400 MHz** | **Servicios de emergencia y seguridad pública en Europa** (banda armonizada) |
| **410-430 MHz** | **Uso civil, PMR/PAMR, transporte, industria y servicios públicos** |
| **450-470 MHz** | Uso civil y PPDR según país |
| **806-870 MHz** | Uso comercial y de transporte, principalmente fuera de Europa |

**Y ahora la parte española, que es la que se pregunta.** El **Cuadro Nacional de Atribución de Frecuencias** es la norma que reparte el espectro en España. Y aquí hay que empezar por un dato que casi ningún material recoge todavía:

> **[DATO CLAVE EXAMEN]** **El CNAF vigente es el aprobado por la Orden TDF/732/2026, de 10 de julio** (BOE núm. 173, de **17 de julio de 2026**, 349 páginas). **Sustituye al anterior —Orden ETD/1449/2021, de 16 de diciembre— con efectos de 18 de julio de 2026**, y su motivo declarado es incorporar las previsiones de la **Conferencia Mundial de Radiocomunicaciones de 2023 (CMR-23)**, en vigor en su mayoría desde el **1 de enero de 2025**. Quien haya estudiado con material anterior al verano de 2026 citará una orden **derogada**.

**Las dos notas del CNAF que hay que conocer.** Las condiciones concretas de uso de cada banda están en las **notas de utilización nacional (UN)**. Dos de ellas son directamente materia de este tema.

**Nota UN-28 — la banda de las emergencias.** Dice literalmente que la banda **235-399,9 MHz** está destinada a **uso exclusivo del Estado para sistemas del Ministerio de Defensa**, *con excepción* de las subbandas **380-385 MHz y 390-395 MHz** que, **de conformidad con la Decisión de la CEPT ECC/DEC(08)05**, «se destinan para **redes de servicios de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y redes de servicios de emergencia en todo el territorio nacional**» `[CNAF]`. Obsérvese la estructura: son **dos subbandas de 5 MHz separadas 10 MHz**, es decir, un **par dúplex**: 380-385 MHz para un sentido y 390-395 MHz para el otro. La nota añade un dato operativo interesante: por problemas de **saturación en entornos urbanos de alta densidad**, las solicitudes de asignación deben incluir «un exhaustivo **plan de reutilización** que minimice las necesidades de espectro».

**Nota UN-31 — la banda de TETRA civil, donde el CNAF nombra la tecnología.** Estructura la banda **406-470 MHz** en subbandas. La que interesa es la **410-430 MHz**, «reservada a aplicaciones del servicio móvil y fijo de banda estrecha bajo la modalidad **dúplex con una separación Tx/Rx de 10 MHz**». Y dentro de ella, textualmente: «Las subbandas de frecuencias **410 a 415,3 MHz y 420 a 425,3 MHz** […] se destinan a **sistemas digitales de acceso aleatorio de canales (TETRA y otros)** con anchura de banda de emisión correspondiente a una **canalización de 25 kHz**» `[CNAF]`. El resto de la banda 410-430 MHz se destina a comunicaciones dúplex con canalización de **12,5 kHz**.

> **[DATO CLAVE EXAMEN]** Las dos cifras que hay que saber de memoria: **380-385 / 390-395 MHz** para las redes de **seguridad del Estado y emergencias** (nota **UN-28**, decisión **ECC/DEC(08)05**); y **410-415,3 / 420-425,3 MHz** para **TETRA civil**, con **canalización de 25 kHz** y **separación dúplex de 10 MHz** (nota **UN-31**). El CNAF **cita TETRA por su nombre** en esta segunda nota: es la única mención expresa de la tecnología en la norma española del espectro, y por eso es un dato de examen de primer orden.

**Un tercer dato del CNAF, para la evolución.** La misma nota **UN-31** reserva los bloques pareados **452-457,5 / 462-467,5 MHz**, en aplicación de la Decisión **ECC/DEC(16)02**, «a sistemas de **protección pública y operaciones de socorro en caso de catástrofe PPDR** de **banda ancha**, preferentemente para el sistema de ámbito nacional» `[CNAF]`. Y en la banda de **700 MHz**, el CNAF destina **733-736 / 788-791 MHz** al sistema PPDR de **ámbito nacional** y **698-703 / 753-758 MHz** a las **redes de ámbito autonómico y local** `[CNAF]`. Ese último bloque es, literalmente, **el espectro que la norma española reserva para una futura red de banda ancha crítica de una comunidad autónoma o de un ayuntamiento** (§5.4).

> **[EJERCICIO RESUELTO]** **Leer el CNAF y decidir en qué banda encaja un despliegue.**
>
> **Supuesto**: un ayuntamiento quiere ampliar su red TETRA para dar servicio, además de a policía y bomberos, a los servicios de limpieza y de parques y jardines.
>
> **Paso 1 — ¿Sirve la banda de 380-400 MHz?** La nota **UN-28** la reserva a «redes de servicios de seguridad de las FCSE y redes de servicios de emergencia». Un servicio de **limpieza viaria** no es ninguna de las dos cosas. **No encaja** por la vía de la UN-28.
>
> **Paso 2 — ¿Y la banda de 410-430 MHz?** La nota **UN-31** destina 410-415,3 / 420-425,3 MHz a «sistemas digitales de acceso aleatorio de canales (TETRA y otros)» con canalización de **25 kHz**, sin restringirlo a emergencias. **Encaja**.
>
> **Paso 3 — ¿Cuántas frecuencias hacen falta?** La subbanda útil es de **5,3 MHz** en cada sentido; a **25 kHz** por portadora, caben **212 portadoras** teóricas en el conjunto del territorio nacional, que se reutilizan geográficamente. El ayuntamiento pedirá **las portadoras concretas** que necesite su plan de reutilización, no la subbanda entera.
>
> **Paso 4 — ¿Qué título habilitante?** Uso **privativo** para **autoprestación** por una Administración pública → **afectación demanial**, art. **88.5.b)** de la Ley 11/2022 (§5.2).
>
> **Conclusión**: la respuesta no es «la banda de emergencias porque somos un ayuntamiento», sino «la banda que corresponda **al servicio**, según lo que diga la nota UN». Es el error más frecuente en este tipo de pregunta.

**Reutilización de frecuencias y planificación celular.** Como en cualquier sistema celular, las mismas portadoras se reutilizan en células suficientemente alejadas. El **patrón de reutilización** debe garantizar una relación señal-interferencia suficiente; en TETRA se manejan patrones más conservadores que en telefonía celular porque el requisito de **calidad de voz en el borde de la célula** es más exigente. La contrapartida es que la red necesita **menos capacidad por célula** que una red comercial: el tráfico de un servicio de emergencia es de baja ocupación media y picos muy acusados.

### 3.2. Técnica de acceso múltiple por división de tiempo (TDMA)

**Los tres accesos múltiples, en una frase cada uno.** Para situar TETRA hay que tener claros los tres esquemas clásicos:

- **FDMA** (*Frequency Division Multiple Access*): a cada usuario se le da **una frecuencia distinta**. Es lo que hace la radio analógica convencional y lo que hace **TETRAPOL**.
- **TDMA** (*Time Division Multiple Access*): varios usuarios **comparten la misma frecuencia** turnándose en el tiempo, en **intervalos** (*time slots*) periódicos. Es lo que hace **TETRA** —y lo que hacía GSM—.
- **CDMA** (*Code Division Multiple Access*): todos transmiten a la vez en la misma banda, separados por **códigos ortogonales**. No se usa en TETRA.

**Lo que hace TETRA es una combinación.** El espectro se divide primero en **portadoras de 25 kHz** —eso es **FDMA**— y cada portadora se divide después en **4 intervalos de tiempo** —eso es **TDMA**—. El resultado es que **una sola pareja de frecuencias de 25 kHz sostiene cuatro canales físicos**.

> **[DATO CLAVE EXAMEN]** **TETRA usa FDMA + TDMA 4:1**: portadoras de **25 kHz** con **4 intervalos** cada una. Ésta es **la** cifra del tema. De ella se derivan las demás: 4 canales por portadora, uno de ellos normalmente de control, y **tres de tráfico** en una estación base de una sola portadora.

**Por qué esto importa tanto en la comparación con TETRAPOL.** Es la diferencia estructural entre los dos sistemas y la pregunta comparativa más probable:

| | **TETRA** | **TETRAPOL** |
|---|---|---|
| Origen | **Estándar abierto del ETSI** | Desarrollo **propietario** (Matra/EADS, hoy Airbus) |
| Acceso múltiple | **TDMA** (4 intervalos) | **FDMA** |
| Canalización | **25 kHz** | **12,5 kHz** |
| Modulación | **π/4-DQPSK** | **GMSK** |
| Canales por par de frecuencias | **4** | **1** |
| Eficiencia por canal de voz | 25 kHz / 4 = **6,25 kHz por canal** | **12,5 kHz por canal** |
| Uso en España | Redes **autonómicas y municipales** (Madrid, entre otras) | **SIRDEE**, la red del **Estado** |

> **[DATO CLAVE EXAMEN]** **TETRA = TDMA, 25 kHz, 4 canales por portadora, π/4-DQPSK. TETRAPOL = FDMA, 12,5 kHz, 1 canal por portadora, GMSK.** En **eficiencia espectral por canal de voz**, TETRA obtiene **6,25 kHz/canal** frente a los **12,5 kHz/canal** de TETRAPOL: **el doble**. A cambio, el esquema FDMA de TETRAPOL da algo más de alcance por canal en condiciones de propagación difíciles, que es el argumento clásico de sus defensores para el despliegue rural. Y, sobre todo: **el SIRDEE español es TETRAPOL, no TETRA**.

**Las consecuencias prácticas del TDMA.** El esquema de intervalos no es solo una forma de repartir: habilita funciones que el FDMA no tiene fáciles.

1. **Menos hardware en la estación base.** Cuatro canales de conversación caben en **un transceptor**, no en cuatro. Menos amplificadores, menos combinadores, menos consumo, menos espacio y menos coste por canal.
2. **Agregación de intervalos para datos.** Si un usuario necesita más capacidad, el sistema puede darle **dos, tres o los cuatro intervalos** de la portadora, multiplicando su tasa (§4.2.2). En FDMA habría que darle varias frecuencias, con la complejidad que eso supone en el terminal.
3. **Modo dúplex sin duplexor completo.** El terminal transmite en un intervalo y recibe en otro **desplazado en el tiempo**, lo que simplifica el diseño de radiofrecuencia.
4. **Ahorro de batería.** El terminal solo transmite y recibe en sus intervalos; el resto del tiempo puede reducir consumo. Es una de las razones de la buena autonomía de los portátiles TETRA.

**Y su limitación característica: el alcance.** La estructura de intervalos impone un **tiempo de guarda** finito entre transmisiones consecutivas. Si un terminal está muy lejos, su ráfaga llega tan retrasada que **invadiría el intervalo siguiente**. Ese razonamiento fija el **radio máximo de célula de TETRA Release 1 en 58 km**. No es una limitación de potencia, sino **de tiempo**: es el mismo fenómeno que limitaba el alcance de las células GSM.

> **[DATO CLAVE EXAMEN]** El **radio máximo de célula en TETRA Release 1 es de 58 km**, y la causa es **la estructura temporal de los intervalos TDMA**, no la potencia. TETRA Release 2 incorporó mejoras de alcance para superar ese límite en despliegues rurales, marítimos y militares.

### 3.3. Modulación digital π/4-DQPSK

**Qué modulación usa TETRA y cómo se lee su nombre.** La modulación del interfaz aire de TETRA Release 1 es la **π/4-DQPSK**, *differential quaternary phase shift keying* con desplazamiento de π/4. Se descompone así:

- **PSK** (*Phase Shift Keying*): la información se codifica en la **fase** de la portadora, no en su amplitud ni en su frecuencia.
- **Q** de *quaternary*: hay **cuatro** estados de fase posibles, de modo que **cada símbolo transporta 2 bits** (2² = 4).
- **D** de *differential*: lo que se codifica **no es la fase absoluta**, sino **el cambio de fase respecto al símbolo anterior**. Eso permite una **detección diferencial** que no necesita recuperar una referencia de fase absoluta en el receptor, lo que simplifica el terminal y lo hace más robusto frente a los desplazamientos de fase que provoca el movimiento.
- **π/4**: entre dos símbolos consecutivos se introduce un **desplazamiento adicional de 45°**, de manera que las transiciones nunca pasan por el **origen de la constelación**.

**Por qué ese detalle del origen es importante.** Pasar por el origen significa que la **envolvente de la señal cae a cero**, y una señal con variaciones muy bruscas de amplitud obliga a usar amplificadores muy lineales, que son **caros e ineficientes en consumo**. Al evitar el paso por cero, la π/4-DQPSK mantiene una **relación pico-media moderada**, lo que permite amplificadores más eficientes: en un terminal alimentado por batería, eso se traduce directamente en **más horas de autonomía**.

> **[DATO CLAVE EXAMEN]** **π/4-DQPSK**: **4 estados de fase → 2 bits por símbolo**; **codificación diferencial** (se codifica el **cambio** de fase, no la fase absoluta); y **desplazamiento de π/4** que evita el paso por el origen y, con él, las caídas de envolvente a cero. Comparar con la **GMSK** de TETRAPOL y de GSM, que es de **envolvente constante** y **1 bit por símbolo**.

**Las cifras que se derivan.** La tasa de símbolo del interfaz aire es de **18.000 símbolos por segundo (18 kbaudios)** en un canal de **25 kHz**, con filtrado de **coseno alzado en raíz** de factor de caída (*roll-off*) **α = 0,35**. Como cada símbolo lleva **2 bits**:

**18.000 símbolos/s × 2 bits/símbolo = 36.000 bits/s = 36 kbit/s brutos por portadora.**

Y como la portadora se divide en **4 intervalos**, a cada uno le corresponden **9 kbit/s brutos**, de los que —descontadas la sincronización, las cabeceras y la protección de errores— quedan **7,2 kbit/s netos** disponibles por intervalo para el usuario.

> **[DATO CLAVE EXAMEN]** La cadena de cifras que hay que saber encadenar: **25 kHz → 18 kbaudios → 2 bits/símbolo → 36 kbit/s brutos por portadora → 4 intervalos → 7,2 kbit/s netos por intervalo**. Con los **cuatro intervalos** agregados: **28,8 kbit/s** netos. Es la cifra que define el techo de datos de TETRA Release 1 y la razón de ser de **TEDS**.

**El códec de voz.** La voz se digitaliza con un códec **ACELP** (*Algebraic Code Excited Linear Prediction*), definido en la **EN 300 395** `[EN395]`. Sus cifras:

- Trabaja sobre **tramas de voz de 30 ms**, muestreadas a **8 kHz** (240 muestras por trama).
- Produce **137 bits por trama**, lo que da **137 / 0,030 = 4.567 bits/s ≈ 4,567 kbit/s** netos de voz.
- A esos bits se les añade **codificación de canal** (protección frente a errores), hasta ocupar los **7,2 kbit/s** del intervalo.

> **[DATO CLAVE EXAMEN]** Códec **ACELP** de TETRA: **137 bits cada 30 ms = 4,567 kbit/s** de voz neta; con protección de errores, **7,2 kbit/s** por intervalo. La diferencia entre ambas cifras —casi el 37 % del caudal dedicado a **corregir errores**— es lo que permite que la voz siga siendo inteligible en el borde de la cobertura, y es una de las ventajas de fondo de la radio digital sobre la analógica: en analógico, la degradación es **progresiva** (ruido creciente); en digital, la corrección de errores mantiene la calidad **constante** hasta que se cae de golpe.

**La protección de errores.** TETRA aplica una cadena clásica: **codificación convolucional** con distintas tasas según la importancia de los bits (los bits más significativos de la voz se protegen más que los menos), **entrelazado** (*interleaving*) para repartir en el tiempo los errores en ráfaga típicos del desvanecimiento, y **comprobación de redundancia cíclica (CRC)** para detectar tramas irrecuperables. Para datos existen tres niveles: **sin protección (7,2 kbit/s)**, **protección baja (4,8 kbit/s)** y **protección alta (2,4 kbit/s)** por intervalo.

> **[REFERENCIA CRUZADA]** Los fundamentos de la modulación digital, la relación entre ancho de banda y tasa binaria y las técnicas de detección y corrección de errores se tratan en el **Tema 33**. Aquí se aplican a un caso concreto y con cifras concretas.

### 3.4. Estructura de trama radio y canales lógicos

**La jerarquía temporal, que hay que memorizar entera.** El tiempo en el interfaz aire de TETRA está organizado en cuatro niveles anidados:

| Unidad | Composición | Duración |
|---|---|---|
| **Intervalo de tiempo** (*time slot*) | Unidad básica | **14,167 ms** |
| **Trama TDMA** (*frame*) | **4 intervalos** | **56,67 ms** |
| **Multitrama** (*multiframe*) | **18 tramas** | **1,02 s** |
| **Hipertrama** (*hyperframe*) | **60 multitramas** | **61,2 s** |

> **[DATO CLAVE EXAMEN]** **1 intervalo = 14,167 ms · 1 trama = 4 intervalos = 56,67 ms · 1 multitrama = 18 tramas = 1,02 s · 1 hipertrama = 60 multitramas = 61,2 s.** Y el detalle que se pregunta con más frecuencia: **la trama 18 de cada multitrama es la trama de control**, reservada a señalización. Por eso el usuario dispone de **17 de cada 18 tramas** para su tráfico, y no de las 18.

**Por qué existe la trama de control.** Reservar una trama de cada dieciocho para señalización permite que la red envíe información a un terminal **mientras éste está en conversación**, sin interrumpirla: avisos de llamada entrante, actualizaciones de estado, cambios de clave, órdenes de traspaso. Es lo que hace posible la función de **entrada tardía** (*late entry*): un terminal que se afilia a un grupo con la conversación ya empezada **se entera de que hay una llamada en curso** y se incorpora a ella.

**La hipertrama y la criptografía.** La hipertrama de **61,2 s** no es un capricho: el **número de hipertrama** interviene en la generación del flujo de clave del cifrado de interfaz aire, junto con el **tiempo de red** difundido por la estación base. Este detalle, aparentemente menor, es exactamente el que la investigación **TETRA:BURST** convirtió en vulnerabilidad: **si el tiempo de red se difunde sin autenticar, un atacante puede manipularlo y forzar la reutilización del flujo de clave** (§4.3.2).

**Los tipos de ráfaga (*burst*).** Cada intervalo se ocupa con una **ráfaga** cuyo formato depende del sentido y de la función:

- **Enlace descendente** (estación base → terminal): **ráfaga normal descendente** (*normal downlink burst*, con **432 bits útiles** en dos bloques de 216), **ráfaga de sincronización** (*synchronisation burst*, que porta la información de temporización y de trama) y **ráfaga de linealización descendente**.
- **Enlace ascendente** (terminal → estación base): **ráfaga normal ascendente** (**336 bits útiles**, en dos bloques de 168), **ráfaga de control ascendente** (**168 bits**, que ocupa un **subintervalo** y se usa para el acceso aleatorio) y **ráfaga de linealización ascendente**.

> **[DATO CLAVE EXAMEN]** La ráfaga **descendente** es **continua** —la estación base transmite sin interrupción, lo que da a los terminales una referencia permanente de sincronismo— mientras que la **ascendente** es **discontinua**, porque cada terminal solo transmite en su intervalo. La **ráfaga de control ascendente** ocupa **medio intervalo** (*subslot*) y es la que se usa para el **acceso aleatorio**, es decir, para pedir recurso al sistema; por eso las colisiones se resuelven ahí y no en los canales de tráfico.

**Los canales lógicos.** Sobre esa estructura física, la capa MAC define **canales lógicos**, que son los que transportan cada tipo de información. Se agrupan en dos familias:

**Canales de control (CCH):**

| Canal | Nombre | Función |
|---|---|---|
| **BCCH** | *Broadcast Control Channel* | Difusión de la información del sistema, en dos variantes: **BNCH** (información de red) y **BSCH** (información de sincronización) |
| **LCH** | *Linearisation Channel* | Linealización de los amplificadores |
| **SCH** | *Signalling Channel* | Señalización punto a punto y de acceso: **SCH/F** (completo), **SCH/HD** (medio, descendente), **SCH/HU** (medio, ascendente, el del acceso aleatorio) |
| **ACCH** | *Associated Control Channel* | Señalización **asociada** a una llamada en curso: **FACCH** (rápido, roba capacidad al tráfico) y **SACCH** (lento, usa la trama de control) |
| **STCH** | *Stealing Channel* | Señalización urgente que «roba» capacidad al canal de tráfico |

**Canales de tráfico (TCH):**

| Canal | Función |
|---|---|
| **TCH/S** | Tráfico de **voz** (*speech*), a 7,2 kbit/s por intervalo |
| **TCH/7,2** | Datos **sin protección**, 7,2 kbit/s |
| **TCH/4,8** | Datos con **protección baja**, 4,8 kbit/s |
| **TCH/2,4** | Datos con **protección alta**, 2,4 kbit/s |

> **[DATO CLAVE EXAMEN]** Distinguir **canal físico** (un intervalo de una portadora) de **canal lógico** (el tipo de información que se transporta sobre él). Y dentro de los lógicos, las dos familias: **de control (CCH)** y **de tráfico (TCH)**. El **canal de control principal (MCCH)** es el canal lógico de control que la estación base mantiene permanentemente activo en el **intervalo 1 de la portadora principal**.

> **[EJERCICIO RESUELTO]** **Calcular la capacidad real de una estación base municipal.**
>
> **Supuesto**: una estación base con **3 portadoras** de 25 kHz da cobertura al centro de la ciudad.
>
> **Paso 1 — Canales físicos brutos**: 3 portadoras × 4 intervalos = **12 canales físicos**.
>
> **Paso 2 — Descontar el control**: la configuración estándar dedica **1 intervalo al MCCH** → **11 canales de tráfico**.
>
> **Paso 3 — Traducirlo a conversaciones**: cada llamada de grupo o individual ocupa **un canal de tráfico** mientras alguien está hablando → hasta **11 conversaciones simultáneas** en esa célula.
>
> **Paso 4 — ¿Y cuántos grupos caben?** **Todos los que se quiera.** Un grupo no ocupa canal por existir, sino **solo cuando alguien transmite en él**. Con 11 canales de tráfico pueden convivir decenas de grupos de conversación afiliados en la célula, siempre que no hablen once más uno a la vez.
>
> **Paso 5 — Ancho de banda ocupado**: 3 portadoras × 25 kHz = **75 kHz** en cada sentido, **150 kHz** contando el par dúplex.
>
> **Comparación**: para dar 11 canales de voz simultáneos con radio convencional analógica de 12,5 kHz harían falta **11 parejas de frecuencias**, es decir, **137,5 kHz en cada sentido**, y además **rígidamente asignadas**. Es la ventaja del *trunking* y del TDMA sumadas.

> **[EJEMPLO AYTO MADRID]** Estas cifras explican por qué la red municipal puede atender simultáneamente a **más de 3.000 efectivos** `[TELEFONICA-2026]` con un número modesto de portadoras: en un momento cualquiera, la inmensa mayoría de esos efectivos **están escuchando, no hablando**, y escuchar **no consume canal en su célula si nadie de su grupo transmite allí**. El dimensionado de una red de emergencia no se hace por número de usuarios, sino por **número de transmisiones simultáneas previstas en la hora punta de la célula más cargada**, con un margen holgado para el escenario de gran emergencia, en el que todo el mundo quiere hablar a la vez.
---
## 4. Servicios y seguridad en sistemas TETRA

**Cómo clasifica el estándar sus servicios.** El ETSI, siguiendo la tradición de las normas de telecomunicación, ordena lo que TETRA ofrece en tres familias:

1. **Teleservicios**: los que el sistema presta de extremo a extremo, con el terminal incluido. En TETRA, básicamente **la voz**.
2. **Servicios portadores** (*bearer services*): los que ofrecen **transporte de información** entre dos puntos, dejando al usuario la aplicación. En TETRA, los servicios de **datos** por circuito y por paquetes.
3. **Servicios suplementarios**: los que **modifican o complementan** a los anteriores. Es la familia más rica de TETRA y la que le da su carácter de sistema profesional: prioridad, desalojo, escucha ambiente, escucha discreta, DGNA, identificación, desvío, inclusión, entrada tardía, inhabilitación remota.

> **[DATO CLAVE EXAMEN]** Las tres familias del estándar: **teleservicios** (voz), **servicios portadores** (datos) y **servicios suplementarios** (las funciones profesionales). Los **servicios suplementarios** están normalizados en las **partes 9 a 12 de la EN 300 392**, y son **más de una treintena**. Que existan **normalizados** —y no como extensiones de fabricante— es una de las razones del éxito de TETRA.

### 4.1. Servicios de voz y comunicaciones de grupo

#### 4.1.1. Llamadas individuales, de grupo y de difusión

**Los tipos de llamada, uno a uno.**

**Llamada de grupo (*group call*).** Es **el modo natural de TETRA**. Un usuario aprieta el PTT y su voz llega **a todos los miembros del grupo de conversación** que estén afiliados y en cobertura. Características:

- Es **semidúplex** (*half-duplex*): habla uno, escuchan todos; el canal se libera al soltar el PTT.
- Es **punto a multipunto**: la red replica el audio hacia todas las células donde haya afiliados, ocupando **un canal en cada una de ellas**, no uno por usuario.
- El **grupo es una entidad lógica**, identificada por su **GSSI**, no una frecuencia.
- Admite **entrada tardía** (*late entry*): quien se afilia o recupera cobertura con la llamada ya iniciada **se incorpora a ella**.
- Puede ser **abierta** (*open channel*), un canal permanentemente establecido en el que basta apretar el PTT sin señalización previa, muy usado en operativos.

**Llamada individual (*individual call*).** De un usuario a otro. Puede ser:

- **Semidúplex**, con PTT, como una llamada de grupo de dos personas.
- **Dúplex completo** (*full duplex*), como una llamada telefónica convencional: ambos hablan y escuchan a la vez. Consume **dos intervalos** (uno en cada sentido) y por eso se usa con moderación.

**Llamada de difusión (*broadcast call*).** Es una llamada **unidireccional de uno a muchos**: el emisor habla y los destinatarios **solo escuchan**, sin posibilidad de responder. Se usa para avisos generales del centro de mando a toda una flota o a todos los usuarios de la red. La clave para el examen es la **unidireccionalidad**.

**Llamada telefónica (*PABX/PSTN call*).** A través de las pasarelas de la **EN 300 392-4**, un terminal puede llamar a la centralita corporativa o a la red telefónica pública, y recibir llamadas de ellas, con las autorizaciones que fije el operador de la red.

> **[DATO CLAVE EXAMEN]** Los cuatro tipos: **grupo** (uno a muchos, **bidireccional**, semidúplex), **individual** (uno a uno, semidúplex o **dúplex completo**), **difusión** (uno a muchos, **unidireccional**: los receptores no pueden contestar) y **telefónica** (hacia PSTN/PABX). La diferencia entre **grupo** y **difusión** es que en la primera **cualquiera puede tomar la palabra** y en la segunda **no**.

**La gestión de grupos, que es donde está la potencia operativa.**

- **Afiliación**: un terminal se **afilia** a los grupos que tiene programados y autorizados; la red sabe en qué célula está cada afiliado y solo replica el audio donde hace falta.
- **Grupo seleccionado y grupos de escucha**: el usuario tiene **un grupo seleccionado** —en el que habla al apretar el PTT— y puede además **escuchar** otros en segundo plano (*scanning*), con prioridades entre ellos.
- **DGNA** (*Dynamic Group Number Assignment*), **asignación dinámica de número de grupo**: el centro de mando puede **crear un grupo nuevo y cargarlo en los terminales seleccionados por el aire**, sin tocar los equipos. Es la función que permite montar en segundos un grupo mixto para una emergencia concreta —policía, bomberos y sanitarios de un incidente— y disolverlo al terminar.
- **Grupos por patrón geográfico**: los grupos pueden asociarse a zonas, de modo que un terminal se afilie automáticamente al grupo del distrito en el que se encuentra.

> **[DATO CLAVE EXAMEN]** **DGNA = asignación dinámica de grupos por el aire desde el centro de control.** Es la función que hace impensable volver a la radio convencional: en convencional, cambiar la organización de grupos obliga a **reprogramar físicamente cada equipo**; con DGNA se hace desde una consola, en caliente y sobre los terminales elegidos.

**Los servicios suplementarios de voz que hay que saber nombrar:**

- **Escucha ambiente** (*ambience listening*): el centro de mando activa remotamente el micrófono de un terminal **sin que su portador lo sepa ni intervenga**, para oír lo que ocurre alrededor. Pensada para el agente que no responde o que está incapacitado.
- **Escucha discreta** (*discreet listening*): un usuario autorizado escucha una conversación en curso **sin que los participantes lo perciban**.
- **Inclusión** (*call inclusion*): un supervisor **se incorpora** a una llamada en curso.
- **Identificación de la parte llamante**: en pantalla aparece el **alias** de quien habla, algo que la radio analógica no podía dar.
- **Inhabilitación remota**: **desactivación temporal** (*stun*) o **permanente** (*kill*) de un terminal robado o extraviado, ordenada desde el centro de gestión.

> **[EJEMPLO AYTO MADRID]** La **escucha ambiente** y la **inhabilitación remota** son ejemplos de funciones con un **impacto directo en derechos** que exigen procedimiento escrito, autorización y registro. Un terminal municipal es un instrumento de trabajo entregado a un empleado público, y activar su micrófono a distancia o dejarlo inservible son actuaciones que deben estar **previstas, motivadas y trazadas**. En términos de la normativa de seguridad, la traza queda amparada por las medidas de **registro de actividad** del ENS; en términos de protección de datos, requieren información previa a la persona trabajadora y una base jurídica clara. El examen puede preguntar por la función técnica; el caso práctico, por la garantía que la rodea.

#### 4.1.2. Gestión de prioridades y llamadas de emergencia

**El principio.** En una red de emergencia, **no todas las comunicaciones valen lo mismo**. El sistema debe garantizar que, cuando el recurso escasea, se sirve primero a quien más lo necesita. TETRA lo resuelve con tres mecanismos escalonados.

**1. Prioridad de acceso (*priority call*).** Cada usuario y cada tipo de llamada llevan asociado un **nivel de prioridad**. Cuando varias peticiones compiten por el mismo canal libre, **se atiende primero la de mayor prioridad**; las demás quedan **en cola**, no rechazadas.

**2. Prioridad con desalojo (*pre-emptive priority call*).** Si **no hay ningún canal libre**, una llamada de prioridad suficiente puede **desalojar** una conversación en curso de prioridad inferior, que se corta para liberar el recurso. Es el mecanismo que garantiza que **una emergencia siempre entra**, aunque la red esté saturada.

**3. Llamada de emergencia (*emergency call*).** Es el nivel máximo. Se lanza con el **botón de emergencia** del terminal y desencadena, típicamente:

- Establecimiento **inmediato** en el grupo de emergencia, con **la máxima prioridad y desalojo**.
- **Alarma visual y sonora** en la consola de despacho, con la **identidad** y, si el terminal la envía, la **posición** del usuario.
- Apertura de un **canal de voz abierto** desde ese terminal, en algunas configuraciones sin necesidad de que el agente pulse el PTT —de modo que, si está incapacitado, el centro de mando **oye igualmente lo que ocurre**—.

> **[DATO CLAVE EXAMEN]** Los tres escalones: **prioridad de acceso** (ordena la cola) → **prioridad con desalojo** (*pre-emption*, **corta** una llamada en curso de menor prioridad) → **llamada de emergencia** (máxima prioridad, alarma en despacho, identidad y posición). La diferencia entre los dos primeros es exactamente la que hay entre **esperar mejor** y **echar a otro**.

**Las funciones asociadas al agente en riesgo.** Los terminales profesionales incorporan detecciones automáticas que disparan la alarma sin intervención del usuario:

- **«Hombre caído»** (*man down*): un acelerómetro detecta que el terminal ha quedado en posición horizontal e inmóvil durante un tiempo.
- **Alarma de inactividad** (*lone worker*): el terminal pide confirmación periódica y, si no la recibe, avisa.
- **Botón de emergencia oculto**, activable sin sacar el equipo.

> **[EJEMPLO AYTO MADRID]** El **CISEM** coordina Policía Municipal, Bomberos, SAMUR-Protección Civil y Agentes de Movilidad, con del orden de **3.000 incidentes diarios** `[CISEM]`. Sobre ese volumen, la gestión de prioridades no es un refinamiento teórico: es lo que asegura que una **alarma de agente en riesgo** entre por delante de las decenas de comunicaciones rutinarias que puedan estar cursándose en el mismo instante en la misma célula. Y la razón por la que ese comportamiento **no se puede replicar con teléfonos móviles comerciales**: en una red pública, el Ayuntamiento **no decide** a quién se desaloja.

### 4.2. Servicios de datos

**El encuadre.** TETRA Release 1 nació con capacidades de datos modestas —recuérdese: **7,2 kbit/s netos por intervalo, 28,8 kbit/s agregando los cuatro**— pero muy bien pensadas para lo que un servicio de campo necesita: **mensajes cortos, estados y posiciones**, no navegación web ni vídeo. Conviene tenerlo presente para no juzgar el sistema con la vara equivocada.

#### 4.2.1. Servicio de mensajes cortos (SDS)

**Qué es el SDS.** El **SDS** (*Short Data Service*) es el servicio de **mensajería corta** de TETRA, equivalente funcional del SMS de la telefonía móvil pero mucho más versátil, porque se usa tanto para texto como para **telemetría, posiciones y órdenes máquina a máquina**. Sus mensajes viajan por los **canales de control**, sin necesidad de establecer un canal de tráfico, lo que los hace **muy rápidos y muy baratos en recursos**.

**Los tipos normalizados:**

| Tipo | Longitud de datos | Uso característico |
|---|---|---|
| **Mensaje de estado** (*status*) | **16 bits** precodificados | Estados operativos: «en ruta», «en el lugar», «disponible», «fuera de servicio». Se envía con una tecla |
| **SDS tipo 1** | **16 bits** | Datos muy breves definidos por el usuario |
| **SDS tipo 2** | **32 bits** | Ídem |
| **SDS tipo 3** | **64 bits** | Ídem |
| **SDS tipo 4** | **hasta 2.047 bits** definidos por el usuario | **Texto libre**, posiciones GNSS, mensajes de aplicación. Es el que se usa en la práctica |

Sobre el tipo 4 se define además el **SDS-TL** (*SDS Transport Layer*), una capa de transporte que añade **identificación del protocolo de aplicación, acuse de recibo y encadenamiento**, y que es la base sobre la que funcionan la mensajería de texto real, el envío de posición y las aplicaciones de gestión.

> **[DATO CLAVE EXAMEN]** **Estado = 16 bits precodificados**; **SDS tipo 1 = 16 bits, tipo 2 = 32 bits, tipo 3 = 64 bits, tipo 4 = hasta 2.047 bits** definidos por el usuario. La distinción **estado / SDS tipo 4** es la más preguntada: el **estado** es un código de una lista cerrada que se envía con una tecla y consume casi nada; el **tipo 4** es carga útil libre. El **SDS-TL** es la capa que le añade acuse de recibo y encadenamiento.

**El uso masivo del SDS: la localización.** La aplicación que más tráfico SDS genera en una red real es el **envío periódico de la posición GNSS** de cada terminal al sistema de gestión de flotas. Se transporta en SDS tipo 4 mediante el **protocolo de información de localización (LIP)** normalizado por el ETSI, que define cómo se codifican coordenadas, precisión, velocidad y rumbo, y **bajo qué condiciones se emite** (por tiempo, por distancia recorrida, por cambio de estado o a petición).

> **[EJERCICIO RESUELTO]** **Dimensionar el tráfico de localización de una flota municipal.**
>
> **Supuesto**: **1.500 terminales** envían su posición **cada 60 segundos** mediante SDS tipo 4.
>
> **Paso 1 — Mensajes por segundo**: 1.500 / 60 = **25 mensajes por segundo** en el conjunto de la red.
>
> **Paso 2 — ¿Es mucho?** Los SDS viajan por **canales de control**, que están permanentemente activos y **no consumen canal de tráfico**. Pero la capacidad de señalización de una célula **no es infinita**: si esos 25 mensajes por segundo se concentran en pocas células —el centro de la ciudad—, pueden competir con la señalización de establecimiento de llamada.
>
> **Paso 3 — Qué se hace en la práctica**: (a) **espaciar** el intervalo de emisión cuando el vehículo está parado y acortarlo cuando se mueve; (b) usar emisión **por distancia recorrida** en lugar de por tiempo; (c) distribuir en el tiempo los envíos para evitar que todos los terminales emitan en el mismo segundo; y (d) reservar capacidad de señalización para el establecimiento de llamada, que **siempre** tiene prioridad sobre la telemetría.
>
> **Conclusión y trampa**: la respuesta «no consume nada porque va por el canal de control» es **incorrecta**. Consume **capacidad de señalización**, que es un recurso finito y compartido con el establecimiento de llamadas. Es el error de diseño más común en despliegues de localización sobre TETRA.

#### 4.2.2. Transmisión de datos por paquetes y circuitos

**Datos por circuito (*circuit mode data*).** Se **reserva un canal de tráfico** para el usuario durante toda la sesión, igual que en una llamada de voz. Las tasas por intervalo dependen del nivel de protección de errores elegido:

| Protección | Tasa por intervalo | Con los 4 intervalos |
|---|---|---|
| **Sin protección** | **7,2 kbit/s** | **28,8 kbit/s** |
| **Protección baja** | **4,8 kbit/s** | 19,2 kbit/s |
| **Protección alta** | **2,4 kbit/s** | 9,6 kbit/s |

Es un modo **ineficiente** para tráfico a ráfagas —el canal está reservado aunque no se transmita nada— pero **predecible**, y por eso se usa cuando hace falta un caudal garantizado: transferencia de un fichero, una imagen o una sesión de telemetría continua.

**Datos por paquetes (*packet data*, PD).** El terminal comparte los recursos con otros y **solo consume canal cuando hay paquetes que enviar**. TETRA transporta **IP** sobre este servicio mediante el protocolo **SNDCP** (*Subnetwork Dependent Convergence Protocol*) de la capa 3, de modo que, desde el punto de vista de la aplicación, **el terminal es un dispositivo IP más**. Es el modo adecuado para consultas a sistemas de información, mensajería de aplicación y sincronización de datos.

> **[DATO CLAVE EXAMEN]** **Circuito = recurso reservado, tasa garantizada, ineficiente para tráfico a ráfagas. Paquetes = recurso compartido, transporte de IP mediante SNDCP, eficiente para tráfico a ráfagas.** Y el techo de TETRA Release 1, que es la cifra que hay que retener: **28,8 kbit/s** con los cuatro intervalos y sin protección de errores. Ese techo es la razón de ser de **TEDS** (§5.4).

**Qué se puede y qué no se puede hacer con esas cifras.** Con 28,8 kbit/s en el mejor de los casos —y realistamente con 7,2 o 14,4 kbit/s— se pueden hacer: mensajería de texto, envío de posiciones, consultas a bases de datos con respuestas breves, formularios, telemetría, envío de una fotografía comprimida en decenas de segundos y actualización de datos operativos. **No** se pueden hacer: vídeo, transmisión de planos o imágenes grandes en tiempo real, acceso a aplicaciones web modernas ni transferencia de ficheros de tamaño ordinario.

> **[EJEMPLO AYTO MADRID]** Ese límite explica una realidad muy visible en la operativa municipal: los servicios de emergencia trabajan con **dos canales de datos en paralelo**. La **radio TETRA** transporta lo crítico y lo breve —estados, posiciones, órdenes, avisos— con disponibilidad garantizada; y una **conexión de datos comercial** (4G/5G) transporta lo voluminoso —imágenes, historia clínica, cartografía, vídeo— **sin garantía de disponibilidad**. La consecuencia operativa es clara y conviene tenerla presente en cualquier caso práctico: **lo que no puede fallar va por la radio propia; lo que aporta valor pero puede esperar va por la red comercial**. La convergencia de ambos mundos es lo que persigue la banda ancha crítica (§5.4).

> **[REFERENCIA CRUZADA]** El transporte de **IP** sobre un enlace de radio de baja capacidad, el efecto del retardo y de la pérdida sobre TCP y los mecanismos de compresión de cabeceras se tratan en el **Tema 34**. El diseño de aplicaciones que funcionen sobre enlaces así —peticiones pequeñas, tolerancia a la desconexión, sincronización diferida— es materia del **Tema 24**.

### 4.3. Mecanismos de seguridad

**El planteamiento.** La seguridad de TETRA se apoya en **cuatro pilares**, y conviene tenerlos separados desde el principio porque cada uno protege de una cosa distinta:

1. **Autenticación**: garantizar que el terminal es quien dice ser y —en la autenticación mutua— que la red también lo es.
2. **Cifrado de la interfaz aire (AIE)**: proteger lo que viaja **entre el terminal y la estación base**.
3. **Cifrado extremo a extremo (E2EE)**: proteger lo que viaja **entre terminal y terminal**, atravesando la infraestructura sin que ésta pueda leerlo.
4. **Protección de identidades**: evitar que un observador pueda **identificar y seguir** a los usuarios.

A ellos se añaden la **inhabilitación remota** de terminales (§4.1.1) y la **gestión de claves**, incluida su distribución **por el aire (OTAR)**.

> **[DATO CLAVE EXAMEN]** La distinción decisiva del apartado: **el cifrado de interfaz aire protege el tramo radio y se descifra en la estación base**; **el cifrado extremo a extremo protege el contenido de punta a punta y la infraestructura no puede leerlo**. Son **complementarios**, no alternativos. Todo lo demás de esta sección se ordena alrededor de esa frase.

#### 4.3.1. Autenticación de usuarios y terminales

**El esquema, en cuatro pasos.** TETRA usa un mecanismo de **desafío-respuesta** con **clave simétrica**, normalizado en la **EN 300 392-7** `[EN392-7]` con los algoritmos del conjunto **TAA1** (*TETRA Authentication Algorithm set 1*):

1. Cada terminal comparte con el **centro de autenticación** de la red una **clave de autenticación secreta**, denominada **K**, que **nunca viaja por el aire**.
2. Cuando el terminal se registra, la red le envía un **desafío** (un número aleatorio).
3. El terminal calcula una **respuesta** aplicando el algoritmo a la clave y al desafío, y la envía.
4. La red hace el mismo cálculo por su cuenta y **compara**. Si coincide, el terminal queda autenticado.

**La autenticación mutua.** El mismo mecanismo puede ejecutarse **en sentido contrario**, de modo que **el terminal verifique a la red**. Es esencial: sin autenticación de la red, un atacante puede montar una **estación base falsa** que atraiga a los terminales de la zona —el equivalente radioeléctrico de un punto de acceso *rogue*— y desde ella degradar la seguridad, capturar tráfico o inyectar mensajes.

> **[DATO CLAVE EXAMEN]** La autenticación de TETRA es **simétrica, de desafío-respuesta**, con la clave **K** que **no se transmite nunca**, y **puede ser mutua**. La autenticación mutua es la defensa contra la **estación base falsa**. La familia de algoritmos original es **TAA1**; el conjunto nuevo, asociado al TEA set B, es **TAA2**, y trabaja con una clave de autenticación denominada **K2** `[TTR001-11]`.

**Y el subproducto más importante de la autenticación: la clave de sesión.** Del proceso de autenticación se **deriva** una clave de cifrado propia de ese terminal y de esa sesión, la **DCK** (*Derived Cipher Key*). Es decir: **autenticar y cifrar están encadenados**. Una red que no autentica no puede usar claves derivadas y tiene que conformarse con claves estáticas precargadas, mucho más débiles porque **son las mismas para todos y durante mucho tiempo**.

**La jerarquía de claves, que se pregunta.**

| Clave | Nombre | Qué protege | Cómo se obtiene |
|---|---|---|---|
| **K** | *Authentication Key* | Es la raíz: **no cifra tráfico**, solo autentica | Precargada de forma segura; nunca viaja |
| **DCK** | *Derived Cipher Key* | Tráfico **individual** de ese terminal | **Se deriva de la autenticación** |
| **CCK** | *Common Cipher Key* | Tráfico y señalización **dirigidos a grupo** dentro de un área de localización | La genera la red y la distribuye **cifrada con la DCK**, por OTAR |
| **SCK** | *Static Cipher Key* | Tráfico, en redes **sin autenticación** y en **modo directo** | **Precargada**; es la opción más débil |
| **GCK** | *Group Cipher Key* | Un **grupo concreto**, con independencia de la célula | No se usa directamente en el aire: se combina con CCK o SCK para dar la **MGCK** |
| **MGCK** | *Modified Group Cipher Key* | La que efectivamente cifra el tráfico de grupo protegido | **GCK modificada** por CCK o SCK |

**OTAR** (*Over The Air Re-keying*), **la distribución de claves por el aire**, es lo que hace manejable todo lo anterior: permite **renovar las claves de miles de terminales sin recogerlos**, algo imprescindible cuando una clave se compromete o cuando se da de baja a un usuario. Las claves viajan **selladas** con otra clave, nunca en claro.

> **[REFERENCIA CRUZADA]** Los conceptos de **clave simétrica**, **desafío-respuesta**, **derivación de claves** y **gestión del ciclo de vida de las claves** se desarrollan en el **Tema 32**. La obligación jurídica de proteger el material criptográfico está en la medida **`op.exp.10`, «protección de claves criptográficas», del ENS** `[ENS]`, y es directamente aplicable a la gestión de claves de una red TETRA municipal.

#### 4.3.2. Cifrado en la interfaz aire

**Qué protege y qué no.** El **cifrado de interfaz aire** (**AIE**, *Air Interface Encryption*) cifra **todo lo que viaja por radio entre el terminal y la estación base**: la voz, los datos, la señalización y —si se activa el cifrado de identidades— las propias identidades. Se aplica en la **capa 2** del interfaz aire. **Se descifra en la estación base**: a partir de ahí, la comunicación circula por la infraestructura del operador de la red **en claro**, salvo que se aplique cifrado adicional en el transporte o cifrado extremo a extremo.

> **[DATO CLAVE EXAMEN]** El AIE **no protege frente al propio operador de la red**, porque el tráfico se descifra en la estación base. Protege frente a **quien escucha el aire**. Es exactamente la razón por la que los usuarios más exigentes añaden **cifrado extremo a extremo** (§4.3.3).

**Las clases de seguridad.** El estándar define tres, y hay que saberlas `[TTR001-11]`:

| Clase | Denominación | Qué usa | Comentario |
|---|---|---|---|
| **SC1** | Clase de seguridad 1 | **Sin cifrado** del interfaz aire | Puede usarse autenticación y cifrado de identidades (ESI), pero el tráfico va **en claro** |
| **SC2** | Clase de seguridad 2 | **Clave estática, SCK** | Cifrado con clave precargada. **No exige autenticación**. Es también la clase del **modo directo** |
| **SC3** | Clase de seguridad 3 | **Clave derivada (DCK) + clave común (CCK)** | Exige **autenticación**; la clave es distinta por terminal y se renueva. Es la configuración recomendada |
| **SC3G** | Clase 3 con **GCK** | DCK + CCK + **GCK/MGCK** | Añade cifrado propio por grupo |

El informe técnico de la TCCA recoge además un detalle operativo relevante: la red puede usar **SC2 como modo de repliegue** para células que temporalmente **no pueden sostener SC3** —por ejemplo, porque han perdido el enlace con el centro de autenticación—, con notificación anticipada del cambio de clase `[TTR001-11]`.

**El cifrado de identidades.** Para evitar que un observador identifique y siga a los usuarios, TETRA cifra las identidades cortas: la **ESI** (*Encrypted Short Identity*) sustituye la identidad por una versión cifrada, y el TEA set B añade la **MAE** (*MAC Address Encryption*) `[TTR001-11]`.

**Los algoritmos: TEA set A.** El cifrado se realiza con generadores de flujo de clave denominados **TEA** (*TETRA Encryption Algorithm*). El conjunto original, **TEA set A**, tiene cuatro:

| Algoritmo | Destinatario previsto | Régimen de exportación |
|---|---|---|
| **TEA1** | **Uso civil general e infraestructuras críticas**, con exportación mundial | **Longitud de clave efectiva reducida** para cumplir controles de exportación |
| **TEA2** | **Servicios de emergencia europeos** (esquema Schengen) | Restringido |
| **TEA3** | Servicios de emergencia y militares **fuera de Europa**, en países afines | Restringido |
| **TEA4** | Uso civil general, variante de TEA1 | Restringido |

> **[DATO CLAVE EXAMEN]** **TEA1 y TEA4** son los de uso **civil y exportación amplia**; **TEA2** es el de las **redes de emergencia europeas**; **TEA3**, el de emergencia y militar **extraeuropeo**. La clave nominal de todos ellos es de **80 bits**, pero **TEA1 tiene una reducción deliberada de la longitud efectiva**. Los algoritmos fueron **secretos** durante casi treinta años; el ETSI publicó la especificación del **TEA set A** en la **TS 104 053-1** en **febrero de 2025** `[TS104053]`.

**TETRA:BURST: la investigación que cambió el escenario.** En **agosto de 2023**, el equipo neerlandés **Midnight Blue** publicó, tras un proceso de divulgación coordinada y con un artículo revisado en **USENIX Security 2023**, cinco vulnerabilidades bautizadas como **TETRA:BURST** `[TETRABURST]`. Las cuatro citables son:

- **CVE-2022-24402 — la puerta trasera de TEA1.** La clave de **80 bits** de TEA1 se **comprime deliberadamente** a una longitud efectiva de **unos 32 bits**, lo que permite **romperla por fuerza bruta en minutos con un ordenador doméstico**. La TCCA ha confirmado que la reducción fue intencionada y la justifica en el cumplimiento del **Acuerdo de Wassenaar** de control de exportación de tecnología criptográfica `[TCCA-RD]`.
- **CVE-2022-24401 — el oráculo de descifrado.** El generador del flujo de clave del AIE depende del **tiempo de red**, que la estación base **difunde sin autenticar**. Manipulándolo, un atacante puede forzar la **reutilización del flujo de clave** y descifrar comunicaciones.
- **CVE-2022-24403 — desanonimización.** El esquema de ofuscación de identidades tiene un diseño débil que permite **identificar y seguir** a los usuarios.
- **CVE-2022-24404 — maleabilidad.** La falta de autenticación del texto cifrado permite **alterar el mensaje cifrado** sin ser detectado.

**La respuesta del ETSI: TEA set B.** En **octubre de 2022** —antes de la publicación de la investigación, con la que la divulgación estaba coordinada— el ETSI liberó un **nuevo conjunto de algoritmos**, el **TEA set B**, con tres piezas `[TCCA-B]`:

| Nuevo | Sustituye a | Destinatario |
|---|---|---|
| **TEA5** | TEA2 | **Redes de emergencia europeas** |
| **TEA6** | TEA3 | Redes de emergencia y militares extraeuropeas afines |
| **TEA7** | TEA1 | **Infraestructuras críticas y uso civil general** — es el único del set B disponible para uso civil amplio |

El TEA set B trabaja con **claves extendidas** —SCKX, DCKX, CCKX, GCKX— y con el nuevo conjunto de autenticación **TAA2** y su clave **K2** `[TTR001-11]`. Según la TCCA, **TEA5 y TEA6 usan claves de 192 bits**, mientras que **TEA7 conserva una reducción de la longitud efectiva a 56 bits** por las mismas razones de control de exportación que en su día afectaron a TEA1 `[TCCA-RD]`.

> **[DATO CLAVE EXAMEN]** **TEA set B = TEA5, TEA6 y TEA7, liberado en octubre de 2022.** Correspondencias: **TEA5 ← TEA2**, **TEA6 ← TEA3**, **TEA7 ← TEA1**. Y el matiz que se pregunta: **TEA7, el civil, sigue teniendo una longitud de clave efectiva reducida (56 bits)** por el régimen de exportación, mientras que TEA5 y TEA6 llevan **192 bits**. La lección de fondo, muy citable: **la debilidad de TEA1 no fue un error de diseño, sino una decisión de política de exportación**.

**2TETRA:2BURST (agosto de 2025).** El mismo equipo presentó en **Black Hat USA el 7 de agosto de 2025** una segunda tanda `[2TETRA]`, y su alcance es mayor porque **llega al cifrado extremo a extremo**:

- **CVE-2025-52944** — **el protocolo TETRA carece de autenticación de mensajes**, lo que permite **inyectar mensajes arbitrarios**. Es la más estructural de todas.
- **CVE-2025-52943** — en redes **multicifrado**, admitir **TEA1** junto a otros algoritmos permite **recuperar la clave** también de los demás. Traducción operativa: **no basta con dejar de usar TEA1; hay que dejar de soportarlo**.
- **MBPH-2025-001** — la corrección publicada por el ETSI para **CVE-2022-24401** **no impide** la recuperación del flujo de clave.
- **CVE-2025-52940, 52941 y 52942** — afectan al **cifrado extremo a extremo** y se tratan en §4.3.3.

> **[DATO CLAVE EXAMEN]** Dos hallazgos de 2025 con consecuencia práctica inmediata para un gestor de red: **(1) soportar TEA1 «por compatibilidad» compromete también a los algoritmos fuertes de la misma red** (CVE-2025-52943); y **(2) el protocolo no autentica los mensajes** (CVE-2025-52944), de modo que la integridad depende de las capas superiores. La primera es la que convierte «desactivar TEA1» en una **decisión de configuración obligatoria**, no en una recomendación.

**Cómo debe leerse todo esto, sin alarmismo y sin complacencia.** Tres precisiones que conviene sostener en un examen o en un informe:

1. **Ninguna de estas vulnerabilidades hace inútil a TETRA.** Explotarlas exige proximidad radioeléctrica, equipamiento específico y capacidad técnica alta; el perfil de atacante es de gama alta, no oportunista.
2. **Pero sí obligan a decisiones concretas**: usar **SC3** con **autenticación mutua**, **no soportar TEA1**, migrar a **TEA set B** y **TAA2** cuando el parque lo permita, activar el **cifrado de identidades**, aplicar los parches del fabricante y **añadir cifrado extremo a extremo** en las comunicaciones sensibles.
3. **Y dejan una lección de método**: la seguridad por oscuridad falló. Los algoritmos estuvieron **secretos treinta años** y su debilidad se descubrió **en cuanto se pudieron examinar**. La publicación del TEA set A en 2025 es el reconocimiento implícito de ese principio.

> **[EJEMPLO AYTO MADRID]** Para una red municipal, la traducción de lo anterior a un pliego es directa y es exactamente lo que un examinador espera ver: exigir **clase de seguridad SC3** con **autenticación mutua** como configuración por defecto; **prohibir expresamente TEA1** en la red, no solo «no usarlo»; exigir **capacidad de migración a TEA set B y TAA2** en los terminales que se adquieran a partir de ahora; exigir **OTAR** para poder renovar claves sin recoger 4.500 equipos; y exigir **procedimiento documentado de inhabilitación remota** de terminales perdidos. Todo ello con respaldo normativo en el ENS: **`mp.com.2`** (confidencialidad), **`mp.com.3`** (integridad y autenticidad), **`mp.si.2`** (criptografía) y **`op.exp.10`** (protección de claves criptográficas) `[ENS]`.

#### 4.3.3. Cifrado extremo a extremo (E2EE)

**Qué añade.** El **cifrado extremo a extremo** (**E2EE**) cifra la información **en el terminal emisor** y la descifra **en el terminal receptor**, de modo que **atraviesa toda la infraestructura sin que ésta pueda leerla**. Es una capa **superior e independiente** del cifrado de interfaz aire, y se aplica **sobre la carga útil** —la voz codificada o el SDS— antes de que ésta entre en la pila de protocolos.

**De qué protege que el AIE no proteja:**

- Del **operador de la red**, si es un tercero (una empresa que presta el servicio, otra Administración que aloja la infraestructura).
- Del **personal técnico** con acceso a los equipos de conmutación o a las grabaciones.
- De un **compromiso de la infraestructura**, incluidas las estaciones base y los enlaces de transporte.
- De la **interconexión con otras redes**, donde el tráfico pasa por sistemas ajenos.

**Cómo se implementa.** El ETSI **no impone un algoritmo** de E2EE: define el **marco** —cómo se sincroniza, cómo se transporta el material cifrado dentro de la trama de voz, cómo se gestionan las claves— y deja que cada comunidad de usuarios elija su criptografía. Históricamente se usó **IDEA**; hoy predomina **AES**, en variantes de 128 o 256 bits. La gestión de claves E2EE es **independiente** de la de la red: normalmente se apoya en un **centro de gestión de claves propio del usuario final**, con distribución por OTAR o por carga física, y las claves **no las conoce el operador**.

**El coste que hay que asumir.** El E2EE tiene tres contrapartidas honestas que un informe debe recoger:

1. **La red no puede procesar lo que no entiende.** Las pasarelas telefónicas, la grabación centralizada en claro y la interconexión con redes de otra tecnología **dejan de funcionar** sobre el tráfico cifrado extremo a extremo, salvo que se prevean puntos de descifrado autorizados.
2. **La gestión de claves es responsabilidad del usuario**, y su complejidad crece con el tamaño de la flota y con la necesidad de interoperar con otros organismos.
3. **Consume capacidad**: la sincronización del cifrado ocupa bits que salen del caudal de voz, con un impacto pequeño pero no nulo.

> **[DATO CLAVE EXAMEN]** **AIE = terminal ↔ estación base; se descifra en la red. E2EE = terminal ↔ terminal; la red no puede leerlo.** Se usan **juntos**. El ETSI **no normaliza el algoritmo de E2EE**, solo el marco de transporte y sincronización; el algoritmo predominante hoy es **AES**.

**El hallazgo de 2025 sobre el E2EE.** La segunda tanda de Midnight Blue alcanzó precisamente a esta capa `[2TETRA]`:

- **CVE-2025-52941** — se identificó una **variante debilitada de AES-128** en la que la **entropía efectiva se reduce a 56 bits** en lugar de 128. Es, funcionalmente, **el mismo patrón que el de TEA1**, ahora en la capa que se suponía la última línea de defensa.
- **CVE-2025-52940** — la voz cifrada extremo a extremo es vulnerable a **ataques de repetición** e **inyección de voz**.
- **CVE-2025-52942** — los **SDS** cifrados extremo a extremo **carecen de protección antirrepetición**, de modo que un mensaje capturado puede reinyectarse tal cual.

> **[DATO CLAVE EXAMEN]** El **E2EE no es una garantía automática**: depende del algoritmo **concreto** que se haya implantado y de si incorpora **protección antirrepetición** y **autenticación del mensaje**. La lección para un pliego es que **no basta con exigir «cifrado extremo a extremo»**: hay que exigir **algoritmo y longitud de clave nombrados**, **protección frente a repetición** y **autenticación del contenido**, y reservarse el derecho de auditar la implementación.

> **[REFERENCIA CRUZADA]** La distinción entre **cifrado en tránsito por tramos** y **cifrado extremo a extremo**, y la razón por la que el segundo no sustituye al primero, es la misma que aparece en el **Tema 35** a propósito de TLS y en el **Tema 36** a propósito de las VPN. Los conceptos de **entropía de clave**, **ataque de repetición** y **autenticación de mensaje** están en el **Tema 32**.
---
## 5. Ámbito público, normativa y evolución tecnológica

### 5.1. Uso de TETRA en servicios de emergencia y seguridad pública

**Por qué TETRA se impuso en este sector.** Las funciones descritas en §4 no son adornos: cada una responde a una necesidad operativa que la telefonía comercial no cubre. Puestas en fila, explican la elección:

| Necesidad operativa | Lo que aporta TETRA | Lo que ofrece un móvil comercial |
|---|---|---|
| Hablar **a todo un equipo** a la vez | **Llamada de grupo** nativa, con un botón | Grupos de mensajería o multiconferencia, con establecimiento lento |
| **Inmediatez** | Establecimiento **< 300 ms** | Segundos |
| **Garantía de acceso** en saturación | **Prioridad y desalojo** decididos por el titular de la red | Ninguna; el operador no da prioridad al ayuntamiento |
| Funcionar **sin infraestructura** | **Modo directo (DMO)** | Imposible |
| Funcionar **cuando cae la luz** | Emplazamientos con **baterías y grupos electrógenos** dimensionados por el titular | Depende del respaldo de un tercero |
| **Confidencialidad** de la comunicación operativa | **AIE + E2EE** con claves propias | Cifrado del operador, sin control del usuario |
| **Trazabilidad** | Grabación e identidad en todas las transmisiones | No integrada |
| **Terminal de trabajo** | Robusto, con PTT, botón de emergencia, «hombre caído» | Terminal de consumo |

> **[DATO CLAVE EXAMEN]** Las **cinco** razones que justifican una red propia de radio frente a la telefonía comercial, y que conviene saber enumerar de corrido: **grupo, inmediatez, prioridad garantizada, funcionamiento sin infraestructura y control de la disponibilidad por su titular**. Ninguna de ellas es una cuestión de calidad de audio ni de cobertura: son cuestiones de **control**.

**El mapa español, que es donde está la trampa del tema.** En España conviven tres niveles de red de emergencia, y **no todos usan la misma tecnología**:

| Nivel | Red | Tecnología | Usuarios |
|---|---|---|---|
| **Estatal** | **SIRDEE** | **TETRAPOL** | Fuerzas y Cuerpos de Seguridad del Estado, Defensa y, con terminales cedidos, otros servicios de emergencia |
| **Autonómico** | Redes propias de las comunidades autónomas | **TETRA** en la mayoría de los casos | Bomberos autonómicos, agentes forestales, emergencias sanitarias, 112, protección civil, policías locales adheridas |
| **Local** | Redes municipales de las grandes ciudades | **TETRA** | Policía local, bomberos municipales, emergencias, servicios urbanos |

> **[DATO CLAVE EXAMEN]** **El SIRDEE —Sistema de Radiocomunicaciones Digitales de Emergencia del Estado, en servicio desde el año 2000— está construido sobre TETRAPOL, no sobre TETRA** `[SIRDEE]`. Es **la** confusión del tema. La razón histórica es que su despliegue se decidió a finales de los años noventa, cuando TETRA aún no estaba maduro comercialmente y TETRAPOL sí. Las redes **autonómicas y municipales**, decididas más tarde, se hicieron en su mayoría **con TETRA**. La consecuencia práctica es que **la interoperabilidad entre el nivel estatal y los otros dos no puede resolverse con la ISI**, sino con pasarelas o con acoplamiento en los centros de mando (§2.3.2).

**La red autonómica madrileña.** La Comunidad de Madrid opera su propia red TETRA, gestionada por la **Agencia de Seguridad y Emergencias Madrid 112 (ASEM 112)**, con **113 estaciones base** y **5.316 terminales** `[CM-TETRA]`. Da servicio al **Cuerpo de Bomberos**, **Agentes Forestales**, brigadas forestales, **ERIVE** de protección civil, personal sanitario del **SUMMA 112**, grupos de protección civil, **policías locales** adheridas a la estrategia de seguridad autonómica y la **Dirección General de Carreteras**. La red permite además la **geolocalización de cada terminal**, cuya posición se envía al centro de control del servicio correspondiente. Los datos económicos recientes: casi **40 millones de euros a cinco años** para su modernización y gestión (agosto de 2025) y **6,1 millones** en el ejercicio 2025, con **2.263 terminales nuevos** repartidos entre Bomberos (1.600), Agentes Forestales (412), Protección Civil (140), Carreteras (66) y Madrid 112 (45) `[CM-TETRA]`.

**Y un dato de 2026 que vale por toda una argumentación.** En **mayo de 2026**, la Comunidad de Madrid dotó de un terminal TETRA a **53 municipios pequeños** que no lo tenían, para garantizar su contacto con el 112. El motivo declarado es el análisis del **apagón del 28 de abril de 2025**: el estudio posterior constató que **las redes TETRA mantuvieron su operatividad durante el corte de suministro**, porque los repetidores cuentan con **baterías de respaldo**, mientras la telefonía convencional y el acceso a internet se degradaron `[CM-TETRA]`.

> **[DATO CLAVE EXAMEN]** El **apagón peninsular del 28 de abril de 2025** es el argumento empírico más potente a favor de una red de radio propia, y por su actualidad es candidato natural a pregunta de caso práctico: **la red TETRA siguió funcionando cuando la telefonía comercial no**, gracias al **respaldo energético de los emplazamientos**. La lección de fondo no es sobre radio, sino sobre **dependencias**: un servicio crítico solo es resiliente si lo son **todas** sus dependencias, empezando por la energía.

> **[EJEMPLO AYTO MADRID]** La red municipal, sobre plataforma **DIMETRA-TETRA**, da servicio a **Policía Municipal, Bomberos, SAMUR-Protección Civil, Agentes de Movilidad, SAMUR Social y Parques y Jardines**, coordinando a **más de 3.000 efectivos**, y su mantenimiento integral y evolución tecnológica se adjudicaron en **marzo de 2026** por **cinco años**, con **disponibilidad 24×7** `[TELEFONICA-2026]`. En **julio de 2026**, la Junta de Gobierno aprobó además el contrato de **operación, gestión, supervisión y mantenimiento de las infraestructuras, equipos y redes de radiocomunicaciones** de la Dirección General de Policía Municipal, con **933.000 euros** de presupuesto plurianual y **tres años** de duración prorrogables `[AYTO-CONTR]`. Obsérvese que son **dos contratos distintos**: uno sobre **la plataforma** y otro sobre **la operación y las redes de un cuerpo concreto**. Distinguir el objeto de cada uno es exactamente el tipo de precisión que se pide en un caso práctico.

**Otros usos de TETRA que conviene citar.** Fuera de la seguridad pública, TETRA se emplea en **transporte** (metros, ferrocarriles, aeropuertos, puertos, flotas de autobuses), **energía y agua** (redes de distribución, telemando), **industria** (minería, petroquímica), **grandes recintos** y **defensa**. El caso más visible en Madrid es el **Metro**, con despliegues de TETRA por tramos para comunicar el Puesto de Mando con estaciones y trenes `[METRO]`.

> **[REFERENCIA CRUZADA]** El encuadre de estas redes como **infraestructura crítica** —con las obligaciones de la **Ley 8/2011** y de la futura transposición de **NIS2**— enlaza con el **Tema 32** (seguridad de los sistemas de información) y con el **Tema 39** (ENS). La coordinación entre administraciones en emergencias es materia de la **Ley 17/2015** del Sistema Nacional de Protección Civil.

### 5.2. Marco normativo y regulación del espectro radioeléctrico

**El punto de partida: el espectro es dominio público.** El art. **85.1** de la Ley 11/2022 lo dice sin matices: «**El espectro radioeléctrico es un bien de dominio público, cuya titularidad y administración corresponden al Estado**» `[LGTel]`. De ahí se deducen las tres consecuencias que se preguntan: **(1)** nadie es propietario de una frecuencia; **(2)** su uso requiere **título habilitante** estatal; y **(3)** ese título está **sujeto a condiciones**, tiene **plazo** y puede **modificarse o revocarse**.

**La pirámide normativa del espectro, de arriba abajo:**

1. **Reglamento de Radiocomunicaciones de la UIT**, tratado internacional que reparte el espectro entre servicios y **regiones** (España está en la **Región 1**), revisado por las **Conferencias Mundiales de Radiocomunicaciones**; la última incorporada es la **CMR-23**.
2. **Derecho de la Unión Europea**: decisiones de armonización de la Comisión y **decisiones y recomendaciones de la CEPT/ECC**, que son las que fijan bandas comunes europeas. Las tres relevantes aquí: **ECC/DEC(08)05** (emergencias en 380-385/390-395 MHz), **ECC/DEC(06)06** (PMR/PAMR digital de banda estrecha) y **ECC/DEC(16)02** (PPDR de banda ancha).
3. **Ley 11/2022, General de Telecomunicaciones**, título V, arts. 85 y siguientes.
4. **Real Decreto 123/2017**, Reglamento sobre el uso del dominio público radioeléctrico, cuyo **art. 6** ordena aprobar el CNAF.
5. **CNAF**, aprobado por **Orden TDF/732/2026, de 10 de julio**, con sus **notas de utilización nacional (UN)**.

**Las tres modalidades de uso, art. 88.1 de la Ley 11/2022** `[LGTel]`:

| Modalidad | Definición legal | Ejemplos |
|---|---|---|
| **Común** | **No precisa título habilitante**; se realiza en las bandas y con las características que se establezcan | Wi-Fi, mandos a distancia, dispositivos de corto alcance |
| **Especial** | Bandas habilitadas para **explotación compartida**, **sin limitación de número** de operadores o usuarios | Radioafición, banda ciudadana |
| **Privativo** | Explotación **en exclusiva o por un número limitado de usuarios** de determinadas frecuencias en un mismo ámbito físico | Telefonía móvil, radiodifusión y **las redes TETRA de emergencia** |

**Las cuatro formas de título habilitante, art. 88.3:** **autorización general**, **autorización individual**, **afectación** y **concesión** administrativas. Y ahora el precepto que hay que saber literalmente:

> **[DATO CLAVE EXAMEN]** **Art. 88.5.b) de la Ley 11/2022**: el derecho de uso **privativo para autoprestación** se otorga mediante **autorización individual**, «**salvo en el caso de Administraciones públicas, que requerirán de afectación demanial**» `[LGTel]`. Es decir: **la red TETRA de un ayuntamiento se ampara en una AFECTACIÓN DEMANIAL, no en una concesión ni en una autorización individual**. Y una **concesión administrativa** exige además, según el art. 88.6, que el solicitante **ostente la condición de operador de comunicaciones electrónicas**, que no es el caso de un ayuntamiento que se autopresta el servicio. Éste es el dato jurídico más específico del tema y el que distingue una respuesta buena de una excelente.

**La duración.** El art. **94.1** fija que los derechos de uso privativo **sin limitación de número** se otorgan «por un período que finalizará el **31 de diciembre del año natural en que cumplan su quinto año de vigencia**», **renovables por períodos de cinco años** en función de las disponibilidades y de la planificación `[LGTel]`. Es decir: **cinco años, con renovación periódica**, no indefinido.

**Las condiciones asociadas.** El art. **91** somete el título a condiciones sobre uso efectivo y eficiente, características técnicas, prevención de interferencias, límites de exposición y pago de la **tasa por reserva del dominio público radioeléctrico**. El incumplimiento puede llevar a la **modificación, extinción o revocación** del título (art. 95).

**Y la calificación jurídica del servicio.** El art. **4.1** de la Ley 11/2022 contiene una declaración con mucho recorrido: «**Sólo tienen la consideración de servicio público los servicios regulados en este artículo**», y el artículo se titula precisamente «**Servicios de telecomunicaciones para la seguridad nacional, la defensa nacional, la seguridad pública, la seguridad vial y la protección civil**» `[LGTel]`. Es decir: en un ordenamiento que declara las telecomunicaciones **servicios de interés general prestados en libre competencia**, las comunicaciones para **seguridad pública y protección civil** son la **excepción** expresamente calificada como servicio público.

> **[DATO CLAVE EXAMEN]** **Art. 4.1 de la Ley 11/2022**: los servicios de telecomunicaciones para la **seguridad nacional, la defensa, la seguridad pública, la seguridad vial y la protección civil** son **los únicos** que tienen la consideración de **servicio público**. Es el fundamento jurídico de fondo de todo este tema y encaja con el art. **2**, que declara al resto de las telecomunicaciones servicios **de interés general en régimen de libre competencia**.

> **[EJERCICIO RESUELTO]** **Determinar el régimen jurídico completo de la red TETRA de un ayuntamiento.**
>
> **Pregunta**: un ayuntamiento explota una red TETRA propia para sus servicios de seguridad y emergencias. ¿Qué modalidad de uso del espectro es, qué título habilitante necesita, cuánto dura y qué obligaciones asume?
>
> **Paso 1 — Modalidad de uso.** Emplea **frecuencias determinadas en exclusiva** en su ámbito físico → **uso privativo** (art. 88.1).
>
> **Paso 2 — ¿Autoprestación o prestación a terceros?** La red sirve **a los propios servicios municipales**, no se vende a terceros → **autoprestación**.
>
> **Paso 3 — Título habilitante.** Uso privativo + autoprestación + **Administración pública** → **afectación demanial** (art. **88.5.b**). **No** es autorización individual (que sería la de un particular en autoprestación) ni concesión (que exigiría ser operador, art. 88.6).
>
> **Paso 4 — Duración.** Régimen general del art. **94.1**: hasta el **31 de diciembre del quinto año**, **renovable por períodos de cinco años**.
>
> **Paso 5 — Bandas.** Según el servicio: **380-385 / 390-395 MHz** si es red de servicios de emergencia (nota **UN-28**); **410-415,3 / 420-425,3 MHz** si es TETRA civil (nota **UN-31**), con canalización de **25 kHz** y dúplex de **10 MHz**.
>
> **Paso 6 — Obligaciones.** Condiciones del art. **91** (uso eficaz y eficiente, características técnicas, no interferencia, exposición radioeléctrica), **tasa por reserva del dominio público radioeléctrico**, y —por ser un sistema de información del sector público— las medidas del **ENS** que le apliquen según su categoría.
>
> **Paso 7 — Y una precisión final.** Si el ayuntamiento **cediera capacidad excedente** de su red a terceros, cambiaría la calificación de la actividad y entrarían en juego las obligaciones de la Ley 11/2022 sobre redes de las Administraciones públicas. La autoprestación **pura** es lo que sostiene el régimen anterior.

**El ENS aplicado a una red de radio.** Un sistema de radiocomunicaciones municipal es un **sistema de información del sector público** y le aplica el **Esquema Nacional de Seguridad**. Las medidas más directamente pertinentes `[ENS]`:

- **`mp.com.1` — Perímetro seguro**, **`mp.com.2` — Protección de la confidencialidad** y **`mp.com.3` — Protección de la integridad y de la autenticidad**: dan cobertura normativa al cifrado y a la autenticación del interfaz aire.
- **`mp.com.4` — Separación de flujos de información en la red**, con su requisito **`mp.com.4.2`**: «**si se emplean comunicaciones inalámbricas, será en un segmento separado**». Es la medida que exige que la red radio **no comparta segmento** con la ofimática municipal. Sus refuerzos: **R1** segmentación lógica con **VLAN** (con subredes mínimas de usuarios, servicios y administración), **R2** con **VPN**, **R3** con **medios físicos separados** y **R4** control en los **puntos de interconexión**. Obsérvese que **no aplica en categoría BÁSICA**, y que en MEDIA exige **[R1 o R2 o R3]**.
- **`mp.if.1` a `mp.if.7` — Protección de las instalaciones**: áreas separadas con control de acceso, identificación de personas, acondicionamiento de los locales, **`mp.if.4` energía eléctrica**, incendios, inundaciones y registro de entrada y salida de equipamiento. Se aplican a **cada emplazamiento de estación base**, no solo al CPD.
- **`op.cont.1` a `op.cont.4` — Continuidad del servicio**: análisis de impacto, plan de continuidad, pruebas periódicas y **medios alternativos**.
- **`mp.si.2` — Criptografía** y **`op.exp.10` — Protección de claves criptográficas**.

> **[DATO CLAVE EXAMEN]** **`mp.com.4.2` del ENS: «si se emplean comunicaciones inalámbricas, será en un segmento separado»** `[ENS]`. Es el precepto que se cita cuando alguien propone conectar la consola de despacho a la red ofimática general o dar salida a internet desde el segmento de la red radio. Y **`mp.if.4`, energía eléctrica**, es el que respalda exigir baterías y grupos electrógenos en los emplazamientos: aplica **ya en categoría BÁSICA**, con refuerzo **R1** en MEDIA y ALTA.

### 5.3. Requisitos de disponibilidad, resiliencia y calidad de servicio (QoS)

**El nivel de exigencia.** En una red de emergencia, la disponibilidad no se expresa en «tres nueves»: se expresa en **99,99 %** o superior, y se acompaña de un requisito adicional que las redes ordinarias no tienen: **la red debe seguir funcionando precisamente cuando el entorno falla**, porque es entonces cuando más se necesita. Una red comercial se degrada con la emergencia; una red de emergencia debe resistirla.

**Las capas de resiliencia, de fuera adentro:**

**1. Energía.** Es la primera y la que el apagón de abril de 2025 puso a prueba. Cada emplazamiento debe tener **baterías** dimensionadas para varias horas y, en los principales, **grupo electrógeno** con combustible y procedimiento de reposición. El ENS lo respalda en **`mp.if.4`** `[ENS]`.

**2. Transporte.** El enlace entre estaciones base y nodos debe estar **duplicado por caminos físicamente diversos**, y conviene que las tecnologías sean distintas (fibra + radioenlace), para que un mismo suceso no corte las dos.

**3. Nodos.** Conmutación **redundante**, preferiblemente **geográficamente distribuida**, de modo que la pérdida de un centro no deje sin servicio a la red.

**4. Radio.** **Solapamiento de cobertura** entre células, de forma que la caída de una estación base degrade el servicio en lugar de anularlo, y **redundancia de portadoras** en los emplazamientos críticos.

**5. Modos degradados.** Son la especialidad de TETRA y lo que la distingue de una red IP convencional:

- **Repliegue local** (*local site trunking*): la estación base aislada del núcleo **sigue troncalizando** dentro de su célula.
- **Modo directo (DMO)**: aunque caiga toda la red, los terminales **siguen hablando entre sí**.
- **Repliegue de clase de seguridad**: si se pierde el enlace con el centro de autenticación, la célula puede pasar de **SC3 a SC2** para seguir cifrando con clave estática `[TTR001-11]`.

**6. Procedimientos y personas.** Plan de continuidad probado, guardia 24×7, repuestos, y **ejercicios periódicos**. El ENS lo exige en **`op.cont.2`** (plan de continuidad), **`op.cont.3`** (**pruebas periódicas**) y **`op.cont.4`** (medios alternativos) `[ENS]`.

> **[DATO CLAVE EXAMEN]** Los **tres modos degradados** de TETRA, ordenados de menos a más severo: **repliegue local de la estación base** (pierde el núcleo, conserva la troncalización en su célula) → **modo directo** (pierde toda la red, conserva la comunicación terminal a terminal) → **repliegue de clase de seguridad SC3 → SC2** (pierde la autenticación, conserva el cifrado con clave estática). Que un sistema **degrade en escalones** en lugar de caer de golpe es el rasgo de diseño que define a las comunicaciones críticas.

**La calidad de servicio operativa.** Además de la disponibilidad, hay parámetros que se miden y se contratan:

| Parámetro | Objetivo típico |
|---|---|
| **Tiempo de establecimiento** de llamada de grupo | **< 300 ms** |
| **Probabilidad de bloqueo** en hora punta | Muy baja, con dimensionado para el escenario de gran emergencia |
| **Cobertura** | Porcentaje de la superficie y de la **población servida en interiores**, no solo en exteriores |
| **Inteligibilidad de la voz** | Medida en el borde de la célula, no en el centro |
| **Retardo de extremo a extremo** | Acotado, para que el diálogo sea natural |
| **Disponibilidad del servicio** | **≥ 99,99 %**, con penalizaciones contractuales |

> **[EJEMPLO AYTO MADRID]** El contrato municipal de 2026 refleja exactamente este lenguaje: **disponibilidad 24×7** de la infraestructura crítica y **tiempos de respuesta casi inmediatos ante incidencias técnicas** `[TELEFONICA-2026]`. Traducido a la práctica, eso significa guardia permanente, repuestos en almacén, procedimientos escritos y compromisos medibles. Y explica por qué el mantenimiento de una red de radio de emergencia se contrata como **servicio con niveles de servicio**, y no como una simple asistencia técnica.

> **[REFERENCIA CRUZADA]** Los conceptos de **plan de continuidad**, **análisis de impacto en el negocio**, **RTO y RPO** y **medios alternativos** se desarrollan en el **Tema 26**; su exigencia normativa, en el **Tema 39**. La **gestión de incidencias** y los acuerdos de nivel de servicio, en el **Tema 29**.

### 5.4. Evolución hacia TEDS y coexistencia con redes de banda ancha crítica

**El problema.** TETRA resuelve la **voz crítica** de forma insuperable, pero su techo de datos —**28,8 kbit/s** en el mejor de los casos— es incompatible con lo que hoy se pide a un servicio de emergencia: **vídeo del lugar del incidente**, **planos y cartografía**, **imagen médica**, **acceso a bases de datos con fotografía**, **cámaras corporales**. La evolución tiene dos caminos, y **no son alternativos sino sucesivos**.

**Camino 1: TEDS, dentro de TETRA.** El **TETRA Enhanced Data Service** es la aportación de datos de **TETRA Release 2**, descrita en el **TR 102 580** `[TR102580]`. Su idea es sencilla: **mantener todo lo que TETRA hace bien y ampliar el canal**. Para ello introduce:

- **Cuatro anchos de canal**: **25, 50, 100 y 150 kHz** (frente a los 25 kHz únicos de la Release 1).
- **Modulaciones de orden superior** además de la π/4-DQPSK: **π/8-D8PSK**, **4-QAM**, **16-QAM** y **64-QAM**.
- **Adaptación al enlace**: el sistema elige la modulación **según la calidad de la señal**, de modo que se usan modulaciones densas cerca de la estación base y robustas en el borde de la célula (el **4-QAM** está pensado precisamente para el borde de cobertura).
- **Negociación de calidad de servicio** para las aplicaciones, con atributos de caudal, retardo, prioridad y fiabilidad.

El resultado es un salto de **uno o dos órdenes de magnitud** en la capacidad de datos —del orden de decenas a **algunos centenares de kbit/s** de caudal útil, según ancho de canal, modulación y condiciones de propagación—, manteniendo la misma red, los mismos grupos y la misma voz crítica.

> **[DATO CLAVE EXAMEN]** **TEDS = TETRA Release 2**, con **cuatro anchos de canal (25, 50, 100 y 150 kHz)** y **modulaciones π/8-D8PSK, 4-QAM, 16-QAM y 64-QAM** con **adaptación al enlace**. Es una **mejora dentro de TETRA**, no una tecnología distinta: sigue siendo banda estrecha en el sentido regulatorio, y **no compite con LTE**. Su adopción real ha sido limitada, entre otras razones porque exige **más espectro por canal** —y el espectro de 380-400 MHz está saturado en entornos urbanos, como reconoce la propia nota UN-28 del CNAF— y porque, cuando TEDS llegó al mercado, la banda ancha comercial ya ofrecía mucho más.

**Camino 2: la banda ancha crítica, fuera de TETRA.** La solución de fondo es llevar las funciones de misión crítica a redes de **banda ancha** LTE y 5G. El **3GPP** las normalizó:

| Servicio | Qué es | Release |
|---|---|---|
| **MCPTT** | *Mission Critical Push To Talk*: la **voz de grupo con PTT, prioridad y desalojo** sobre LTE | **Release 13** (culminada en **2016**); etapa 1 en la **TS 22.179** |
| **MCVideo** | Vídeo de misión crítica | Release 14 |
| **MCData** | Datos de misión crítica | Release 14 |

Y se apoya en tres habilitadores previos del propio 3GPP: **GCSE** (comunicaciones de grupo), **eMBMS** (difusión eficiente a muchos receptores sobre la misma portadora, imprescindible para que una llamada de grupo no consuma un canal por usuario) y **ProSe** (comunicación de proximidad, el equivalente conceptual del **modo directo**).

> **[DATO CLAVE EXAMEN]** **MCPTT se normalizó en la Release 13 del 3GPP, culminada en 2016**, con la **TS 22.179** como especificación de requisitos. **MCVideo y MCData** llegaron en la **Release 14**. El habilitador que hace viable la llamada de grupo sobre LTE es **eMBMS**; el que aspira a replicar el modo directo es **ProSe**.

**Por qué la transición es lenta, y esto es lo que se pregunta en un caso práctico.** Las razones son cuatro y conviene saberlas defender:

1. **Cobertura y control.** Una red TETRA municipal está dimensionada por su titular para cubrir el 100 % del término municipal, incluidos interiores y subsuelo. Replicar esa cobertura con LTE **propio** es carísimo; usar LTE **comercial** significa renunciar al control de la disponibilidad y de la prioridad.
2. **El modo directo.** **ProSe no ha alcanzado en la práctica la madurez del DMO de TETRA**, y el modo directo es innegociable para bomberos y equipos de rescate.
3. **Consumo y autonomía.** Un terminal de banda ancha consume mucho más que uno de banda estrecha; la autonomía de jornada completa no es trivial.
4. **Amortización y parque instalado.** Hay miles de terminales en servicio, personal formado y procedimientos escritos alrededor de ellos.

**El modelo que se impone: la coexistencia.** La respuesta práctica del sector no es sustituir, sino **operar dos redes complementarias**: **TETRA para la voz crítica y los datos cortos garantizados**, y **banda ancha (LTE/5G, propia o comercial con prioridad contratada) para todo lo que necesita caudal**, con **terminales híbridos** que integran ambas y con **interconexión entre el mundo MCPTT y el mundo TETRA** en los centros de mando. La migración se plantea **por fases y por servicios**, no de golpe.

> **[EJEMPLO AYTO MADRID]** El caso español ilustra bien este modelo. El **SIRDEE**, en servicio desde el año 2000 sobre TETRAPOL, inició en **julio de 2024** un proyecto piloto de **migración a banda ancha LTE** de la mano de Telefónica, **manteniendo la red de banda estrecha durante la transición** y usando la red pública como cobertura de respaldo donde no llega la red dedicada `[SIRDEE]`. En paralelo, el CNAF ya tiene **reservado el espectro** para ese futuro: **452-457,5 / 462-467,5 MHz** para PPDR de banda ancha y, en la banda de 700 MHz, **733-736 / 788-791 MHz** para el sistema de **ámbito nacional** y **698-703 / 753-758 MHz** para las redes de **ámbito autonómico y local** `[CNAF]`. Ese último bloque es, literalmente, **el espectro que la norma española reserva para una eventual red de banda ancha crítica de la Comunidad de Madrid o del Ayuntamiento**. Que exista la reserva no significa que exista la red: significa que **la decisión está pendiente y el recurso, apartado**.

> **[DATO CLAVE EXAMEN]** El reparto de espectro PPDR de banda ancha del CNAF: **733-736 / 788-791 MHz → ámbito NACIONAL**; **698-703 / 753-758 MHz → ámbito AUTONÓMICO y LOCAL**; y **452-457,5 / 462-467,5 MHz**, «preferentemente para el sistema de ámbito nacional» `[CNAF]`. Una pregunta que cruce «banda ancha PPDR» con «ámbito local» se responde con el segundo par.

> **[REFERENCIA CRUZADA]** La arquitectura de las redes móviles de banda ancha (LTE, 5G) es materia del **Tema 33**; el transporte IP sobre ellas, del **Tema 34**; los servicios de vídeo y colaboración que justifican el salto de capacidad, del **Tema 40**; y la seguridad del acceso remoto que exigirán las aplicaciones móviles de misión crítica, del **Tema 36**.

---

## Los ocho datos que no se pueden fallar

Si de todo el tema hubiera que retener solo ocho cosas, serían éstas:

1. **TETRA es un estándar abierto del ETSI**, serie **EN 300 392** (modo troncalizado, V+D) y **EN 300 396** (modo directo, DMO). La expansión vigente de las siglas es **TErrestrial TRunked RAdio**; *Trans European Trunked Radio* es la histórica.
2. **Capa física**: portadora de **25 kHz**, **FDMA + TDMA con 4 intervalos**, modulación **π/4-DQPSK** a **18 kbaudios** → **36 kbit/s brutos** por portadora y **7,2 kbit/s netos** por intervalo. Códec **ACELP**, **4,567 kbit/s**.
3. **Jerarquía temporal**: intervalo **14,167 ms** → trama **56,67 ms** (4 intervalos) → multitrama **1,02 s** (18 tramas, la **18.ª es la de control**) → hipertrama **61,2 s** (60 multitramas).
4. **TMO frente a DMO**: el modo troncalizado va por la infraestructura; el **modo directo funciona sin ella**, y es lo que un teléfono móvil no puede hacer. El **DM-REP** amplía el alcance del modo directo; el **DM-GATE** lo conecta con la red. **No son lo mismo.**
5. **Bandas en España**: **380-385 / 390-395 MHz** para redes de seguridad del Estado y emergencias (nota **UN-28**); **410-415,3 / 420-425,3 MHz** para **TETRA civil** (nota **UN-31**, que **cita TETRA por su nombre**), con **25 kHz** de canalización y **10 MHz** de separación dúplex. El CNAF vigente es la **Orden TDF/732/2026, de 10 de julio**.
6. **Régimen jurídico**: el espectro es **dominio público estatal** (art. 85). Una red municipal es **uso privativo en autoprestación** y su título es una **afectación demanial** (art. **88.5.b**), por **cinco años renovables** (art. 94.1). Y las comunicaciones para **seguridad pública y protección civil** son **los únicos servicios de telecomunicación calificados como servicio público** (art. **4.1**).
7. **Seguridad**: clases **SC1** (sin cifrar), **SC2** (clave estática **SCK**) y **SC3** (clave derivada **DCK** + **CCK**, con autenticación). **TEA set A = TEA1-TEA4**; **TEA set B = TEA5, TEA6 y TEA7** (octubre de 2022). **TEA1 tiene la clave reducida a ~32 bits efectivos** (**CVE-2022-24402**), y **soportarlo en la red compromete también a los demás algoritmos** (**CVE-2025-52943**). El **cifrado de interfaz aire se descifra en la estación base**; el **extremo a extremo, no**.
8. **Y la trampa del tema**: **el SIRDEE, la red de emergencia del Estado, es TETRAPOL —FDMA, 12,5 kHz, GMSK— y no TETRA**. Las redes **autonómicas y municipales** españolas, incluidas la de la Comunidad de Madrid y la del Ayuntamiento, sí son **TETRA**.
