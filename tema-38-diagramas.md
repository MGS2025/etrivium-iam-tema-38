# Tema 38 — Catálogo de Diagramas

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
>
> **Versión**: v1.0
> **Fecha**: 2026-08-27
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (cero dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)
> **Nota técnica**: las clases CSS de cada SVG llevan sufijo numérico único (`.t1`, `.h1`…) para evitar colisiones de estilos entre los 18 diagramas embebidos en la misma página. Ningún elemento mezcla `class` con el atributo `fill`: cuando hace falta un color distinto se declara una clase nueva.

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | Cuatro generaciones de radio profesional | §1.1 | Línea temporal | 680×292 |
| D2 | Radio convencional frente a sistema troncalizado | §1.2 | Comparativa de reparto | 680×340 |
| D3 | La familia de normas TETRA del ETSI | §1.3 | Mapa de normas | 680×324 |
| D4 | Arquitectura de una red TETRA | §2.1 | Topología | 680×340 |
| D5 | La SwMI por dentro: qué hace cada bloque | §2.1.2 · §2.1.3 | Bloques funcionales | 680×340 |
| D6 | Terminales: factores de forma y clases de potencia | §2.2.1 | Comparativa | 680×308 |
| D7 | TMO, DMO y las dos figuras que los unen | §2.2.2 · §2.2.3 | Escenario operativo | 680×356 |
| D8 | Las seis interfaces normalizadas (I1 a I6) | §2.3 | Modelo de referencia | 680×340 |
| D9 | El espectro de TETRA en España según el CNAF | §3.1 | Mapa de bandas | 680×350 |
| D10 | FDMA + TDMA: cuatro conversaciones en 25 kHz | §3.2 | Estructura | 680×308 |
| D11 | Modulación π/4-DQPSK | §3.3 | Constelación + cifras | 680×324 |
| D12 | Jerarquía temporal: intervalo, trama, multitrama e hipertrama | §3.4 | Estructura anidada | 680×334 |
| D13 | Canales lógicos: control y tráfico | §3.4 | Clasificación | 680×328 |
| D14 | Tipos de llamada y escalones de prioridad | §4.1 | Comparativa + escalera | 680×358 |
| D15 | Servicios de datos: estados, SDS, circuito y paquetes | §4.2 | Tabla comparada | 680×348 |
| D16 | Cadena de seguridad: autenticación, claves y clases | §4.3.1 · §4.3.2 | Flujo + jerarquía | 680×356 |
| D17 | Interfaz aire frente a extremo a extremo, y qué rompió cada divulgación | §4.3.2 · §4.3.3 | Capas + cronología | 680×390 |
| D18 | De TETRA a la banda ancha crítica | §5.4 | Evolución + espectro | 680×360 |

---
## D1 · Cuatro generaciones de radio profesional

