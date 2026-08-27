# Tema 38 — Índice

> **Título oficial**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Introducción y fundamentos de los sistemas móviles de radiocomunicación**
   1.1. Concepto y evolución de la radiocomunicación móvil privada (PMR)
   1.2. Sistemas *trunked* o troncalizados: concepto y ventajas
   1.3. Estandarización de TETRA por el ETSI: *Trans European* / *Terrestrial Trunked Radio*

2. **Arquitectura y componentes de la red TETRA**
   2.1. Infraestructura de conmutación y gestión (SwMI)
   2.1.1. Estaciones base (BS)
   2.1.2. Nodos de conmutación y control de red
   2.1.3. Centros de gestión y administración del sistema
   2.2. Terminales de usuario
   2.2.1. Equipos portátiles, móviles y fijos
   2.2.2. Modos de operación: modo troncalizado (TMO) y modo directo (DMO)
   2.2.3. Funciones de repetición y pasarela (*repeater* y *gateway*)
   2.3. Interfaces estándar de TETRA
   2.3.1. Interfaz aire (*air interface*)
   2.3.2. Interfaz de interconexión entre sistemas (ISI)
   2.3.3. Interfaz de línea (LNI) e interfaces de datos

3. **Capa física y transmisión radio en TETRA**
   3.1. Espectro radioeléctrico y asignación de frecuencias
   3.2. Técnica de acceso múltiple por división de tiempo (TDMA)
   3.3. Modulación digital π/4-DQPSK
   3.4. Estructura de trama radio y canales lógicos

4. **Servicios y seguridad en sistemas TETRA**
   4.1. Servicios de voz y comunicaciones de grupo
   4.1.1. Llamadas individuales, de grupo y de difusión
   4.1.2. Gestión de prioridades y llamadas de emergencia
   4.2. Servicios de datos
   4.2.1. Servicio de mensajes cortos (SDS)
   4.2.2. Transmisión de datos por paquetes y circuitos
   4.3. Mecanismos de seguridad
   4.3.1. Autenticación de usuarios y terminales
   4.3.2. Cifrado en la interfaz aire
   4.3.3. Cifrado extremo a extremo (E2EE)

5. **Ámbito público, normativa y evolución tecnológica**
   5.1. Uso de TETRA en servicios de emergencia y seguridad pública
   5.2. Marco normativo y regulación del espectro radioeléctrico
   5.3. Requisitos de disponibilidad, resiliencia y calidad de servicio (QoS)
   5.4. Evolución hacia TEDS y coexistencia con redes de banda ancha crítica

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| Significado de las siglas | **TE**rrestrial **TRA**nked **RA**dio (nombre actual). El original fue *Trans European Trunked Radio*, cambiado por el ETSI cuando el estándar dejó de ser solo europeo |
| Organismo que lo normaliza | **ETSI** (European Telecommunications Standards Institute). Serie **EN 300 392** (V+D), **EN 300 396** (DMO), **EN 300 394** (conformidad), **EN 300 395** (códec de voz) |
| Acceso al medio | **FDMA + TDMA**: portadoras de **25 kHz** con **4 intervalos de tiempo** (*time slots*) por portadora |
| Modulación (Release 1) | **π/4-DQPSK**, **18.000 símbolos/s**, 2 bits por símbolo → **36 kbit/s** brutos por portadora |
| Duración del intervalo | **14,167 ms** · trama = 4 intervalos = **56,67 ms** · multitrama = 18 tramas = **1,02 s** · hipertrama = 60 multitramas = **61,2 s** |
| Trama de control | La **trama 18** de cada multitrama se reserva para señalización (*control frame*) |
| Códec de voz | **ACELP**, **137 bits cada 30 ms** = **4,567 kbit/s** netos; **7,2 kbit/s** por intervalo con protección de errores |
| Radio de célula máximo | **58 km** en TETRA Release 1 (límite impuesto por la estructura de intervalos) |
| Bandas en España (emergencias) | **380-385 / 390-395 MHz**, reservadas por la **nota UN-28** del CNAF a las FCSE y a los servicios de emergencia |
| Bandas en España (TETRA civil) | **410-415,3 / 420-425,3 MHz**, que la **nota UN-31** destina literalmente a «sistemas digitales de acceso aleatorio de canales (**TETRA** y otros)» con canalización de 25 kHz y separación dúplex de **10 MHz** |
| CNAF vigente | **Orden TDF/732/2026, de 10 de julio** (BOE núm. 173, de 17-7-2026). **Sustituye** a la Orden ETD/1449/2021 con efectos de **18 de julio de 2026** |
| Título habilitante de un ayuntamiento | **Afectación demanial** — art. **88.5.b)** de la Ley 11/2022: la autorización individual para autoprestación no vale para las Administraciones públicas |
| Modos de operación | **TMO** (a través de la infraestructura) y **DMO** (terminal a terminal, sin red) |
| Elementos que amplían el DMO | **DM-REP** (repetidor, tipo 1A, 1B o 2) y **DM-GATE** (pasarela hacia la red V+D); el **DM-REP/GATE** hace las dos cosas |
| Interfaces normalizadas | **I1** aire (TMO) · **I2** línea (LSI/LNI) · **I3** **ISI** entre sistemas · **I4** terminal (**PEI**) · **I5** gestión de red · **I6** aire en modo directo |
| Tiempo de establecimiento | **< 300 ms** en llamada de grupo, frente a varios segundos en telefonía celular |
| Cifrado de interfaz aire | Clases de seguridad **SC1** (sin cifrar) · **SC2** (clave estática **SCK**) · **SC3** (clave derivada **DCK** + **CCK**), con la variante **SC3G** cuando se usa **GCK** |
| Algoritmos de cifrado | **TEA set A**: TEA1-TEA4 (2 de exportación libre, 2 restringidos). **TEA set B**: **TEA5, TEA6 y TEA7** (octubre de 2022), con claves extendidas y autenticación **TAA2** |
| Vulnerabilidades publicadas | **TETRA:BURST** (agosto de 2023, 5 CVE; **TEA1 con clave reducida a ~32 bits**) y **2TETRA:2BURST** (7 de agosto de 2025, Black Hat USA), que alcanza al **cifrado extremo a extremo** |
| Datos de banda ancha | **TEDS** (TETRA Release 2): canales de **25, 50, 100 y 150 kHz** con π/8-D8PSK, 4-QAM, 16-QAM y 64-QAM |
| Evolución | **MCPTT**, normalizado por el **3GPP en la Release 13** (2016); banda **700 MHz** para PPDR de banda ancha en el CNAF |
| La red del Estado NO es TETRA | **SIRDEE** usa **TETRAPOL** (FDMA, 12,5 kHz, GMSK), no TETRA. Es la confusión más penalizada del tema |