**Sección**: §1.1 — Concepto y evolución de la radiocomunicación móvil privada (PMR)
**Propósito**: Situar TETRA en la **tercera** generación y fijar qué problema resuelve cada etapa, que es la forma en que se pregunta esta materia.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 292" role="img" aria-label="Línea del tiempo con las cuatro generaciones de la radio móvil privada: la analógica convencional con un canal fijo por colectivo, el trunking analógico con MPT mil trescientos veintisiete, el trunking digital al que pertenecen TETRA, TETRAPOL, P25 y DMR, y la banda ancha crítica con MCPTT del 3GPP. Debajo se indica qué deja sin resolver cada etapa y se concluye que TETRA pertenece a la tercera generación">
  <style>.t1{font:700 10px system-ui,sans-serif;fill:#fff}.s1{font:8.5px system-ui,sans-serif;fill:#fff}.d1{font:8.5px system-ui,sans-serif;fill:#333}.h1{font:700 13px system-ui,sans-serif;fill:#0055a0}.k1{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n1{font:8.5px system-ui,sans-serif;fill:#666}</style>
  <text x="340" y="22" text-anchor="middle" class="h1">TETRA es la TERCERA generación: trunking digital</text>
  <rect x="20" y="40" width="154" height="76" rx="5" fill="#6b7c8c"/>
  <text x="97" y="58" text-anchor="middle" class="t1">1.ª · ANALÓGICA</text>
  <text x="97" y="72" text-anchor="middle" class="s1">Desde los años treinta</text>
  <text x="97" y="86" text-anchor="middle" class="s1">Un canal FIJO por cada</text>
  <text x="97" y="100" text-anchor="middle" class="s1">colectivo. Modulación FM</text>
  <path d="M175,71 L181,78 L175,85 Z" fill="#0055a0"/>
  <rect x="182" y="40" width="154" height="76" rx="5" fill="#0055a0"/>
  <text x="259" y="58" text-anchor="middle" class="t1">2.ª · TRUNKING ANALÓGICO</text>
  <text x="259" y="72" text-anchor="middle" class="s1">Años setenta y ochenta</text>
  <text x="259" y="86" text-anchor="middle" class="s1">Bolsa común de canales.</text>
  <text x="259" y="100" text-anchor="middle" class="s1">Norma típica: MPT-1327</text>
  <path d="M337,71 L343,78 L337,85 Z" fill="#0055a0"/>
  <rect x="344" y="40" width="154" height="76" rx="5" fill="#2d8659"/>
  <text x="421" y="58" text-anchor="middle" class="t1">3.ª · TRUNKING DIGITAL</text>
  <text x="421" y="72" text-anchor="middle" class="s1">Años noventa</text>
  <text x="421" y="86" text-anchor="middle" class="s1">TETRA · TETRAPOL</text>
  <text x="421" y="100" text-anchor="middle" class="s1">P25 · DMR</text>
  <path d="M499,71 L505,78 L499,85 Z" fill="#0055a0"/>
  <rect x="506" y="40" width="154" height="76" rx="5" fill="#e89822"/>
  <text x="583" y="58" text-anchor="middle" class="t1">4.ª · BANDA ANCHA</text>
  <text x="583" y="72" text-anchor="middle" class="s1">Desde 2016</text>
  <text x="583" y="86" text-anchor="middle" class="s1">MCPTT, MCVideo y MCData</text>
  <text x="583" y="100" text-anchor="middle" class="s1">del 3GPP, sobre LTE y 5G</text>
  <text x="20" y="138" class="k1">LO QUE CADA ETAPA DEJA SIN RESOLVER</text>
  <rect x="20" y="146" width="154" height="60" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="97" y="164" text-anchor="middle" class="d1">Desperdicia espectro,</text>
  <text x="97" y="177" text-anchor="middle" class="d1">no hay privacidad</text>
  <text x="97" y="190" text-anchor="middle" class="d1">ni identificación</text>
  <rect x="182" y="146" width="154" height="60" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="259" y="164" text-anchor="middle" class="d1">Gana eficiencia, pero</text>
  <text x="259" y="177" text-anchor="middle" class="d1">la voz sigue siendo</text>
  <text x="259" y="190" text-anchor="middle" class="d1">analógica: sin cifrado</text>
  <rect x="344" y="146" width="154" height="60" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="421" y="164" text-anchor="middle" class="d1">Resuelve cifrado, voz</text>
  <text x="421" y="177" text-anchor="middle" class="d1">y datos juntos. Techo</text>
  <text x="421" y="190" text-anchor="middle" class="d1">de datos: 28,8 kbit/s</text>
  <rect x="506" y="146" width="154" height="60" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="583" y="164" text-anchor="middle" class="d1">Da caudal, pero aún no</text>
  <text x="583" y="177" text-anchor="middle" class="d1">iguala el modo directo</text>
  <text x="583" y="190" text-anchor="middle" class="d1">ni la autonomía</text>
  <rect x="20" y="222" width="640" height="42" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="340" y="240" text-anchor="middle" class="k1">Las cuatro NO se sustituyen limpiamente: la tercera y la cuarta CONVIVEN</text>
  <text x="340" y="255" text-anchor="middle" class="n1">TETRA aporta voz crítica, prioridad y modo directo; la banda ancha aporta caudal. Hoy se despliegan juntas</text>
  <text x="670" y="284" text-anchor="end" class="n1">[Fuente: elaboración propia sobre ETSI EN 300 392, ETSI EN 300 396 y 3GPP Release 13]</text>
</svg>
```

---

## D2 · Radio convencional frente a sistema troncalizado

**Sección**: §1.2 — Sistemas *trunked* o troncalizados: concepto y ventajas
**Propósito**: Mostrar con números por qué el mismo espectro rinde varias veces más cuando se troncaliza, y fijar la idea de que **un grupo solo consume canal mientras alguien habla**.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Comparación entre radio convencional y sistema troncalizado. En la convencional cada colectivo tiene un canal fijo asignado, de modo que cuatro portadoras dan cuatro canales rígidos. En el sistema troncalizado TETRA las cuatro portadoras se dividen en cuatro intervalos cada una, dan dieciséis canales físicos, uno se dedica al canal de control y quedan quince canales de tráfico repartidos dinámicamente entre todos los grupos">
  <style>.t2{font:700 10px system-ui,sans-serif;fill:#fff}.s2{font:8.5px system-ui,sans-serif;fill:#fff}.d2{font:8.5px system-ui,sans-serif;fill:#333}.h2{font:700 13px system-ui,sans-serif;fill:#0055a0}.k2{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n2{font:8.5px system-ui,sans-serif;fill:#666}.b2{font:700 9px system-ui,sans-serif;fill:#0055a0}.r2{font:700 9.5px system-ui,sans-serif;fill:#d13c3c}.g2{font:700 9.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="22" text-anchor="middle" class="h2">Mismo espectro, casi cuatro veces más conversaciones</text>
  <text x="20" y="46" class="r2">CONVENCIONAL · 4 portadoras de 25 kHz</text>
  <rect x="20" y="54" width="314" height="120" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <rect x="32" y="66" width="140" height="22" rx="3" fill="#d13c3c"/>
  <text x="102" y="81" text-anchor="middle" class="s2">Canal 1 · POLICÍA</text>
  <rect x="182" y="66" width="140" height="22" rx="3" fill="#d13c3c"/>
  <text x="252" y="81" text-anchor="middle" class="s2">Canal 2 · BOMBEROS</text>
  <rect x="32" y="94" width="140" height="22" rx="3" fill="#d13c3c"/>
  <text x="102" y="109" text-anchor="middle" class="s2">Canal 3 · SANITARIOS</text>
  <rect x="182" y="94" width="140" height="22" rx="3" fill="#d13c3c"/>
  <text x="252" y="109" text-anchor="middle" class="s2">Canal 4 · MOVILIDAD</text>
  <text x="177" y="136" text-anchor="middle" class="d2">Cada canal pertenece a UN colectivo, hable o no.</text>
  <text x="177" y="149" text-anchor="middle" class="d2">Si el de policía se satura, el agente espera</text>
  <text x="177" y="162" text-anchor="middle" class="d2">aunque los otros tres estén vacíos.</text>
  <text x="346" y="46" class="g2">TRONCALIZADO TETRA · las mismas 4 portadoras</text>
  <rect x="346" y="54" width="314" height="120" rx="5" fill="none" stroke="#2d8659" stroke-width="1.5"/>
  <rect x="358" y="66" width="68" height="22" rx="3" fill="#0055a0"/>
  <text x="392" y="81" text-anchor="middle" class="s2">CONTROL</text>
  <rect x="430" y="66" width="68" height="22" rx="3" fill="#2d8659"/>
  <text x="464" y="81" text-anchor="middle" class="s2">Tráfico</text>
  <rect x="502" y="66" width="68" height="22" rx="3" fill="#2d8659"/>
  <text x="536" y="81" text-anchor="middle" class="s2">Tráfico</text>
  <rect x="574" y="66" width="68" height="22" rx="3" fill="#2d8659"/>
  <text x="608" y="81" text-anchor="middle" class="s2">Tráfico</text>
  <rect x="358" y="94" width="284" height="22" rx="3" fill="#2d8659"/>
  <text x="500" y="109" text-anchor="middle" class="s2">12 canales de tráfico más, en las otras 3 portadoras</text>
  <text x="503" y="136" text-anchor="middle" class="d2">4 portadoras × 4 intervalos = 16 canales físicos.</text>
  <text x="503" y="149" text-anchor="middle" class="d2">Menos 1 de control = 15 canales de tráfico,</text>
  <text x="503" y="162" text-anchor="middle" class="d2">repartidos entre TODOS los grupos.</text>
  <text x="20" y="198" class="k2">Y LA CONSECUENCIA QUE MÁS SE PREGUNTA</text>
  <rect x="20" y="206" width="200" height="66" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="120" y="224" text-anchor="middle" class="b2">El grupo es LÓGICO</text>
  <text x="120" y="240" text-anchor="middle" class="d2">No es una frecuencia: es una</text>
  <text x="120" y="253" text-anchor="middle" class="d2">identidad (GSSI) en la base</text>
  <text x="120" y="266" text-anchor="middle" class="d2">de datos del sistema</text>
  <rect x="244" y="206" width="200" height="66" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="344" y="224" text-anchor="middle" class="b2">Solo consume al hablar</text>
  <text x="344" y="240" text-anchor="middle" class="d2">Un grupo ocupa canal SOLO</text>
  <text x="344" y="253" text-anchor="middle" class="d2">mientras alguien transmite,</text>
  <text x="344" y="266" text-anchor="middle" class="d2">y solo en las células con afiliados</text>
  <rect x="468" y="206" width="200" height="66" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="568" y="224" text-anchor="middle" class="b2">Grupos casi ilimitados</text>
  <text x="568" y="240" text-anchor="middle" class="d2">Pueden existir decenas o</text>
  <text x="568" y="253" text-anchor="middle" class="d2">centenares de grupos con</text>
  <text x="568" y="266" text-anchor="middle" class="d2">muy pocas portadoras</text>
  <rect x="20" y="286" width="648" height="26" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="344" y="303" text-anchor="middle" class="k2">Trunking = asignación DINÁMICA de canales bajo demanda desde una bolsa común, dirigida por el canal de control</text>
  <text x="670" y="332" text-anchor="end" class="n2">[Fuente: elaboración propia sobre ETSI EN 300 392-2 y la nota UN-27 del CNAF]</text>
</svg>
```

---

## D3 · La familia de normas TETRA del ETSI

**Sección**: §1.3 — Estandarización de TETRA por el ETSI
**Propósito**: Ordenar las series de normas para poder responder «qué norma regula qué», que es la forma habitual de la pregunta.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 324" role="img" aria-label="Mapa de la familia de normas TETRA del ETSI. La serie EN 300 392 regula el modo troncalizado voz más datos, con la parte 1 de diseño general, la parte 2 del interfaz aire, la parte 3 de la interfaz entre sistemas, la parte 4 de pasarelas, la parte 5 del interfaz de equipo periférico, la parte 7 de seguridad y las partes 9 a 12 de servicios suplementarios. La serie EN 300 396 regula el modo directo. Además, EN 300 394 de pruebas de conformidad, EN 300 395 del códec de voz, EN 300 812 del módulo de identidad, TR 102 580 de TEDS y TS 104 053 de los algoritmos de cifrado">
  <style>.t3{font:700 10px system-ui,sans-serif;fill:#fff}.s3{font:8.5px system-ui,sans-serif;fill:#fff}.d3{font:8.5px system-ui,sans-serif;fill:#333}.h3{font:700 13px system-ui,sans-serif;fill:#0055a0}.k3{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n3{font:8.5px system-ui,sans-serif;fill:#666}.b3{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="22" text-anchor="middle" class="h3">Las dos series que no se pueden confundir: 392 y 396</text>
  <rect x="20" y="36" width="420" height="150" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <rect x="32" y="46" width="396" height="24" rx="3" fill="#0055a0"/>
  <text x="230" y="62" text-anchor="middle" class="t3">EN 300 392 · TETRA V+D — MODO TRONCALIZADO (TMO)</text>
  <rect x="32" y="78" width="126" height="46" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="95" y="94" text-anchor="middle" class="b3">Parte 1</text>
  <text x="95" y="108" text-anchor="middle" class="d3">Diseño general de red</text>
  <text x="95" y="120" text-anchor="middle" class="d3">Interfaces I1 a I6</text>
  <rect x="167" y="78" width="126" height="46" rx="3" fill="#d13c3c"/>
  <text x="230" y="94" text-anchor="middle" class="t3">Parte 2</text>
  <text x="230" y="108" text-anchor="middle" class="s3">INTERFAZ AIRE</text>
  <text x="230" y="120" text-anchor="middle" class="s3">Capas 1, 2 y 3</text>
  <rect x="302" y="78" width="126" height="46" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="365" y="94" text-anchor="middle" class="b3">Parte 3</text>
  <text x="365" y="108" text-anchor="middle" class="d3">ISI: interconexión</text>
  <text x="365" y="120" text-anchor="middle" class="d3">entre redes TETRA</text>
  <rect x="32" y="132" width="126" height="46" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="95" y="148" text-anchor="middle" class="b3">Partes 4 y 5</text>
  <text x="95" y="162" text-anchor="middle" class="d3">Pasarelas PSTN/RDSI</text>
  <text x="95" y="174" text-anchor="middle" class="d3">y PEI (datos)</text>
  <rect x="167" y="132" width="126" height="46" rx="3" fill="#d13c3c"/>
  <text x="230" y="148" text-anchor="middle" class="t3">Parte 7</text>
  <text x="230" y="162" text-anchor="middle" class="s3">SEGURIDAD</text>
  <text x="230" y="174" text-anchor="middle" class="s3">Claves y clases</text>
  <rect x="302" y="132" width="126" height="46" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="365" y="148" text-anchor="middle" class="b3">Partes 9 a 12</text>
  <text x="365" y="162" text-anchor="middle" class="d3">Servicios</text>
  <text x="365" y="174" text-anchor="middle" class="d3">suplementarios</text>
  <rect x="452" y="36" width="216" height="150" rx="5" fill="none" stroke="#2d8659" stroke-width="2"/>
  <rect x="464" y="46" width="192" height="24" rx="3" fill="#2d8659"/>
  <text x="560" y="62" text-anchor="middle" class="t3">EN 300 396 · DMO</text>
  <text x="560" y="86" text-anchor="middle" class="d3">MODO DIRECTO: terminal a</text>
  <text x="560" y="99" text-anchor="middle" class="d3">terminal, SIN infraestructura</text>
  <rect x="464" y="110" width="192" height="30" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="560" y="123" text-anchor="middle" class="d3">DM-REP · repetidor</text>
  <text x="560" y="135" text-anchor="middle" class="d3">tipos 1A, 1B y 2</text>
  <rect x="464" y="146" width="192" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="560" y="159" text-anchor="middle" class="d3">DM-GATE · pasarela hacia</text>
  <text x="560" y="171" text-anchor="middle" class="d3">la red troncalizada</text>
  <text x="20" y="208" class="k3">Y EL RESTO DE LA FAMILIA</text>
  <rect x="20" y="216" width="120" height="58" rx="4" fill="#e89822"/>
  <text x="80" y="234" text-anchor="middle" class="t3">EN 300 394</text>
  <text x="80" y="249" text-anchor="middle" class="s3">Pruebas de</text>
  <text x="80" y="262" text-anchor="middle" class="s3">conformidad</text>
  <rect x="152" y="216" width="120" height="58" rx="4" fill="#e89822"/>
  <text x="212" y="234" text-anchor="middle" class="t3">EN 300 395</text>
  <text x="212" y="249" text-anchor="middle" class="s3">Códec de voz</text>
  <text x="212" y="262" text-anchor="middle" class="s3">ACELP</text>
  <rect x="284" y="216" width="120" height="58" rx="4" fill="#e89822"/>
  <text x="344" y="234" text-anchor="middle" class="t3">EN 300 812</text>
  <text x="344" y="249" text-anchor="middle" class="s3">Módulo de</text>
  <text x="344" y="262" text-anchor="middle" class="s3">identidad (SIM)</text>
  <rect x="416" y="216" width="120" height="58" rx="4" fill="#e89822"/>
  <text x="476" y="234" text-anchor="middle" class="t3">TR 102 580</text>
  <text x="476" y="249" text-anchor="middle" class="s3">TEDS · datos de</text>
  <text x="476" y="262" text-anchor="middle" class="s3">la Release 2</text>
  <rect x="548" y="216" width="120" height="58" rx="4" fill="#e89822"/>
  <text x="608" y="234" text-anchor="middle" class="t3">TS 104 053</text>
  <text x="608" y="249" text-anchor="middle" class="s3">Algoritmos TEA</text>
  <text x="608" y="262" text-anchor="middle" class="s3">(parte 1, 2025)</text>
  <text x="340" y="296" text-anchor="middle" class="k3">La EN 300 394 es la pieza que hace VERIFICABLE la interoperabilidad entre fabricantes</text>
  <text x="670" y="316" text-anchor="end" class="n3">[Fuente: elaboración propia sobre el catálogo de normas TETRA del ETSI]</text>
</svg>
```

---

## D4 · Arquitectura de una red TETRA

**Sección**: §2.1 — Infraestructura de conmutación y gestión (SwMI)
**Propósito**: Fijar de un vistazo qué es la SwMI, qué queda fuera de ella y por dónde entra cada elemento.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Topología de una red TETRA. En el centro, la infraestructura de conmutación y gestión o SwMI, que contiene el nodo de conmutación, las bases de datos de abonados y grupos, el centro de autenticación y las estaciones base. A la izquierda, los terminales portátiles, móviles y fijos, que se conectan por el interfaz aire I1. A la derecha, las consolas de despacho, el grabador y el sistema de gestión de red, conectados por las interfaces de línea I2 y de gestión I5. Abajo, la pasarela hacia la red telefónica y la interfaz entre sistemas I3 hacia otra red TETRA">
  <style>.t4{font:700 10px system-ui,sans-serif;fill:#fff}.s4{font:8.5px system-ui,sans-serif;fill:#fff}.d4{font:8.5px system-ui,sans-serif;fill:#333}.h4{font:700 13px system-ui,sans-serif;fill:#0055a0}.k4{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n4{font:8.5px system-ui,sans-serif;fill:#666}.b4{font:700 9px system-ui,sans-serif;fill:#0055a0}.i4{font:700 8.5px system-ui,sans-serif;fill:#d13c3c}</style>
  <text x="340" y="22" text-anchor="middle" class="h4">Todo lo que no es terminal, se llama SwMI</text>
  <rect x="196" y="38" width="288" height="180" rx="6" fill="#eaf1f8" stroke="#0055a0" stroke-width="2"/>
  <text x="340" y="56" text-anchor="middle" class="b4">SwMI · Switching and Management Infrastructure</text>
  <rect x="210" y="66" width="126" height="42" rx="4" fill="#0055a0"/>
  <text x="273" y="82" text-anchor="middle" class="t4">Conmutación</text>
  <text x="273" y="97" text-anchor="middle" class="s4">Encamina cada llamada</text>
  <rect x="344" y="66" width="126" height="42" rx="4" fill="#0055a0"/>
  <text x="407" y="82" text-anchor="middle" class="t4">Abonados y grupos</text>
  <text x="407" y="97" text-anchor="middle" class="s4">Identidades y permisos</text>
  <rect x="210" y="116" width="126" height="42" rx="4" fill="#0055a0"/>
  <text x="273" y="132" text-anchor="middle" class="t4">Autenticación</text>
  <text x="273" y="147" text-anchor="middle" class="s4">Claves y OTAR</text>
  <rect x="344" y="116" width="126" height="42" rx="4" fill="#0055a0"/>
  <text x="407" y="132" text-anchor="middle" class="t4">Movilidad</text>
  <text x="407" y="147" text-anchor="middle" class="s4">Registro y traspaso</text>
  <rect x="210" y="166" width="260" height="42" rx="4" fill="#2d8659"/>
  <text x="340" y="182" text-anchor="middle" class="t4">ESTACIONES BASE (BS)</text>
  <text x="340" y="197" text-anchor="middle" class="s4">Canal de control (MCCH) y cifrado del interfaz aire</text>
  <rect x="20" y="70" width="156" height="120" rx="5" fill="none" stroke="#666" stroke-width="1.5"/>
  <text x="98" y="88" text-anchor="middle" class="b4">TERMINALES (MS)</text>
  <rect x="32" y="98" width="132" height="24" rx="3" fill="#e89822"/>
  <text x="98" y="114" text-anchor="middle" class="s4">Portátil · 1 W o 3 W</text>
  <rect x="32" y="128" width="132" height="24" rx="3" fill="#e89822"/>
  <text x="98" y="144" text-anchor="middle" class="s4">Móvil · 3 W o 10 W</text>
  <rect x="32" y="158" width="132" height="24" rx="3" fill="#e89822"/>
  <text x="98" y="174" text-anchor="middle" class="s4">Fijo · 10 W o más</text>
  <path d="M176,130 L194,130" stroke="#d13c3c" stroke-width="2"/>
  <path d="M188,126 L196,130 L188,134 Z" fill="#d13c3c"/>
  <text x="185" y="122" text-anchor="middle" class="i4">I1</text>
  <rect x="504" y="70" width="156" height="120" rx="5" fill="none" stroke="#666" stroke-width="1.5"/>
  <text x="582" y="88" text-anchor="middle" class="b4">EQUIPOS POR LÍNEA</text>
  <rect x="516" y="98" width="132" height="24" rx="3" fill="#6b7c8c"/>
  <text x="582" y="114" text-anchor="middle" class="s4">Consolas de despacho</text>
  <rect x="516" y="128" width="132" height="24" rx="3" fill="#6b7c8c"/>
  <text x="582" y="144" text-anchor="middle" class="s4">Grabador</text>
  <rect x="516" y="158" width="132" height="24" rx="3" fill="#6b7c8c"/>
  <text x="582" y="174" text-anchor="middle" class="s4">Gestión de red (NMS)</text>
  <path d="M486,130 L502,130" stroke="#d13c3c" stroke-width="2"/>
  <path d="M494,126 L502,130 L494,134 Z" fill="#d13c3c"/>
  <text x="494" y="118" text-anchor="middle" class="i4">I2</text>
  <text x="494" y="148" text-anchor="middle" class="i4">I5</text>
  <path d="M300,218 L300,238" stroke="#d13c3c" stroke-width="2"/>
  <path d="M296,230 L300,238 L304,230 Z" fill="#d13c3c"/>
  <path d="M440,218 L440,228 L556,228 L556,238" stroke="#d13c3c" stroke-width="2" fill="none"/>
  <path d="M552,230 L556,238 L560,230 Z" fill="#d13c3c"/>
  <path d="M92,192 L92,238" stroke="#666" stroke-width="2"/>
  <path d="M88,230 L92,238 L96,230 Z" fill="#666"/>
  <rect x="180" y="242" width="240" height="40" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="300" y="258" text-anchor="middle" class="b4">Pasarelas PSTN / RDSI</text>
  <text x="300" y="272" text-anchor="middle" class="d4">EN 300 392-4 · llamadas al teléfono</text>
  <rect x="436" y="242" width="240" height="40" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="556" y="258" text-anchor="middle" class="b4">I3 · ISI hacia otra red TETRA</text>
  <text x="556" y="272" text-anchor="middle" class="d4">EN 300 392-3 · itinerancia y grupos</text>
  <rect x="20" y="242" width="144" height="40" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="92" y="258" text-anchor="middle" class="b4">I6 · modo directo</text>
  <text x="92" y="272" text-anchor="middle" class="d4">terminal a terminal</text>
  <text x="340" y="302" text-anchor="middle" class="k4">Regla de lectura: el terminal solo ve el interfaz aire; TODO lo demás es SwMI</text>
  <text x="670" y="332" text-anchor="end" class="n4">[Fuente: elaboración propia sobre ETSI EN 300 392-1 y ETSI ETR 300-1]</text>
</svg>
```

---

## D5 · La SwMI por dentro: qué hace cada bloque

**Sección**: §2.1.2 — Nodos de conmutación y control de red · §2.1.3 — Centros de gestión
**Propósito**: Separar las tres capas de la infraestructura fija —radio, conmutación y gestión— porque los casos prácticos suelen preguntar por la tercera, que es la que se olvida.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Las tres capas de la infraestructura fija de una red TETRA. La capa de radio, con las estaciones base, el canal de control principal, el traspaso entre células y el repliegue local. La capa de conmutación y control, con el encaminamiento de llamadas de grupo, la gestión de movilidad, las bases de datos de abonados, el centro de autenticación y la gestión de prioridades. Y la capa de gestión y despacho, con el sistema de gestión de red, la gestión de abonados y grupos, las consolas de despacho, la grabación y la gestión de claves criptográficas">
  <style>.t5{font:700 10px system-ui,sans-serif;fill:#fff}.s5{font:8.5px system-ui,sans-serif;fill:#fff}.d5{font:8.5px system-ui,sans-serif;fill:#333}.h5{font:700 13px system-ui,sans-serif;fill:#0055a0}.k5{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n5{font:8.5px system-ui,sans-serif;fill:#666}.b5{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="22" text-anchor="middle" class="h5">La capa que se olvida al estudiar es la tercera: la de gestión</text>
  <rect x="20" y="36" width="648" height="76" rx="5" fill="#2d8659"/>
  <text x="36" y="56" class="t5">CAPA 1 · RADIO — las estaciones base</text>
  <text x="36" y="74" class="s5">Radiar y recibir en las portadoras asignadas · mantener el canal de control principal (MCCH) · difundir la información</text>
  <text x="36" y="88" class="s5">de sistema · asignar canales de tráfico · cifrar y descifrar el interfaz aire · gestionar el traspaso entre células</text>
  <text x="36" y="104" class="s5">Modo degradado propio: REPLIEGUE LOCAL — sigue troncalizando en su célula aunque pierda el núcleo</text>
  <rect x="20" y="122" width="648" height="76" rx="5" fill="#0055a0"/>
  <text x="36" y="142" class="t5">CAPA 2 · CONMUTACIÓN Y CONTROL — el núcleo</text>
  <text x="36" y="160" class="s5">Encaminar cada llamada de grupo SOLO a las células con afiliados · gestión de movilidad y traspaso entre nodos</text>
  <text x="36" y="174" class="s5">Bases de datos de abonados y grupos · centro de autenticación y distribución de claves (OTAR)</text>
  <text x="36" y="190" class="s5">Gestión de prioridades y desalojo · pasarelas hacia la red telefónica · interconexión ISI con otras redes TETRA</text>
  <rect x="20" y="208" width="648" height="76" rx="5" fill="#e89822"/>
  <text x="36" y="228" class="t5">CAPA 3 · GESTIÓN Y DESPACHO — donde trabajan las personas</text>
  <text x="36" y="246" class="s5">Sistema de gestión de red (NMS): alarmas, ocupación, estado de baterías y grupos electrógenos de cada emplazamiento</text>
  <text x="36" y="260" class="s5">Gestión de abonados y grupos, incluida la DGNA y la inhabilitación remota · consolas de despacho · grabación</text>
  <text x="36" y="276" class="s5">Gestión de claves criptográficas — respaldo normativo: medida op.exp.10 del ENS</text>
  <rect x="20" y="292" width="648" height="22" rx="4" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="344" y="307" text-anchor="middle" class="k5">Cuando se moderniza una red madura, lo que se moderniza casi siempre es la CAPA 3</text>
  <text x="670" y="332" text-anchor="end" class="n5">[Fuente: elaboración propia sobre ETSI EN 300 392-1 y RD 311/2022 (ENS)]</text>
</svg>
```

---

## D6 · Terminales: factores de forma y clases de potencia

**Sección**: §2.2.1 — Equipos portátiles, móviles y fijos
**Propósito**: Fijar las clases de potencia normalizadas y las identidades del terminal, que son dos bloques de datos memorizables.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 308" role="img" aria-label="Los tres factores de forma del terminal TETRA con sus potencias típicas: portátil de uno o tres vatios para el agente a pie, móvil embarcado de tres o diez vatios para patrullas y ambulancias, y fijo de diez vatios o más para dependencias. Debajo, las clases de potencia normalizadas: clase uno treinta vatios, clase dos diez vatios, clase tres tres vatios y clase cuatro un vatio. Y a la derecha, el esquema de identidades: ITSI igual a MNI más ISSI, donde MNI es MCC más MNC, la identidad de grupo GSSI y la identidad corta cifrada ESI">
  <style>.t6{font:700 10px system-ui,sans-serif;fill:#fff}.s6{font:8.5px system-ui,sans-serif;fill:#fff}.d6{font:8.5px system-ui,sans-serif;fill:#333}.h6{font:700 13px system-ui,sans-serif;fill:#0055a0}.k6{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n6{font:8.5px system-ui,sans-serif;fill:#666}.b6{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="22" text-anchor="middle" class="h6">El portátil llega menos lejos que el vehículo: de ahí las pasarelas</text>
  <text x="20" y="46" class="k6">FACTORES DE FORMA</text>
  <rect x="20" y="54" width="200" height="62" rx="5" fill="#0055a0"/>
  <text x="120" y="72" text-anchor="middle" class="t6">PORTÁTIL · 1 W o 3 W</text>
  <text x="120" y="88" text-anchor="middle" class="s6">Batería, antena corta.</text>
  <text x="120" y="102" text-anchor="middle" class="s6">El agente a pie, el bombero</text>
  <rect x="244" y="54" width="200" height="62" rx="5" fill="#0055a0"/>
  <text x="344" y="72" text-anchor="middle" class="t6">MÓVIL · 3 W o 10 W</text>
  <text x="344" y="88" text-anchor="middle" class="s6">Embarcado, antena exterior.</text>
  <text x="344" y="102" text-anchor="middle" class="s6">Patrullas, ambulancias, autobombas</text>
  <rect x="468" y="54" width="200" height="62" rx="5" fill="#0055a0"/>
  <text x="568" y="72" text-anchor="middle" class="t6">FIJO · 10 W o más</text>
  <text x="568" y="88" text-anchor="middle" class="s6">Sobremesa, alimentación de red.</text>
  <text x="568" y="102" text-anchor="middle" class="s6">Dependencias y retenes</text>
  <text x="20" y="140" class="k6">CLASES DE POTENCIA NORMALIZADAS</text>
  <rect x="20" y="148" width="98" height="46" rx="4" fill="#e89822"/>
  <text x="69" y="167" text-anchor="middle" class="t6">CLASE 1</text>
  <text x="69" y="183" text-anchor="middle" class="s6">30 W</text>
  <rect x="130" y="148" width="98" height="46" rx="4" fill="#e89822"/>
  <text x="179" y="167" text-anchor="middle" class="t6">CLASE 2</text>
  <text x="179" y="183" text-anchor="middle" class="s6">10 W</text>
  <rect x="240" y="148" width="98" height="46" rx="4" fill="#e89822"/>
  <text x="289" y="167" text-anchor="middle" class="t6">CLASE 3</text>
  <text x="289" y="183" text-anchor="middle" class="s6">3 W</text>
  <rect x="350" y="148" width="98" height="46" rx="4" fill="#e89822"/>
  <text x="399" y="167" text-anchor="middle" class="t6">CLASE 4</text>
  <text x="399" y="183" text-anchor="middle" class="s6">1 W</text>
  <rect x="468" y="148" width="200" height="46" rx="4" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="568" y="165" text-anchor="middle" class="d6">Existen clases adicionales de</text>
  <text x="568" y="178" text-anchor="middle" class="d6">menor potencia. La estación base</text>
  <text x="568" y="190" text-anchor="middle" class="d6">tiene su propia escala.</text>
  <text x="20" y="216" class="k6">IDENTIDADES DEL TERMINAL</text>
  <rect x="20" y="224" width="314" height="52" rx="4" fill="#2d8659"/>
  <text x="177" y="242" text-anchor="middle" class="t6">ITSI = MNI + ISSI · y MNI = MCC + MNC</text>
  <text x="177" y="258" text-anchor="middle" class="s6">ITSI: identidad individual completa del abonado</text>
  <text x="177" y="270" text-anchor="middle" class="s6">ISSI: su parte corta, dentro de la red</text>
  <rect x="346" y="224" width="322" height="52" rx="4" fill="#2d8659"/>
  <text x="507" y="242" text-anchor="middle" class="t6">GTSI / GSSI · identidad de GRUPO</text>
  <text x="507" y="258" text-anchor="middle" class="s6">ESI: la identidad corta CIFRADA en el aire, para</text>
  <text x="507" y="270" text-anchor="middle" class="s6">impedir el seguimiento de los usuarios</text>
  <text x="670" y="300" text-anchor="end" class="n6">[Fuente: elaboración propia sobre ETSI EN 300 392-1, -2 y -7]</text>
</svg>
```

---
## D7 · TMO, DMO y las dos figuras que los unen

**Sección**: §2.2.2 — Modos de operación · §2.2.3 — Repetidor y pasarela
**Propósito**: Resolver de una vez la confusión entre **DM-REP** y **DM-GATE** sobre un escenario operativo real.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 356" role="img" aria-label="Escenario operativo que compara el modo troncalizado y el modo directo. Arriba, el modo troncalizado: los terminales en superficie hablan con la estación base y con el centro de mando. En el centro, el sótano sin cobertura, donde las dotaciones trabajan en modo directo y el centro de mando no las oye. Abajo, las dos soluciones: el repetidor DM-REP amplía el alcance dentro del modo directo pero sigue sin llegar al centro de mando, y la pasarela DM-GATE reinyecta la comunicación en la red y devuelve la visibilidad al despacho">
  <style>.t7{font:700 10px system-ui,sans-serif;fill:#fff}.s7{font:8.5px system-ui,sans-serif;fill:#fff}.d7{font:8.5px system-ui,sans-serif;fill:#333}.h7{font:700 13px system-ui,sans-serif;fill:#0055a0}.k7{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n7{font:8.5px system-ui,sans-serif;fill:#666}.b7{font:700 9px system-ui,sans-serif;fill:#0055a0}.r7{font:700 9.5px system-ui,sans-serif;fill:#d13c3c}.g7{font:700 9.5px system-ui,sans-serif;fill:#2d8659}</style>
  <text x="340" y="22" text-anchor="middle" class="h7">Repetidor y pasarela NO son lo mismo</text>
  <rect x="20" y="36" width="648" height="74" rx="5" fill="none" stroke="#2d8659" stroke-width="1.5"/>
  <text x="32" y="54" class="g7">TMO · MODO TRONCALIZADO — a través de la infraestructura (EN 300 392)</text>
  <rect x="32" y="62" width="130" height="36" rx="4" fill="#2d8659"/>
  <text x="97" y="78" text-anchor="middle" class="t7">Terminal</text>
  <text x="97" y="92" text-anchor="middle" class="s7">en superficie</text>
  <path d="M164,80 L198,80" stroke="#2d8659" stroke-width="2"/>
  <path d="M190,76 L198,80 L190,84 Z" fill="#2d8659"/>
  <rect x="200" y="62" width="130" height="36" rx="4" fill="#2d8659"/>
  <text x="265" y="78" text-anchor="middle" class="t7">Estación base</text>
  <text x="265" y="92" text-anchor="middle" class="s7">de la red</text>
  <path d="M332,80 L366,80" stroke="#2d8659" stroke-width="2"/>
  <path d="M358,76 L366,80 L358,84 Z" fill="#2d8659"/>
  <rect x="368" y="62" width="130" height="36" rx="4" fill="#2d8659"/>
  <text x="433" y="78" text-anchor="middle" class="t7">SwMI</text>
  <text x="433" y="92" text-anchor="middle" class="s7">conmutación</text>
  <path d="M500,80 L534,80" stroke="#2d8659" stroke-width="2"/>
  <path d="M526,76 L534,80 L526,84 Z" fill="#2d8659"/>
  <rect x="536" y="62" width="120" height="36" rx="4" fill="#0055a0"/>
  <text x="596" y="78" text-anchor="middle" class="t7">CENTRO</text>
  <text x="596" y="92" text-anchor="middle" class="s7">de mando</text>
  <rect x="20" y="120" width="648" height="62" rx="5" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="32" y="138" class="r7">DMO · MODO DIRECTO — terminal a terminal, sin red (EN 300 396)</text>
  <rect x="32" y="146" width="150" height="26" rx="4" fill="#d13c3c"/>
  <text x="107" y="163" text-anchor="middle" class="s7">Dotación en el sótano</text>
  <path d="M184,159 L214,159" stroke="#d13c3c" stroke-width="2"/>
  <path d="M206,155 L214,159 L206,163 Z" fill="#d13c3c"/>
  <rect x="216" y="146" width="150" height="26" rx="4" fill="#d13c3c"/>
  <text x="291" y="163" text-anchor="middle" class="s7">Otra dotación, a 20 m</text>
  <text x="380" y="157" class="d7">Se oyen entre sí, pero el centro de mando NO se entera:</text>
  <text x="380" y="170" class="d7">sin despacho, sin grabación y sin posiciones.</text>
  <text x="20" y="206" class="k7">LAS DOS FORMAS DE AMPLIAR EL MODO DIRECTO, Y LO QUE CONSIGUE CADA UNA</text>
  <rect x="20" y="214" width="314" height="104" rx="5" fill="#e89822"/>
  <text x="177" y="234" text-anchor="middle" class="t7">DM-REP · REPETIDOR</text>
  <text x="177" y="252" text-anchor="middle" class="s7">Recibe en modo directo y retransmite con más</text>
  <text x="177" y="265" text-anchor="middle" class="s7">potencia y desde mejor posición.</text>
  <text x="177" y="282" text-anchor="middle" class="s7">Tipos: 1A (una portadora) · 1B (par dúplex) · 2 (dos llamadas)</text>
  <text x="177" y="302" text-anchor="middle" class="t7">Resultado: se oyen MÁS LEJOS, pero siguen aislados</text>
  <rect x="346" y="214" width="322" height="104" rx="5" fill="#0055a0"/>
  <text x="507" y="234" text-anchor="middle" class="t7">DM-GATE · PASARELA</text>
  <text x="507" y="252" text-anchor="middle" class="s7">Recibe en modo directo y REINYECTA la comunicación</text>
  <text x="507" y="265" text-anchor="middle" class="s7">en la red troncalizada, y al revés.</text>
  <text x="507" y="282" text-anchor="middle" class="s7">El DM-REP/GATE hace las dos funciones a la vez</text>
  <text x="507" y="302" text-anchor="middle" class="t7">Resultado: vuelven a ser VISIBLES para el centro de mando</text>
  <text x="670" y="348" text-anchor="end" class="n7">[Fuente: elaboración propia sobre ETSI EN 300 392-2 y ETSI EN 300 396-4]</text>
</svg>
```

---

## D8 · Las seis interfaces normalizadas (I1 a I6)

**Sección**: §2.3 — Interfaces estándar de TETRA
**Propósito**: Memorizar las seis interfaces y su norma, distinguiendo las **dos interfaces aire** (I1 y I6), que es donde se falla.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Las seis interfaces normalizadas de TETRA. I1 es el interfaz aire en modo troncalizado, entre terminal y estación base, norma EN 300 392-2. I2 es la interfaz de línea entre la infraestructura y los equipos conectados por cable. I3 es la interfaz entre sistemas o ISI, hacia otra red TETRA, norma EN 300 392-3. I4 es la interfaz de equipo periférico o PEI, entre terminal y equipo de datos, norma EN 300 392-5. I5 es la interfaz de gestión de red. I6 es el interfaz aire en modo directo, entre terminales, norma EN 300 396">
  <style>.t8{font:700 10px system-ui,sans-serif;fill:#fff}.s8{font:8.5px system-ui,sans-serif;fill:#fff}.d8{font:8.5px system-ui,sans-serif;fill:#333}.h8{font:700 13px system-ui,sans-serif;fill:#0055a0}.k8{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n8{font:8.5px system-ui,sans-serif;fill:#666}.i8{font:700 14px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h8">Hay DOS interfaces aire: la I1 (con red) y la I6 (sin red)</text>
  <rect x="20" y="36" width="648" height="44" rx="5" fill="#d13c3c"/>
  <text x="52" y="63" text-anchor="middle" class="i8">I1</text>
  <text x="96" y="55" class="t8">INTERFAZ AIRE · modo troncalizado</text>
  <text x="96" y="70" class="s8">Terminal ↔ estación base · EN 300 392-2 · es la norma central del estándar: capas física, de enlace y de red</text>
  <rect x="20" y="88" width="648" height="44" rx="5" fill="#0055a0"/>
  <text x="52" y="115" text-anchor="middle" class="i8">I2</text>
  <text x="96" y="107" class="t8">INTERFAZ DE LÍNEA · LSI / LNI</text>
  <text x="96" y="122" class="s8">Equipos conectados por cable ↔ SwMI · consolas de despacho, estaciones fijas, grabadores y pasarelas</text>
  <rect x="20" y="140" width="648" height="44" rx="5" fill="#0055a0"/>
  <text x="52" y="167" text-anchor="middle" class="i8">I3</text>
  <text x="96" y="159" class="t8">ISI · INTERFAZ ENTRE SISTEMAS</text>
  <text x="96" y="174" class="s8">Red TETRA ↔ otra red TETRA · EN 300 392-3 · llamadas entre redes, itinerancia y mensajes cortos</text>
  <rect x="20" y="192" width="648" height="44" rx="5" fill="#0055a0"/>
  <text x="52" y="219" text-anchor="middle" class="i8">I4</text>
  <text x="96" y="211" class="t8">PEI · INTERFAZ DE EQUIPO PERIFÉRICO</text>
  <text x="96" y="226" class="s8">Terminal ↔ equipo de datos del usuario · EN 300 392-5 · comandos AT; convierte la radio en módem</text>
  <rect x="20" y="244" width="648" height="30" rx="5" fill="#0055a0"/>
  <text x="52" y="264" text-anchor="middle" class="i8">I5</text>
  <text x="96" y="263" class="s8">GESTIÓN DE RED · SwMI ↔ sistema de gestión (NMS): alarmas, configuración y supervisión</text>
  <rect x="20" y="282" width="648" height="30" rx="5" fill="#d13c3c"/>
  <text x="52" y="302" text-anchor="middle" class="i8">I6</text>
  <text x="96" y="301" class="s8">INTERFAZ AIRE EN MODO DIRECTO · terminal ↔ terminal, SIN red · EN 300 396</text>
  <text x="670" y="332" text-anchor="end" class="n8">[Fuente: ETSI ETR 300-1 y ETSI EN 300 392-1]</text>
</svg>
```

---

## D9 · El espectro de TETRA en España según el CNAF

**Sección**: §3.1 — Espectro radioeléctrico y asignación de frecuencias
**Propósito**: Reunir en un solo cuadro las bandas y las notas UN que el CNAF vigente dedica a estos sistemas. Es el diagrama con más datos literales del tema.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 350" role="img" aria-label="Mapa de las bandas de frecuencia que el Cuadro Nacional de Atribución de Frecuencias español dedica a estos sistemas. La banda 380-385 y 390-395 megahercios, según la nota UN-28, se reserva a redes de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y a redes de servicios de emergencia. Las subbandas 410-415,3 y 420-425,3 megahercios, según la nota UN-31, se destinan a sistemas digitales de acceso aleatorio de canales, TETRA y otros, con canalización de 25 kilohercios y separación dúplex de 10 megahercios. Los bloques 452-457,5 y 462-467,5 megahercios se reservan a banda ancha para protección pública y socorro. Y en la banda de 700 megahercios, 733-736 y 788-791 para el ámbito nacional y 698-703 y 753-758 para el ámbito autonómico y local">
  <style>.t9{font:700 10px system-ui,sans-serif;fill:#fff}.s9{font:8.5px system-ui,sans-serif;fill:#fff}.d9{font:8.5px system-ui,sans-serif;fill:#333}.h9{font:700 13px system-ui,sans-serif;fill:#0055a0}.k9{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n9{font:8.5px system-ui,sans-serif;fill:#666}.m9{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="20" text-anchor="middle" class="h9">CNAF vigente: Orden TDF/732/2026, de 10 de julio (BOE 17-7-2026)</text>
  <text x="340" y="36" text-anchor="middle" class="n9">Deroga la Orden ETD/1449/2021 con efectos de 18 de julio de 2026 e incorpora la CMR-23</text>
  <rect x="20" y="48" width="648" height="62" rx="5" fill="#d13c3c"/>
  <text x="36" y="68" class="m9">380-385 / 390-395 MHz — nota UN-28</text>
  <text x="36" y="85" class="s9">«Redes de servicios de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y redes de servicios</text>
  <text x="36" y="99" class="s9">de emergencia en todo el territorio nacional» · Decisión CEPT ECC/DEC(08)05 · par dúplex separado 10 MHz</text>
  <rect x="20" y="118" width="648" height="62" rx="5" fill="#0055a0"/>
  <text x="36" y="138" class="m9">410-415,3 / 420-425,3 MHz — nota UN-31</text>
  <text x="36" y="155" class="s9">«Sistemas digitales de acceso aleatorio de canales (TETRA y otros)» · canalización de 25 kHz</text>
  <text x="36" y="169" class="s9">Separación Tx/Rx de 10 MHz · es la ÚNICA mención expresa de TETRA en el CNAF</text>
  <rect x="20" y="188" width="648" height="48" rx="5" fill="#e89822"/>
  <text x="36" y="208" class="m9">452-457,5 / 462-467,5 MHz — banda ancha PPDR</text>
  <text x="36" y="225" class="s9">Decisión CEPT ECC/DEC(16)02 · «preferentemente para el sistema de ámbito nacional» (nota UN-31)</text>
  <rect x="20" y="244" width="318" height="60" rx="5" fill="#2d8659"/>
  <text x="179" y="264" text-anchor="middle" class="m9">733-736 / 788-791 MHz</text>
  <text x="179" y="281" text-anchor="middle" class="s9">PPDR de banda ancha</text>
  <text x="179" y="295" text-anchor="middle" class="s9">ÁMBITO NACIONAL</text>
  <rect x="350" y="244" width="318" height="60" rx="5" fill="#2d8659"/>
  <text x="509" y="264" text-anchor="middle" class="m9">698-703 / 753-758 MHz</text>
  <text x="509" y="281" text-anchor="middle" class="s9">PPDR de banda ancha</text>
  <text x="509" y="295" text-anchor="middle" class="s9">ÁMBITO AUTONÓMICO Y LOCAL</text>
  <text x="340" y="320" text-anchor="middle" class="k9">El bloque autonómico y local es el espectro que la norma reserva a una futura red de banda ancha crítica municipal</text>
  <text x="670" y="342" text-anchor="end" class="n9">[Fuente: Orden TDF/732/2026, notas UN-28 y UN-31, BOE núm. 173 de 17-7-2026]</text>
</svg>
```

---

## D10 · FDMA + TDMA: cuatro conversaciones en 25 kHz

**Sección**: §3.2 — Técnica de acceso múltiple por división de tiempo
**Propósito**: Visualizar la doble división —en frecuencia y en tiempo— y encadenar las cifras de la capa física.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 308" role="img" aria-label="Esquema del acceso múltiple de TETRA. Primero se divide el espectro en portadoras de 25 kilohercios, lo que es FDMA. Después cada portadora se divide en cuatro intervalos de tiempo, lo que es TDMA. El resultado son cuatro canales físicos por portadora, uno de los cuales suele ser el canal de control. Debajo, la cadena de cifras: 18.000 símbolos por segundo, dos bits por símbolo, 36 kilobits por segundo brutos por portadora y 7,2 kilobits por segundo netos por intervalo, o 28,8 agregando los cuatro">
  <style>.t10{font:700 10px system-ui,sans-serif;fill:#fff}.s10{font:8.5px system-ui,sans-serif;fill:#fff}.d10{font:8.5px system-ui,sans-serif;fill:#333}.h10{font:700 13px system-ui,sans-serif;fill:#0055a0}.k10{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n10{font:8.5px system-ui,sans-serif;fill:#666}.b10{font:700 9px system-ui,sans-serif;fill:#0055a0}.m10{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h10">Primero se divide en frecuencia (FDMA); luego, en tiempo (TDMA)</text>
  <text x="20" y="46" class="k10">PASO 1 · FDMA — el espectro se trocea en portadoras de 25 kHz</text>
  <rect x="20" y="54" width="156" height="30" rx="4" fill="#6b7c8c"/>
  <text x="98" y="73" text-anchor="middle" class="s10">Portadora 1 · 25 kHz</text>
  <rect x="184" y="54" width="156" height="30" rx="4" fill="#0055a0"/>
  <text x="262" y="73" text-anchor="middle" class="s10">Portadora 2 · 25 kHz</text>
  <rect x="348" y="54" width="156" height="30" rx="4" fill="#6b7c8c"/>
  <text x="426" y="73" text-anchor="middle" class="s10">Portadora 3 · 25 kHz</text>
  <rect x="512" y="54" width="156" height="30" rx="4" fill="#6b7c8c"/>
  <text x="590" y="73" text-anchor="middle" class="s10">Portadora 4 · 25 kHz</text>
  <path d="M262,86 L262,102" stroke="#0055a0" stroke-width="2"/>
  <path d="M258,94 L262,102 L266,94 Z" fill="#0055a0"/>
  <text x="20" y="122" class="k10">PASO 2 · TDMA — cada portadora se divide en 4 intervalos de tiempo</text>
  <rect x="20" y="130" width="158" height="44" rx="4" fill="#d13c3c"/>
  <text x="99" y="148" text-anchor="middle" class="t10">Intervalo 1</text>
  <text x="99" y="164" text-anchor="middle" class="s10">CANAL DE CONTROL</text>
  <rect x="186" y="130" width="158" height="44" rx="4" fill="#2d8659"/>
  <text x="265" y="148" text-anchor="middle" class="t10">Intervalo 2</text>
  <text x="265" y="164" text-anchor="middle" class="s10">Tráfico</text>
  <rect x="352" y="130" width="158" height="44" rx="4" fill="#2d8659"/>
  <text x="431" y="148" text-anchor="middle" class="t10">Intervalo 3</text>
  <text x="431" y="164" text-anchor="middle" class="s10">Tráfico</text>
  <rect x="518" y="130" width="150" height="44" rx="4" fill="#2d8659"/>
  <text x="593" y="148" text-anchor="middle" class="t10">Intervalo 4</text>
  <text x="593" y="164" text-anchor="middle" class="s10">Tráfico</text>
  <text x="20" y="196" class="k10">LA CADENA DE CIFRAS QUE HAY QUE SABER ENCADENAR</text>
  <rect x="20" y="204" width="120" height="52" rx="4" fill="#0055a0"/>
  <text x="80" y="224" text-anchor="middle" class="m10">18 kbaudios</text>
  <text x="80" y="241" text-anchor="middle" class="s10">símbolos/segundo</text>
  <path d="M142,230 L156,230" stroke="#0055a0" stroke-width="2"/>
  <path d="M150,226 L158,230 L150,234 Z" fill="#0055a0"/>
  <rect x="160" y="204" width="120" height="52" rx="4" fill="#0055a0"/>
  <text x="220" y="224" text-anchor="middle" class="m10">× 2 bits</text>
  <text x="220" y="241" text-anchor="middle" class="s10">π/4-DQPSK</text>
  <path d="M282,230 L296,230" stroke="#0055a0" stroke-width="2"/>
  <path d="M290,226 L298,230 L290,234 Z" fill="#0055a0"/>
  <rect x="300" y="204" width="120" height="52" rx="4" fill="#0055a0"/>
  <text x="360" y="224" text-anchor="middle" class="m10">36 kbit/s</text>
  <text x="360" y="241" text-anchor="middle" class="s10">brutos, por portadora</text>
  <path d="M422,230 L436,230" stroke="#0055a0" stroke-width="2"/>
  <path d="M430,226 L438,230 L430,234 Z" fill="#0055a0"/>
  <rect x="440" y="204" width="110" height="52" rx="4" fill="#2d8659"/>
  <text x="495" y="224" text-anchor="middle" class="m10">7,2 kbit/s</text>
  <text x="495" y="241" text-anchor="middle" class="s10">netos por intervalo</text>
  <path d="M552,230 L566,230" stroke="#2d8659" stroke-width="2"/>
  <path d="M560,226 L568,230 L560,234 Z" fill="#2d8659"/>
  <rect x="570" y="204" width="98" height="52" rx="4" fill="#d13c3c"/>
  <text x="619" y="224" text-anchor="middle" class="m10">28,8 kbit/s</text>
  <text x="619" y="241" text-anchor="middle" class="s10">con los 4 juntos</text>
  <text x="340" y="278" text-anchor="middle" class="k10">Ese techo de 28,8 kbit/s es exactamente la razón de ser de TEDS</text>
  <text x="670" y="300" text-anchor="end" class="n10">[Fuente: elaboración propia sobre ETSI EN 300 392-2]</text>
</svg>
```

---

## D11 · Modulación π/4-DQPSK

**Sección**: §3.3 — Modulación digital π/4-DQPSK
**Propósito**: Explicar de dónde salen los 2 bits por símbolo y por qué el desplazamiento de π/4 evita el paso por el origen, que es la parte que suele quedar sin entender.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 324" role="img" aria-label="Explicación de la modulación pi cuartos DQPSK de TETRA. A la izquierda, una constelación con cuatro estados de fase y el detalle de que las transiciones nunca pasan por el origen, lo que evita que la envolvente caiga a cero. A la derecha, el desglose del nombre: PSK codifica en la fase, la cuarta parte quiere decir cuatro estados y por tanto dos bits por símbolo, la D indica codificación diferencial del cambio de fase y el desplazamiento de pi cuartos evita el paso por el origen. Abajo, la comparación con la modulación GMSK que usan TETRAPOL y GSM">
  <style>.t11{font:700 10px system-ui,sans-serif;fill:#fff}.s11{font:8.5px system-ui,sans-serif;fill:#fff}.d11{font:8.5px system-ui,sans-serif;fill:#333}.h11{font:700 13px system-ui,sans-serif;fill:#0055a0}.k11{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n11{font:8.5px system-ui,sans-serif;fill:#666}.b11{font:700 9px system-ui,sans-serif;fill:#0055a0}.p11{font:700 8.5px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="22" text-anchor="middle" class="h11">Cuatro fases, dos bits por símbolo, y nunca por el centro</text>
  <rect x="20" y="36" width="220" height="196" rx="5" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="130" y="54" text-anchor="middle" class="b11">Constelación</text>
  <line x1="130" y1="70" x2="130" y2="212" stroke="#aab" stroke-width="1"/>
  <line x1="52" y1="141" x2="208" y2="141" stroke="#aab" stroke-width="1"/>
  <circle cx="130" cy="141" r="52" fill="none" stroke="#c9d6e2" stroke-width="1"/>
  <circle cx="167" cy="104" r="5" fill="#0055a0"/>
  <circle cx="167" cy="178" r="5" fill="#0055a0"/>
  <circle cx="93" cy="104" r="5" fill="#0055a0"/>
  <circle cx="93" cy="178" r="5" fill="#0055a0"/>
  <circle cx="182" cy="141" r="5" fill="#2d8659"/>
  <circle cx="78" cy="141" r="5" fill="#2d8659"/>
  <circle cx="130" cy="89" r="5" fill="#2d8659"/>
  <circle cx="130" cy="193" r="5" fill="#2d8659"/>
  <path d="M167,104 L182,141" stroke="#d13c3c" stroke-width="1.5"/>
  <path d="M182,141 L167,178" stroke="#d13c3c" stroke-width="1.5"/>
  <circle cx="130" cy="141" r="14" fill="none" stroke="#d13c3c" stroke-width="1.5" stroke-dasharray="3 2"/>
  <text x="130" y="226" text-anchor="middle" class="p11">Las transiciones esquivan el origen</text>
  <rect x="252" y="36" width="416" height="196" rx="5" fill="none" stroke="#0055a0" stroke-width="1.5"/>
  <text x="264" y="54" class="b11">Cómo se lee el nombre, pieza a pieza</text>
  <rect x="264" y="62" width="392" height="38" rx="4" fill="#0055a0"/>
  <text x="278" y="78" class="t11">PSK — Phase Shift Keying</text>
  <text x="278" y="93" class="s11">La información se codifica en la FASE de la portadora, no en amplitud ni en frecuencia</text>
  <rect x="264" y="104" width="392" height="38" rx="4" fill="#0055a0"/>
  <text x="278" y="120" class="t11">Q — quaternary: CUATRO estados de fase</text>
  <text x="278" y="135" class="s11">Cuatro estados = 2 bits por símbolo, porque 2 elevado a 2 son 4</text>
  <rect x="264" y="146" width="392" height="38" rx="4" fill="#2d8659"/>
  <text x="278" y="162" class="t11">D — differential: se codifica el CAMBIO de fase</text>
  <text x="278" y="177" class="s11">No hace falta recuperar una referencia de fase absoluta: receptor más simple y robusto</text>
  <rect x="264" y="188" width="392" height="38" rx="4" fill="#d13c3c"/>
  <text x="278" y="204" class="t11">π/4 — desplazamiento adicional de 45 grados</text>
  <text x="278" y="219" class="s11">Evita el paso por el origen: la envolvente nunca cae a cero</text>
  <rect x="20" y="244" width="648" height="52" rx="5" fill="#e89822"/>
  <text x="36" y="264" class="t11">COMPARACIÓN QUE SE PREGUNTA</text>
  <text x="36" y="281" class="s11">TETRA: π/4-DQPSK, 2 bits por símbolo, 18 kbaudios en 25 kHz · TETRAPOL y GSM: GMSK, envolvente constante, 1 bit por símbolo</text>
  <text x="670" y="316" text-anchor="end" class="n11">[Fuente: elaboración propia sobre ETSI EN 300 392-2 e Informe UIT-R M.2014]</text>
</svg>
```

---

## D12 · Jerarquía temporal: intervalo, trama, multitrama e hipertrama

**Sección**: §3.4 — Estructura de trama radio y canales lógicos
**Propósito**: Es el bloque de cifras más preguntado del tema. El diagrama las anida de menor a mayor y señala la trama 18.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 334" role="img" aria-label="Jerarquía temporal del interfaz aire de TETRA. El intervalo de tiempo dura 14,167 milisegundos. Cuatro intervalos forman una trama de 56,67 milisegundos. Dieciocho tramas forman una multitrama de 1,02 segundos, y la trama número 18 se reserva para señalización. Sesenta multitramas forman una hipertrama de 61,2 segundos, cuyo número interviene en la generación del flujo de clave del cifrado del interfaz aire">
  <style>.t12{font:700 10px system-ui,sans-serif;fill:#fff}.s12{font:8.5px system-ui,sans-serif;fill:#fff}.d12{font:8.5px system-ui,sans-serif;fill:#333}.h12{font:700 13px system-ui,sans-serif;fill:#0055a0}.k12{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n12{font:8.5px system-ui,sans-serif;fill:#666}.m12{font:700 11px system-ui,sans-serif;fill:#fff}.p12{font:7.5px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h12">14,167 ms → 56,67 ms → 1,02 s → 61,2 s</text>
  <text x="20" y="46" class="k12">NIVEL 1 · INTERVALO DE TIEMPO (time slot)</text>
  <rect x="20" y="54" width="140" height="34" rx="4" fill="#0055a0"/>
  <text x="90" y="76" text-anchor="middle" class="m12">14,167 ms</text>
  <text x="176" y="68" class="d12">Unidad básica. En el enlace descendente, la ráfaga normal lleva 432 bits útiles;</text>
  <text x="176" y="82" class="d12">en el ascendente, 336. La ráfaga de control ascendente ocupa medio intervalo.</text>
  <text x="20" y="110" class="k12">NIVEL 2 · TRAMA TDMA = 4 INTERVALOS</text>
  <rect x="20" y="118" width="158" height="32" rx="4" fill="#2d8659"/>
  <text x="99" y="139" text-anchor="middle" class="s12">Int. 1</text>
  <rect x="182" y="118" width="158" height="32" rx="4" fill="#2d8659"/>
  <text x="261" y="139" text-anchor="middle" class="s12">Int. 2</text>
  <rect x="344" y="118" width="158" height="32" rx="4" fill="#2d8659"/>
  <text x="423" y="139" text-anchor="middle" class="s12">Int. 3</text>
  <rect x="506" y="118" width="162" height="32" rx="4" fill="#2d8659"/>
  <text x="587" y="139" text-anchor="middle" class="s12">Int. 4 · trama = 56,67 ms</text>
  <text x="20" y="172" class="k12">NIVEL 3 · MULTITRAMA = 18 TRAMAS = 1,02 s</text>
  <rect x="20" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="37" y="200" text-anchor="middle" class="p12">1</text>
  <rect x="58" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="75" y="200" text-anchor="middle" class="p12">2</text>
  <rect x="96" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="113" y="200" text-anchor="middle" class="p12">3</text>
  <rect x="134" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="151" y="200" text-anchor="middle" class="p12">4</text>
  <rect x="172" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="189" y="200" text-anchor="middle" class="p12">5</text>
  <rect x="210" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="227" y="200" text-anchor="middle" class="p12">6</text>
  <rect x="248" y="180" width="182" height="30" rx="3" fill="#e89822"/>
  <text x="339" y="200" text-anchor="middle" class="p12">tramas 7 a 16 · tráfico del usuario</text>
  <rect x="434" y="180" width="34" height="30" rx="3" fill="#e89822"/>
  <text x="451" y="200" text-anchor="middle" class="p12">17</text>
  <rect x="472" y="180" width="60" height="30" rx="3" fill="#d13c3c"/>
  <text x="502" y="200" text-anchor="middle" class="p12">18</text>
  <text x="544" y="192" class="d12">La trama 18 es la TRAMA</text>
  <text x="544" y="205" class="d12">DE CONTROL: señalización</text>
  <text x="20" y="232" class="k12">NIVEL 4 · HIPERTRAMA = 60 MULTITRAMAS = 61,2 s</text>
  <rect x="20" y="240" width="648" height="34" rx="4" fill="#0055a0"/>
  <text x="340" y="254" text-anchor="middle" class="t12">60 multitramas seguidas · 61,2 segundos</text>
  <text x="340" y="268" text-anchor="middle" class="s12">El número de hipertrama interviene en la generación del flujo de clave del cifrado de interfaz aire</text>
  <rect x="20" y="284" width="648" height="22" rx="4" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="344" y="299" text-anchor="middle" class="k12">Y ahí estuvo la vulnerabilidad CVE-2022-24401: el tiempo de red se difunde SIN AUTENTICAR</text>
  <text x="670" y="326" text-anchor="end" class="n12">[Fuente: elaboración propia sobre ETSI EN 300 392-2 y Midnight Blue, TETRA:BURST 2023]</text>
</svg>
```

---
## D13 · Canales lógicos: control y tráfico

**Sección**: §3.4 — Estructura de trama radio y canales lógicos
**Propósito**: Separar canal **físico** de canal **lógico** y ordenar las dos familias, que es la forma en que se pregunta esta materia.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 328" role="img" aria-label="Clasificación de los canales lógicos de TETRA. La familia de canales de control incluye el BCCH de difusión con sus variantes BNCH de red y BSCH de sincronización, el LCH de linealización, el SCH de señalización con sus variantes completa y de medio intervalo, el ACCH asociado a una llamada en curso con las variantes rápida y lenta, y el STCH que roba capacidad al tráfico. La familia de canales de tráfico incluye el TCH de voz a 7,2 kilobits por segundo y los de datos a 7,2 sin protección, 4,8 con protección baja y 2,4 con protección alta">
  <style>.t13{font:700 10px system-ui,sans-serif;fill:#fff}.s13{font:8.5px system-ui,sans-serif;fill:#fff}.d13{font:8.5px system-ui,sans-serif;fill:#333}.h13{font:700 13px system-ui,sans-serif;fill:#0055a0}.k13{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n13{font:8.5px system-ui,sans-serif;fill:#666}.b13{font:700 9px system-ui,sans-serif;fill:#0055a0}</style>
  <text x="340" y="22" text-anchor="middle" class="h13">Canal FÍSICO es un intervalo; canal LÓGICO es lo que se transporta en él</text>
  <rect x="20" y="36" width="322" height="216" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <rect x="32" y="46" width="298" height="24" rx="3" fill="#0055a0"/>
  <text x="181" y="62" text-anchor="middle" class="t13">CANALES DE CONTROL (CCH)</text>
  <rect x="32" y="78" width="298" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="44" y="92" class="b13">BCCH · difusión</text>
  <text x="44" y="105" class="d13">BNCH (información de red) y BSCH (sincronización)</text>
  <rect x="32" y="116" width="298" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="44" y="130" class="b13">SCH · señalización</text>
  <text x="44" y="143" class="d13">SCH/F completo · SCH/HD y SCH/HU de medio intervalo</text>
  <rect x="32" y="154" width="298" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="44" y="168" class="b13">ACCH · asociado a una llamada en curso</text>
  <text x="44" y="181" class="d13">FACCH rápido (roba tráfico) y SACCH lento (trama de control)</text>
  <rect x="32" y="192" width="298" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="44" y="206" class="b13">STCH · robo de capacidad</text>
  <text x="44" y="219" class="d13">Señalización urgente sobre el canal de tráfico</text>
  <rect x="32" y="230" width="298" height="14" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="44" y="241" class="d13">LCH · linealización de los amplificadores</text>
  <rect x="354" y="36" width="314" height="216" rx="5" fill="none" stroke="#2d8659" stroke-width="2"/>
  <rect x="366" y="46" width="290" height="24" rx="3" fill="#2d8659"/>
  <text x="511" y="62" text-anchor="middle" class="t13">CANALES DE TRÁFICO (TCH)</text>
  <rect x="366" y="78" width="290" height="38" rx="3" fill="#2d8659"/>
  <text x="378" y="94" class="t13">TCH/S · VOZ</text>
  <text x="378" y="109" class="s13">7,2 kbit/s por intervalo · códec ACELP</text>
  <rect x="366" y="122" width="290" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="378" y="136" class="b13">TCH/7,2 · datos sin protección</text>
  <text x="378" y="149" class="d13">Máximo caudal, mínima robustez</text>
  <rect x="366" y="160" width="290" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="378" y="174" class="b13">TCH/4,8 · datos con protección baja</text>
  <text x="378" y="187" class="d13">Compromiso habitual</text>
  <rect x="366" y="198" width="290" height="32" rx="3" fill="#f1f5f9" stroke="#c9d6e2"/>
  <text x="378" y="212" class="b13">TCH/2,4 · datos con protección alta</text>
  <text x="378" y="225" class="d13">Para el borde de la cobertura</text>
  <text x="378" y="245" class="d13">Con los 4 intervalos agregados: hasta 28,8 kbit/s</text>
  <rect x="20" y="262" width="648" height="38" rx="4" fill="#e89822"/>
  <text x="36" y="278" class="t13">EL CANAL DE CONTROL PRINCIPAL (MCCH)</text>
  <text x="36" y="293" class="s13">Es el canal lógico de control que la estación base mantiene permanentemente activo en el intervalo 1 de la portadora principal</text>
  <text x="670" y="320" text-anchor="end" class="n13">[Fuente: elaboración propia sobre ETSI EN 300 392-2, capa MAC]</text>
</svg>
```

---

## D14 · Tipos de llamada y escalones de prioridad

**Sección**: §4.1 — Servicios de voz y comunicaciones de grupo
**Propósito**: Distinguir los cuatro tipos de llamada —y sobre todo grupo frente a difusión— y fijar los tres escalones de prioridad.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 358" role="img" aria-label="Los cuatro tipos de llamada de TETRA y los tres escalones de prioridad. Los tipos son: llamada de grupo, de uno a muchos y bidireccional; llamada individual, de uno a uno, semidúplex o dúplex completo; llamada de difusión, de uno a muchos pero unidireccional, en la que los receptores no pueden contestar; y llamada telefónica hacia la red pública. Los escalones de prioridad son: prioridad de acceso, que ordena la cola; prioridad con desalojo, que corta una llamada en curso de menor prioridad; y llamada de emergencia, con la máxima prioridad, alarma en el despacho, identidad y posición del usuario">
  <style>.t14{font:700 10px system-ui,sans-serif;fill:#fff}.s14{font:8.5px system-ui,sans-serif;fill:#fff}.d14{font:8.5px system-ui,sans-serif;fill:#333}.h14{font:700 13px system-ui,sans-serif;fill:#0055a0}.k14{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n14{font:8.5px system-ui,sans-serif;fill:#666}.b14{font:700 9px system-ui,sans-serif;fill:#0055a0}.m14{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h14">Grupo y difusión NO son lo mismo: en la difusión nadie contesta</text>
  <text x="20" y="46" class="k14">LOS CUATRO TIPOS DE LLAMADA</text>
  <rect x="20" y="54" width="158" height="86" rx="5" fill="#2d8659"/>
  <text x="99" y="74" text-anchor="middle" class="t14">DE GRUPO</text>
  <text x="99" y="92" text-anchor="middle" class="s14">Uno a MUCHOS</text>
  <text x="99" y="106" text-anchor="middle" class="s14">BIDIRECCIONAL</text>
  <text x="99" y="122" text-anchor="middle" class="s14">Semidúplex, con PTT.</text>
  <text x="99" y="134" text-anchor="middle" class="s14">Es el modo natural</text>
  <rect x="186" y="54" width="158" height="86" rx="5" fill="#0055a0"/>
  <text x="265" y="74" text-anchor="middle" class="t14">INDIVIDUAL</text>
  <text x="265" y="92" text-anchor="middle" class="s14">Uno a UNO</text>
  <text x="265" y="106" text-anchor="middle" class="s14">Semidúplex o</text>
  <text x="265" y="122" text-anchor="middle" class="s14">DÚPLEX COMPLETO,</text>
  <text x="265" y="134" text-anchor="middle" class="s14">que ocupa 2 intervalos</text>
  <rect x="352" y="54" width="158" height="86" rx="5" fill="#d13c3c"/>
  <text x="431" y="74" text-anchor="middle" class="t14">DE DIFUSIÓN</text>
  <text x="431" y="92" text-anchor="middle" class="s14">Uno a MUCHOS</text>
  <text x="431" y="106" text-anchor="middle" class="s14">UNIDIRECCIONAL</text>
  <text x="431" y="122" text-anchor="middle" class="s14">Los receptores solo</text>
  <text x="431" y="134" text-anchor="middle" class="s14">escuchan: no responden</text>
  <rect x="518" y="54" width="150" height="86" rx="5" fill="#6b7c8c"/>
  <text x="593" y="74" text-anchor="middle" class="t14">TELEFÓNICA</text>
  <text x="593" y="92" text-anchor="middle" class="s14">Hacia PSTN o PABX</text>
  <text x="593" y="106" text-anchor="middle" class="s14">EN 300 392-4</text>
  <text x="593" y="122" text-anchor="middle" class="s14">Sujeta a autorización</text>
  <text x="593" y="134" text-anchor="middle" class="s14">y tarificación</text>
  <text x="20" y="164" class="k14">LOS TRES ESCALONES DE PRIORIDAD, DE MENOS A MÁS</text>
  <rect x="20" y="172" width="200" height="70" rx="5" fill="#e89822"/>
  <text x="120" y="192" text-anchor="middle" class="m14">1 · PRIORIDAD DE ACCESO</text>
  <text x="120" y="210" text-anchor="middle" class="s14">Ordena la COLA cuando</text>
  <text x="120" y="223" text-anchor="middle" class="s14">varios piden el mismo canal.</text>
  <text x="120" y="236" text-anchor="middle" class="s14">Nadie es interrumpido</text>
  <path d="M222,207 L240,207" stroke="#0055a0" stroke-width="2"/>
  <path d="M234,203 L242,207 L234,211 Z" fill="#0055a0"/>
  <rect x="244" y="172" width="200" height="70" rx="5" fill="#e89822"/>
  <text x="344" y="192" text-anchor="middle" class="m14">2 · CON DESALOJO</text>
  <text x="344" y="210" text-anchor="middle" class="s14">Si NO hay canal libre,</text>
  <text x="344" y="223" text-anchor="middle" class="s14">CORTA una llamada en curso</text>
  <text x="344" y="236" text-anchor="middle" class="s14">de prioridad inferior</text>
  <path d="M446,207 L464,207" stroke="#0055a0" stroke-width="2"/>
  <path d="M458,203 L466,207 L458,211 Z" fill="#0055a0"/>
  <rect x="468" y="172" width="200" height="70" rx="5" fill="#d13c3c"/>
  <text x="568" y="192" text-anchor="middle" class="m14">3 · DE EMERGENCIA</text>
  <text x="568" y="210" text-anchor="middle" class="s14">Botón de emergencia.</text>
  <text x="568" y="223" text-anchor="middle" class="s14">Máxima prioridad, alarma</text>
  <text x="568" y="236" text-anchor="middle" class="s14">en despacho, identidad y posición</text>
  <text x="20" y="266" class="k14">SERVICIOS SUPLEMENTARIOS QUE HAY QUE SABER NOMBRAR</text>
  <rect x="20" y="274" width="648" height="56" rx="5" fill="#0055a0"/>
  <text x="36" y="292" class="s14">DGNA · asignación dinámica de grupos por el aire, desde la consola · Entrada tardía · Escucha ambiente (micrófono remoto)</text>
  <text x="36" y="307" class="s14">Escucha discreta · Inclusión de un supervisor en una llamada · Identificación del llamante por alias</text>
  <text x="36" y="322" class="s14">Inhabilitación remota del terminal: temporal (stun) o permanente (kill)</text>
  <text x="670" y="350" text-anchor="end" class="n14">[Fuente: elaboración propia sobre ETSI EN 300 392, partes 2 y 9 a 12]</text>
</svg>
```

---

## D15 · Servicios de datos: estados, SDS, circuito y paquetes

**Sección**: §4.2 — Servicios de datos
**Propósito**: Fijar los tamaños de los SDS y la diferencia entre datos por circuito y por paquetes, junto con el techo real de capacidad.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 348" role="img" aria-label="Los servicios de datos de TETRA. Arriba, la mensajería corta: el mensaje de estado con 16 bits precodificados, el SDS tipo 1 con 16 bits, el tipo 2 con 32, el tipo 3 con 64 y el tipo 4 con hasta 2047 bits definidos por el usuario, sobre el que se define la capa de transporte SDS-TL con acuse de recibo y encadenamiento. Abajo, la comparación entre datos por circuito, que reserva un canal con tasas de 7,2, 4,8 o 2,4 kilobits por segundo por intervalo, y datos por paquetes, que comparte recursos y transporta IP mediante SNDCP">
  <style>.t15{font:700 10px system-ui,sans-serif;fill:#fff}.s15{font:8.5px system-ui,sans-serif;fill:#fff}.d15{font:8.5px system-ui,sans-serif;fill:#333}.h15{font:700 13px system-ui,sans-serif;fill:#0055a0}.k15{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n15{font:8.5px system-ui,sans-serif;fill:#666}.b15{font:700 9px system-ui,sans-serif;fill:#0055a0}.m15{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h15">El SDS tipo 4 es el que se usa: hasta 2.047 bits</text>
  <text x="20" y="46" class="k15">MENSAJERÍA CORTA (SDS) — viaja por los canales de CONTROL, sin ocupar canal de tráfico</text>
  <rect x="20" y="54" width="120" height="60" rx="4" fill="#6b7c8c"/>
  <text x="80" y="74" text-anchor="middle" class="m15">ESTADO</text>
  <text x="80" y="91" text-anchor="middle" class="s15">16 bits</text>
  <text x="80" y="105" text-anchor="middle" class="s15">precodificados</text>
  <rect x="152" y="54" width="120" height="60" rx="4" fill="#0055a0"/>
  <text x="212" y="74" text-anchor="middle" class="m15">SDS TIPO 1</text>
  <text x="212" y="91" text-anchor="middle" class="s15">16 bits</text>
  <text x="212" y="105" text-anchor="middle" class="s15">de usuario</text>
  <rect x="284" y="54" width="120" height="60" rx="4" fill="#0055a0"/>
  <text x="344" y="74" text-anchor="middle" class="m15">SDS TIPO 2</text>
  <text x="344" y="91" text-anchor="middle" class="s15">32 bits</text>
  <text x="344" y="105" text-anchor="middle" class="s15">de usuario</text>
  <rect x="416" y="54" width="120" height="60" rx="4" fill="#0055a0"/>
  <text x="476" y="74" text-anchor="middle" class="m15">SDS TIPO 3</text>
  <text x="476" y="91" text-anchor="middle" class="s15">64 bits</text>
  <text x="476" y="105" text-anchor="middle" class="s15">de usuario</text>
  <rect x="548" y="54" width="120" height="60" rx="4" fill="#2d8659"/>
  <text x="608" y="74" text-anchor="middle" class="m15">SDS TIPO 4</text>
  <text x="608" y="91" text-anchor="middle" class="s15">hasta 2.047 bits</text>
  <text x="608" y="105" text-anchor="middle" class="s15">de usuario</text>
  <rect x="20" y="124" width="648" height="34" rx="4" fill="#e89822"/>
  <text x="36" y="140" class="t15">SDS-TL · capa de transporte sobre el tipo 4</text>
  <text x="36" y="153" class="s15">Añade identificador de protocolo de aplicación, acuse de recibo y encadenamiento. Es la base del texto y del envío de posición (LIP)</text>
  <text x="20" y="182" class="k15">LOS DOS MODOS DE DATOS DE MAYOR VOLUMEN</text>
  <rect x="20" y="190" width="314" height="112" rx="5" fill="none" stroke="#d13c3c" stroke-width="2"/>
  <rect x="32" y="200" width="290" height="22" rx="3" fill="#d13c3c"/>
  <text x="177" y="216" text-anchor="middle" class="t15">POR CIRCUITO — recurso RESERVADO</text>
  <text x="44" y="238" class="d15">Sin protección de errores: 7,2 kbit/s por intervalo</text>
  <text x="44" y="252" class="d15">Protección baja: 4,8 kbit/s por intervalo</text>
  <text x="44" y="266" class="d15">Protección alta: 2,4 kbit/s por intervalo</text>
  <text x="44" y="282" class="b15">Agregando los 4 intervalos: hasta 28,8 kbit/s</text>
  <text x="44" y="295" class="d15">Ineficiente a ráfagas, pero de caudal predecible</text>
  <rect x="346" y="190" width="322" height="112" rx="5" fill="none" stroke="#2d8659" stroke-width="2"/>
  <rect x="358" y="200" width="298" height="22" rx="3" fill="#2d8659"/>
  <text x="507" y="216" text-anchor="middle" class="t15">POR PAQUETES — recurso COMPARTIDO</text>
  <text x="370" y="238" class="d15">Solo consume canal cuando hay paquetes que enviar</text>
  <text x="370" y="252" class="d15">Transporta IP mediante el protocolo SNDCP de capa 3</text>
  <text x="370" y="266" class="d15">El terminal se comporta como un dispositivo IP más</text>
  <text x="370" y="282" class="b15">Es el modo adecuado para consultas y aplicaciones</text>
  <text x="370" y="295" class="d15">Eficiente a ráfagas, sin caudal garantizado</text>
  <text x="340" y="318" text-anchor="middle" class="k15">Con este techo se hace texto, posiciones y consultas breves; no se hace vídeo ni cartografía</text>
  <text x="670" y="340" text-anchor="end" class="n15">[Fuente: elaboración propia sobre ETSI EN 300 392-2, capa 3]</text>
</svg>
```

---

## D16 · Cadena de seguridad: autenticación, claves y clases

**Sección**: §4.3.1 — Autenticación · §4.3.2 — Cifrado en la interfaz aire
**Propósito**: Encadenar autenticación → clave derivada → clase de seguridad, que es la relación que explica por qué una red sin autenticación es estructuralmente más débil.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 356" role="img" aria-label="Cadena de seguridad de TETRA. Primero, la autenticación por desafío y respuesta con la clave secreta K, que nunca viaja por el aire y que puede ejecutarse en sentido inverso para que el terminal verifique a la red y evitar así una estación base falsa. De la autenticación se deriva la clave DCK. Después, la jerarquía de claves: K de autenticación, DCK derivada individual, CCK común de área, SCK estática precargada, y GCK de grupo que se combina para dar la MGCK. Finalmente, las clases de seguridad: SC1 sin cifrar, SC2 con clave estática y SC3 con clave derivada y común, más la variante SC3G con clave de grupo">
  <style>.t16{font:700 10px system-ui,sans-serif;fill:#fff}.s16{font:8.5px system-ui,sans-serif;fill:#fff}.d16{font:8.5px system-ui,sans-serif;fill:#333}.h16{font:700 13px system-ui,sans-serif;fill:#0055a0}.k16{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n16{font:8.5px system-ui,sans-serif;fill:#666}.b16{font:700 9px system-ui,sans-serif;fill:#0055a0}.m16{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h16">Autenticar y cifrar están ENCADENADOS: de la autenticación sale la clave</text>
  <text x="20" y="46" class="k16">PASO 1 · AUTENTICACIÓN POR DESAFÍO-RESPUESTA (algoritmos TAA1; TAA2 con el set B)</text>
  <rect x="20" y="54" width="150" height="56" rx="4" fill="#0055a0"/>
  <text x="95" y="74" text-anchor="middle" class="t16">Clave secreta K</text>
  <text x="95" y="90" text-anchor="middle" class="s16">Compartida terminal-red.</text>
  <text x="95" y="103" text-anchor="middle" class="s16">NUNCA viaja por el aire</text>
  <path d="M172,82 L190,82" stroke="#0055a0" stroke-width="2"/>
  <path d="M184,78 L192,82 L184,86 Z" fill="#0055a0"/>
  <rect x="194" y="54" width="150" height="56" rx="4" fill="#0055a0"/>
  <text x="269" y="74" text-anchor="middle" class="t16">Desafío</text>
  <text x="269" y="90" text-anchor="middle" class="s16">La red envía un número</text>
  <text x="269" y="103" text-anchor="middle" class="s16">aleatorio al terminal</text>
  <path d="M346,82 L364,82" stroke="#0055a0" stroke-width="2"/>
  <path d="M358,78 L366,82 L358,86 Z" fill="#0055a0"/>
  <rect x="368" y="54" width="150" height="56" rx="4" fill="#0055a0"/>
  <text x="443" y="74" text-anchor="middle" class="t16">Respuesta</text>
  <text x="443" y="90" text-anchor="middle" class="s16">El terminal calcula y</text>
  <text x="443" y="103" text-anchor="middle" class="s16">la red compara</text>
  <path d="M520,82 L538,82" stroke="#2d8659" stroke-width="2"/>
  <path d="M532,78 L540,82 L532,86 Z" fill="#2d8659"/>
  <rect x="542" y="54" width="126" height="56" rx="4" fill="#2d8659"/>
  <text x="605" y="74" text-anchor="middle" class="t16">Se deriva la DCK</text>
  <text x="605" y="90" text-anchor="middle" class="s16">Clave de cifrado</text>
  <text x="605" y="103" text-anchor="middle" class="s16">propia de esa sesión</text>
  <rect x="20" y="120" width="648" height="24" rx="4" fill="#d13c3c"/>
  <text x="344" y="136" text-anchor="middle" class="s16">Si la autenticación es MUTUA, el terminal verifica también a la red: es la defensa contra la ESTACIÓN BASE FALSA</text>
  <text x="20" y="168" class="k16">PASO 2 · JERARQUÍA DE CLAVES</text>
  <rect x="20" y="176" width="126" height="58" rx="4" fill="#0055a0"/>
  <text x="83" y="196" text-anchor="middle" class="m16">K</text>
  <text x="83" y="212" text-anchor="middle" class="s16">Autenticación.</text>
  <text x="83" y="225" text-anchor="middle" class="s16">No cifra tráfico</text>
  <rect x="158" y="176" width="126" height="58" rx="4" fill="#2d8659"/>
  <text x="221" y="196" text-anchor="middle" class="m16">DCK</text>
  <text x="221" y="212" text-anchor="middle" class="s16">Derivada, individual.</text>
  <text x="221" y="225" text-anchor="middle" class="s16">La más fuerte</text>
  <rect x="296" y="176" width="126" height="58" rx="4" fill="#2d8659"/>
  <text x="359" y="196" text-anchor="middle" class="m16">CCK</text>
  <text x="359" y="212" text-anchor="middle" class="s16">Común de área.</text>
  <text x="359" y="225" text-anchor="middle" class="s16">Se envía por OTAR</text>
  <rect x="434" y="176" width="112" height="58" rx="4" fill="#e89822"/>
  <text x="490" y="196" text-anchor="middle" class="m16">SCK</text>
  <text x="490" y="212" text-anchor="middle" class="s16">Estática, precargada.</text>
  <text x="490" y="225" text-anchor="middle" class="s16">La más débil</text>
  <rect x="558" y="176" width="110" height="58" rx="4" fill="#6b7c8c"/>
  <text x="613" y="196" text-anchor="middle" class="m16">GCK → MGCK</text>
  <text x="613" y="212" text-anchor="middle" class="s16">De grupo. No se usa</text>
  <text x="613" y="225" text-anchor="middle" class="s16">directa: se modifica</text>
  <text x="20" y="258" class="k16">PASO 3 · CLASES DE SEGURIDAD DEL INTERFAZ AIRE</text>
  <rect x="20" y="266" width="158" height="62" rx="4" fill="#d13c3c"/>
  <text x="99" y="286" text-anchor="middle" class="m16">SC1</text>
  <text x="99" y="303" text-anchor="middle" class="s16">SIN cifrado del aire.</text>
  <text x="99" y="316" text-anchor="middle" class="s16">Puede usar ESI</text>
  <rect x="186" y="266" width="158" height="62" rx="4" fill="#e89822"/>
  <text x="265" y="286" text-anchor="middle" class="m16">SC2</text>
  <text x="265" y="303" text-anchor="middle" class="s16">Clave estática SCK.</text>
  <text x="265" y="316" text-anchor="middle" class="s16">Es la clase del modo directo</text>
  <rect x="352" y="266" width="158" height="62" rx="4" fill="#2d8659"/>
  <text x="431" y="286" text-anchor="middle" class="m16">SC3</text>
  <text x="431" y="303" text-anchor="middle" class="s16">DCK + CCK, con</text>
  <text x="431" y="316" text-anchor="middle" class="s16">AUTENTICACIÓN. Recomendada</text>
  <rect x="518" y="266" width="150" height="62" rx="4" fill="#2d8659"/>
  <text x="593" y="286" text-anchor="middle" class="m16">SC3G</text>
  <text x="593" y="303" text-anchor="middle" class="s16">SC3 más GCK/MGCK:</text>
  <text x="593" y="316" text-anchor="middle" class="s16">cifrado propio por grupo</text>
  <text x="670" y="348" text-anchor="end" class="n16">[Fuente: elaboración propia sobre ETSI EN 300 392-7 y TCCA TTR 001-11 v4.1.0 (2023)]</text>
</svg>
```

---

## D17 · Interfaz aire frente a extremo a extremo, y qué rompió cada divulgación

**Sección**: §4.3.2 — Cifrado en la interfaz aire · §4.3.3 — Cifrado extremo a extremo
**Propósito**: Fijar de una vez qué protege cada capa de cifrado y situar en ellas los hallazgos de 2023 y de 2025.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 390" role="img" aria-label="Comparación entre el cifrado de interfaz aire y el cifrado extremo a extremo. El cifrado de interfaz aire protege el tramo entre terminal y estación base y se descifra en la estación base, de modo que no protege frente al operador de la red. El cifrado extremo a extremo protege de terminal a terminal y la infraestructura no puede leerlo. Debajo, la cronología de las divulgaciones: en octubre de 2022 el ETSI libera el conjunto de algoritmos TEA set B con TEA5, TEA6 y TEA7; en agosto de 2023 se publica TETRA:BURST con cinco vulnerabilidades incluida la reducción de clave de TEA1; en febrero de 2025 el ETSI publica la especificación del TEA set A; y en agosto de 2025 se presenta 2TETRA:2BURST, que alcanza al cifrado extremo a extremo">
  <style>.t17{font:700 10px system-ui,sans-serif;fill:#fff}.s17{font:8.5px system-ui,sans-serif;fill:#fff}.d17{font:8.5px system-ui,sans-serif;fill:#333}.h17{font:700 13px system-ui,sans-serif;fill:#0055a0}.k17{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n17{font:8.5px system-ui,sans-serif;fill:#666}.b17{font:700 9px system-ui,sans-serif;fill:#0055a0}.m17{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h17">Uno se descifra en la estación base; el otro, no</text>
  <rect x="20" y="36" width="648" height="60" rx="5" fill="#0055a0"/>
  <text x="36" y="56" class="m17">CIFRADO DE INTERFAZ AIRE (AIE) — capa 2 del interfaz aire</text>
  <text x="36" y="74" class="s17">Terminal ↔ ESTACIÓN BASE. Cifra voz, datos, señalización y, con ESI, también las identidades.</text>
  <text x="36" y="88" class="s17">Se DESCIFRA en la estación base: NO protege frente al operador de la red ni frente a un compromiso de la infraestructura</text>
  <rect x="20" y="104" width="648" height="60" rx="5" fill="#2d8659"/>
  <text x="36" y="124" class="m17">CIFRADO EXTREMO A EXTREMO (E2EE) — por encima, sobre la carga útil</text>
  <text x="36" y="142" class="s17">Terminal ↔ TERMINAL. Atraviesa toda la infraestructura sin que ésta pueda leerlo.</text>
  <text x="36" y="156" class="s17">El ETSI NO impone el algoritmo: define el marco de transporte y sincronización. Hoy predomina AES</text>
  <rect x="20" y="172" width="648" height="40" rx="4" fill="#e89822"/>
  <text x="344" y="189" text-anchor="middle" class="s17">Son COMPLEMENTARIOS, no alternativos: se usan juntos.</text>
  <text x="344" y="203" text-anchor="middle" class="s17">El E2EE inutiliza pasarelas, grabación en claro e interconexión, salvo puntos de descifrado autorizados</text>
  <text x="20" y="234" class="k17">CRONOLOGÍA DE LAS DIVULGACIONES Y DE LAS RESPUESTAS</text>
  <rect x="20" y="242" width="158" height="86" rx="5" fill="#2d8659"/>
  <text x="99" y="262" text-anchor="middle" class="t17">OCT · 2022</text>
  <text x="99" y="280" text-anchor="middle" class="s17">El ETSI libera el</text>
  <text x="99" y="293" text-anchor="middle" class="s17">TEA set B: TEA5, TEA6</text>
  <text x="99" y="306" text-anchor="middle" class="s17">y TEA7, con claves</text>
  <text x="99" y="319" text-anchor="middle" class="s17">extendidas y TAA2</text>
  <rect x="186" y="242" width="158" height="86" rx="5" fill="#d13c3c"/>
  <text x="265" y="262" text-anchor="middle" class="t17">AGO · 2023</text>
  <text x="265" y="280" text-anchor="middle" class="s17">TETRA:BURST · 5 CVE.</text>
  <text x="265" y="293" text-anchor="middle" class="s17">TEA1 con clave reducida</text>
  <text x="265" y="306" text-anchor="middle" class="s17">a ~32 bits efectivos</text>
  <text x="265" y="319" text-anchor="middle" class="s17">(CVE-2022-24402)</text>
  <rect x="352" y="242" width="158" height="86" rx="5" fill="#0055a0"/>
  <text x="431" y="262" text-anchor="middle" class="t17">FEB · 2025</text>
  <text x="431" y="280" text-anchor="middle" class="s17">El ETSI PUBLICA la</text>
  <text x="431" y="293" text-anchor="middle" class="s17">especificación del</text>
  <text x="431" y="306" text-anchor="middle" class="s17">TEA set A en la</text>
  <text x="431" y="319" text-anchor="middle" class="s17">TS 104 053-1</text>
  <rect x="518" y="242" width="150" height="86" rx="5" fill="#d13c3c"/>
  <text x="593" y="262" text-anchor="middle" class="t17">AGO · 2025</text>
  <text x="593" y="280" text-anchor="middle" class="s17">2TETRA:2BURST.</text>
  <text x="593" y="293" text-anchor="middle" class="s17">Alcanza al E2EE y</text>
  <text x="593" y="306" text-anchor="middle" class="s17">al propio protocolo:</text>
  <text x="593" y="319" text-anchor="middle" class="s17">no autentica mensajes</text>
  <rect x="20" y="340" width="648" height="22" rx="4" fill="none" stroke="#d13c3c" stroke-width="1.5"/>
  <text x="344" y="355" text-anchor="middle" class="k17">Consecuencia práctica: no basta con dejar de USAR TEA1; hay que dejar de SOPORTARLO (CVE-2025-52943)</text>
  <text x="340" y="382" text-anchor="middle" class="n17">[Fuente: Midnight Blue (2023 y 2025), TCCA Research Disclosures y ETSI TS 104 053-1]</text>
</svg>
```

---

## D18 · De TETRA a la banda ancha crítica

**Sección**: §5.4 — Evolución hacia TEDS y coexistencia con redes de banda ancha crítica
**Propósito**: Separar los dos caminos de evolución —TEDS dentro de TETRA, MCPTT fuera— y mostrar que la respuesta real es la coexistencia.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 360" role="img" aria-label="Los dos caminos de evolución de TETRA. El primero es TEDS, dentro de TETRA, que es la aportación de datos de la Release 2 con anchos de canal de 25, 50, 100 y 150 kilohercios y modulaciones pi octavos D8PSK, 4-QAM, 16-QAM y 64-QAM con adaptación al enlace. El segundo es la banda ancha crítica del 3GPP, con MCPTT normalizado en la Release 13 de 2016 y MCVideo y MCData en la Release 14, apoyados en los habilitadores GCSE, eMBMS y ProSe. Abajo, las cuatro razones por las que la transición es lenta y el modelo de coexistencia que se impone">
  <style>.t18{font:700 10px system-ui,sans-serif;fill:#fff}.s18{font:8.5px system-ui,sans-serif;fill:#fff}.d18{font:8.5px system-ui,sans-serif;fill:#333}.h18{font:700 13px system-ui,sans-serif;fill:#0055a0}.k18{font:700 9.5px system-ui,sans-serif;fill:#0055a0}.n18{font:8.5px system-ui,sans-serif;fill:#666}.b18{font:700 9px system-ui,sans-serif;fill:#0055a0}.m18{font:700 11px system-ui,sans-serif;fill:#fff}</style>
  <text x="340" y="22" text-anchor="middle" class="h18">Dos caminos, y la respuesta real es la coexistencia</text>
  <rect x="20" y="36" width="314" height="132" rx="5" fill="none" stroke="#2d8659" stroke-width="2"/>
  <rect x="32" y="46" width="290" height="24" rx="3" fill="#2d8659"/>
  <text x="177" y="62" text-anchor="middle" class="t18">CAMINO 1 · TEDS — dentro de TETRA</text>
  <text x="44" y="86" class="d18">TETRA Release 2. Mantiene todo lo que TETRA hace bien</text>
  <text x="44" y="100" class="d18">y amplía el canal de datos.</text>
  <text x="44" y="118" class="b18">Anchos de canal: 25, 50, 100 y 150 kHz</text>
  <text x="44" y="132" class="b18">Modulaciones: π/8-D8PSK · 4-QAM · 16-QAM · 64-QAM</text>
  <text x="44" y="148" class="d18">Con adaptación al enlace: modulación densa cerca de la</text>
  <text x="44" y="161" class="d18">estación base y robusta (4-QAM) en el borde de la célula</text>
  <rect x="346" y="36" width="322" height="132" rx="5" fill="none" stroke="#0055a0" stroke-width="2"/>
  <rect x="358" y="46" width="298" height="24" rx="3" fill="#0055a0"/>
  <text x="507" y="62" text-anchor="middle" class="t18">CAMINO 2 · BANDA ANCHA CRÍTICA — fuera de TETRA</text>
  <text x="370" y="86" class="b18">MCPTT · voz de grupo con PTT, prioridad y desalojo</text>
  <text x="370" y="100" class="d18">3GPP Release 13, culminada en 2016 · TS 22.179</text>
  <text x="370" y="118" class="b18">MCVideo y MCData · Release 14</text>
  <text x="370" y="132" class="d18">Habilitadores previos del propio 3GPP:</text>
  <text x="370" y="148" class="d18">GCSE (grupo) · eMBMS (difusión) · ProSe (proximidad,</text>
  <text x="370" y="161" class="d18">el equivalente conceptual del modo directo)</text>
  <text x="20" y="192" class="k18">POR QUÉ LA TRANSICIÓN ES LENTA</text>
  <rect x="20" y="200" width="158" height="66" rx="4" fill="#e89822"/>
  <text x="99" y="218" text-anchor="middle" class="t18">1 · COBERTURA</text>
  <text x="99" y="234" text-anchor="middle" class="s18">Replicar con LTE propio</text>
  <text x="99" y="247" text-anchor="middle" class="s18">es carísimo; con LTE</text>
  <text x="99" y="260" text-anchor="middle" class="s18">comercial se pierde control</text>
  <rect x="186" y="200" width="158" height="66" rx="4" fill="#e89822"/>
  <text x="265" y="218" text-anchor="middle" class="t18">2 · MODO DIRECTO</text>
  <text x="265" y="234" text-anchor="middle" class="s18">ProSe aún no iguala</text>
  <text x="265" y="247" text-anchor="middle" class="s18">al DMO, y el DMO es</text>
  <text x="265" y="260" text-anchor="middle" class="s18">innegociable en rescate</text>
  <rect x="352" y="200" width="158" height="66" rx="4" fill="#e89822"/>
  <text x="431" y="218" text-anchor="middle" class="t18">3 · AUTONOMÍA</text>
  <text x="431" y="234" text-anchor="middle" class="s18">Un terminal de banda</text>
  <text x="431" y="247" text-anchor="middle" class="s18">ancha consume mucho</text>
  <text x="431" y="260" text-anchor="middle" class="s18">más que uno estrecho</text>
  <rect x="518" y="200" width="150" height="66" rx="4" fill="#e89822"/>
  <text x="593" y="218" text-anchor="middle" class="t18">4 · PARQUE</text>
  <text x="593" y="234" text-anchor="middle" class="s18">Miles de terminales,</text>
  <text x="593" y="247" text-anchor="middle" class="s18">personal formado y</text>
  <text x="593" y="260" text-anchor="middle" class="s18">procedimientos escritos</text>
  <rect x="20" y="280" width="648" height="52" rx="5" fill="#0055a0"/>
  <text x="36" y="300" class="m18">EL MODELO QUE SE IMPONE: DOS REDES COMPLEMENTARIAS</text>
  <text x="36" y="318" class="s18">TETRA para la voz crítica y los datos cortos garantizados · banda ancha para lo que necesita caudal · terminales híbridos · migración por fases</text>
  <text x="670" y="352" text-anchor="end" class="n18">[Fuente: elaboración propia sobre ETSI TR 102 580, 3GPP Releases 13 y 14 y el CNAF 2026]</text>
</svg>
```
