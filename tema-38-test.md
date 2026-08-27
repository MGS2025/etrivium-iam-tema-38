# Tema 38 — Test de Autoevaluación

> **Título**: Sistema de radiocomunicación Trans European Trunked Radio o TErrestrial Trunked RAdio (TETRA).
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-08-27
> **Fuentes**: ver tema-38-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Fundamentos de la PMR y del *trunking* (P1-P9), Arquitectura y componentes (P10-P22), Capa física y transmisión radio (P23-P33), Servicios y seguridad (P34-P48), Ámbito público, normativa y evolución (P49-P60).

---

### Pregunta 1

**¿Cuál es la expansión vigente de las siglas TETRA según el ETSI?**

A) TErrestrial TRunked RAdio
B) Trans European Trunked Radio
C) Telephony and Trunked Radio Access

<details><summary>Respuesta</summary>

**Correcta: A) TErrestrial TRunked RAdio**

La denominación original fue *Trans European Trunked Radio*, coherente con un proyecto concebido para dotar a Europa de un sistema común de radio profesional. Cuando el estándar se difundió fuera de Europa —hoy está desplegado en más de 124 países— el adjetivo «transeuropeo» perdió sentido y el ETSI pasó a expandir el acrónimo como *TErrestrial TRunked RAdio*. El adjetivo «terrestre» tiene además valor descriptivo: distingue estos sistemas de los móviles por satélite.

*Referencia: §1.3 [TCCA-GLOBAL]*

</details>

---

### Pregunta 2

**¿Qué organismo normaliza TETRA?**

A) La APCO estadounidense
B) El ETSI, Instituto Europeo de Normas de Telecomunicaciones
C) La Unión Internacional de Telecomunicaciones (UIT)

<details><summary>Respuesta</summary>

**Correcta: B) El ETSI, Instituto Europeo de Normas de Telecomunicaciones**

TETRA es un estándar abierto del ETSI, con las series EN 300 392 (modo troncalizado), EN 300 396 (modo directo), EN 300 394 (conformidad) y EN 300 395 (códec de voz). La APCO es el organismo que normaliza P25 en Estados Unidos, y la UIT reparte el espectro entre servicios y regiones pero no elabora este estándar.

*Referencia: §1.3 [EN392-1]*

</details>

---

### Pregunta 3

**En la evolución de la radio móvil privada, ¿a qué generación pertenece TETRA?**

A) A la primera: la radio analógica convencional
B) A la segunda: el trunking analógico
C) A la tercera: el trunking digital

<details><summary>Respuesta</summary>

**Correcta: C) A la tercera: el trunking digital**

La secuencia es: analógica convencional (canal fijo por colectivo) → trunking analógico (MPT-1327) → trunking digital (TETRA, TETRAPOL, P25 y DMR) → banda ancha crítica (MCPTT del 3GPP). Una pregunta habitual pide identificar el sistema analógico de la segunda etapa, que es MPT-1327, no TETRA.

*Referencia: §1.1 [UIT-M2014]*

</details>

---

### Pregunta 4

**¿Qué significa que un sistema de radio sea troncalizado?**

A) Que cada colectivo de usuarios tiene asignada una frecuencia fija en exclusiva
B) Que la voz se transmite de forma analógica sobre un enlace troncal de alta capacidad
C) Que los canales forman una bolsa común que el sistema asigna dinámicamente bajo demanda

<details><summary>Respuesta</summary>

**Correcta: C) Que los canales forman una bolsa común que el sistema asigna dinámicamente bajo demanda**

La asignación la dirige un canal de control dedicado, que recibe la petición, comprueba la identidad y el grupo del solicitante y le asigna un canal de tráfico solo mientras dura la transmisión. La opción A describe precisamente el sistema convencional, que es lo contrario. El CNAF lo denomina «sistemas multicanales de acceso aleatorio de frecuencias con concentración de enlaces».

*Referencia: §1.2 [CNAF]*

</details>

---

### Pregunta 5

**¿Qué diferencia esencial existe entre PMR y PAMR?**

A) La PAMR es la misma tecnología explotada por un operador comercial que vende el servicio a terceros
B) La PAMR usa exclusivamente tecnología analógica y la PMR, digital
C) La PAMR opera en VHF y la PMR, en UHF

<details><summary>Respuesta</summary>

**Correcta: A) La PAMR es la misma tecnología explotada por un operador comercial que vende el servicio a terceros**

La distinción es jurídica y de modelo de explotación, no técnica, y tiene consecuencias directas en el título habilitante necesario para usar el espectro. El CNAF español las trata conjuntamente como «sistemas móviles digitales de banda estrecha PMR/PAMR».

*Referencia: §1.1 [CNAF]*

</details>

---

### Pregunta 6

**En una estación base TETRA con cuatro portadoras y un intervalo dedicado al canal de control, ¿cuántos canales de tráfico simultáneos hay?**

A) 4
B) 15
C) 16

<details><summary>Respuesta</summary>

**Correcta: B) 15**

Cuatro portadoras por cuatro intervalos de tiempo dan 16 canales físicos; descontando el intervalo dedicado al canal de control principal quedan 15 canales de tráfico simultáneos, repartidos dinámicamente entre todos los grupos. La opción C olvida restar el canal de control y la opción A corresponde a un despliegue convencional de cuatro canales rígidos.

*Referencia: §1.2 [EN392-2]*

</details>

---

### Pregunta 7

**¿Cuál de las siguientes NO es una ventaja del trunking frente a la radio convencional?**

A) La posibilidad de crear y disolver grupos desde el centro de control sin tocar los terminales
B) La independencia respecto de la infraestructura, que le permite funcionar aunque caiga el canal de control
C) La eficiencia espectral, al servir a más usuarios con el mismo número de frecuencias

<details><summary>Respuesta</summary>

**Correcta: B) La independencia respecto de la infraestructura, que le permite funcionar aunque caiga el canal de control**

Es justamente lo contrario: el trunking introduce dependencia de la infraestructura, porque sin canal de control no hay asignación dinámica. Por eso los sistemas troncalizados serios incorporan modos degradados, como el repliegue local de la estación base y el modo directo entre terminales.

*Referencia: §1.2 [EN392-2]*

</details>

---

### Pregunta 8

**¿Qué norma del ETSI hace verificable la interoperabilidad entre equipos TETRA de fabricantes distintos?**

A) La EN 300 392-7, de seguridad
B) La EN 300 395, del códec de voz
C) La EN 300 394, de pruebas de conformidad

<details><summary>Respuesta</summary>

**Correcta: C) La EN 300 394, de pruebas de conformidad**

Un estándar abierto define interfaces, pero la promesa de interoperabilidad solo se hace real si existe una forma normalizada de comprobar que un equipo cumple la norma. Esa es la función de la EN 300 394, complementada por las pruebas de interoperabilidad que organiza la industria.

*Referencia: §1.3 [EN394]*

</details>

---

### Pregunta 9

**¿Cuál de estos rasgos distingue a la radiocomunicación móvil privada de la telefonía celular pública?**

A) El establecimiento de llamada de grupo en menos de 300 milisegundos
B) El uso de modulaciones digitales de fase
C) La existencia de un identificador único de abonado

<details><summary>Respuesta</summary>

**Correcta: A) El establecimiento de llamada de grupo en menos de 300 milisegundos**

Las modulaciones digitales de fase y los identificadores de abonado existen también en la telefonía celular, de modo que no distinguen nada. Lo propio de la PMR es la combinación de comunicación de grupo, inmediatez por debajo de 300 ms, prioridad garantizada por el titular de la red, funcionamiento sin infraestructura y control de la disponibilidad.

*Referencia: §1.1 [ETR300-1]*

</details>

---

### Pregunta 10

**¿Qué designa la sigla SwMI en el estándar TETRA?**

A) Toda la infraestructura fija de conmutación y gestión de la red
B) El módulo de identidad de abonado que se inserta en el terminal
C) El protocolo de señalización entre la estación base y el terminal

<details><summary>Respuesta</summary>

**Correcta: A) Toda la infraestructura fija de conmutación y gestión de la red**

SwMI es *Switching and Management Infrastructure*. Desde el punto de vista del terminal, la SwMI «es la red»: incluye las estaciones base, los nodos de conmutación, las bases de datos de abonados y grupos, el centro de autenticación y la gestión. El módulo de identidad se normaliza en la EN 300 812.

*Referencia: §2.1 [EN392-1]*

</details>

---

### Pregunta 11

**¿Dónde se aplica y dónde se deshace el cifrado de interfaz aire de TETRA?**

A) Entre los dos terminales que participan en la comunicación
B) Entre el terminal y el nodo de conmutación de la red
C) Entre el terminal y la estación base, que es donde se descifra

<details><summary>Respuesta</summary>

**Correcta: C) Entre el terminal y la estación base, que es donde se descifra**

Por eso el cifrado de interfaz aire protege frente a quien escucha el aire, pero no frente al operador de la red ni frente a un compromiso de la infraestructura. La opción A describe el cifrado extremo a extremo, que es una capa distinta y complementaria.

*Referencia: §2.1.1 · §4.3.2 [TTR001-11]*

</details>

---

### Pregunta 12

**¿Qué es el canal de control principal (MCCH) de una célula TETRA?**

A) El canal por el que circula el tráfico de voz de mayor prioridad
B) El canal permanentemente activo por el que se difunde la información del sistema y se piden recursos
C) El enlace de transporte entre la estación base y el nodo de conmutación

<details><summary>Respuesta</summary>

**Correcta: B) El canal permanentemente activo por el que se difunde la información del sistema y se piden recursos**

Se transmite en el intervalo 1 de la portadora principal de la célula. Un terminal recién encendido lo busca para sincronizarse. Sin canal de control no hay troncalización, y de ahí la necesidad de modos degradados como el repliegue local y el modo directo.

*Referencia: §2.1.1 [EN392-2]*

</details>

---

### Pregunta 13

**En una llamada de grupo, ¿en qué células ocupa canal de tráfico la red?**

A) En todas las células de la red, para garantizar que nadie se quede fuera
B) Solo en aquellas donde hay miembros del grupo afiliados
C) Solo en la célula donde se encuentra quien transmite

<details><summary>Respuesta</summary>

**Correcta: B) Solo en aquellas donde hay miembros del grupo afiliados**

Es la razón por la que un sistema TETRA soporta cientos de grupos con pocas portadoras. La opción C impediría que los miembros situados en otras células oyeran la comunicación, y la opción A desperdiciaría capacidad en toda la red.

*Referencia: §2.1.2 [EN392-1]*

</details>

---

### Pregunta 14

**¿Cuál de estas funciones corresponde a la capa de gestión y despacho de una red TETRA?**

A) La asignación dinámica de grupos (DGNA) y la inhabilitación remota de terminales
B) La modulación π/4-DQPSK y la codificación de canal
C) El encaminamiento del audio de una llamada hacia las células con afiliados

<details><summary>Respuesta</summary>

**Correcta: A) La asignación dinámica de grupos (DGNA) y la inhabilitación remota de terminales**

La modulación y la codificación de canal pertenecen a la capa de radio, y el encaminamiento del audio, a la capa de conmutación. La capa de gestión es la que soporta el trabajo de las personas: gestión de abonados y grupos, consolas de despacho, grabación, supervisión de la red y gestión de claves.

*Referencia: §2.1.3 [EN392-1]*

</details>

---

### Pregunta 15

**¿Cuáles son las clases de potencia normalizadas del terminal TETRA?**

A) 50 W, 25 W, 5 W y 0,5 W
B) 20 W, 5 W, 2 W y 0,5 W
C) 30 W, 10 W, 3 W y 1 W

<details><summary>Respuesta</summary>

**Correcta: C) 30 W, 10 W, 3 W y 1 W**

Corresponden a las clases 1, 2, 3 y 4 respectivamente, y existen clases adicionales de menor potencia. En la práctica los portátiles son de 1 y 3 W y los equipos embarcados, de 3 y 10 W. Esa diferencia explica que en el borde de la cobertura llegue el vehículo y no el agente a pie.

*Referencia: §2.2.1 [EN392-2]*

</details>

---

### Pregunta 16

**En el esquema de identidades de TETRA, ¿cómo se compone la ITSI?**

A) Por el MCC más el MNC exclusivamente
B) Por la GSSI más el alias del usuario
C) Por la MNI más la ISSI, donde la MNI es a su vez el MCC más el MNC

<details><summary>Respuesta</summary>

**Correcta: C) Por la MNI más la ISSI, donde la MNI es a su vez el MCC más el MNC**

La ITSI es la identidad individual completa del abonado. La ISSI es su parte corta, la que lo identifica dentro de su red. La identidad de grupo es la GTSI, con la GSSI como parte corta. La ESI es la identidad corta cifrada en el aire.

*Referencia: §2.2.1 [EN392-7]*

</details>

---

### Pregunta 17

**¿Qué caracteriza al modo directo (DMO) de TETRA?**

A) Que los terminales se comunican a través de una única estación base, sin pasar por el nodo de conmutación
B) Que los terminales se comunican entre sí sin ninguna infraestructura de red
C) Que la red asigna un canal permanente a un grupo para toda la duración del incidente

<details><summary>Respuesta</summary>

**Correcta: B) Que los terminales se comunican entre sí sin ninguna infraestructura de red**

Está normalizado en la serie EN 300 396, distinta de la EN 300 392 del modo troncalizado. La opción A describe el repliegue local de una estación base aislada, que sigue siendo modo troncalizado. La capacidad de funcionar sin infraestructura es una de las razones por las que un servicio de emergencia no puede sustituir su radio por telefonía móvil.

*Referencia: §2.2.2 [EN396]*

</details>

---

### Pregunta 18

**Una dotación trabaja en modo directo en un sótano sin cobertura y el centro de mando necesita oírla y hablar con ella. ¿Qué elemento hay que desplegar?**

A) Un DM-GATE, es decir, una pasarela hacia la red troncalizada
B) Un DM-REP de tipo 2, para soportar dos llamadas simultáneas
C) Una estación base adicional en repliegue local

<details><summary>Respuesta</summary>

**Correcta: A) Un DM-GATE, es decir, una pasarela hacia la red troncalizada**

El DM-REP solo amplía el alcance dentro del modo directo: la dotación se oiría mejor entre sí, pero el centro de mando seguiría sin enterarse de nada. Es la pasarela la que reinyecta la comunicación en la red y devuelve la visibilidad al despacho. El equipo DM-REP/GATE combina ambas funciones.

*Referencia: §2.2.3 [EN396]*

</details>

---

### Pregunta 19

**¿Qué tipos de repetidor de modo directo distingue la norma EN 300 396?**

A) Tipo 1A sobre una portadora, tipo 1B sobre un par de portadoras dúplex y tipo 2 con dos llamadas
B) Tipo A analógico, tipo B digital y tipo C híbrido
C) Tipo simplex, tipo semidúplex y tipo dúplex completo

<details><summary>Respuesta</summary>

**Correcta: A) Tipo 1A sobre una portadora, tipo 1B sobre un par de portadoras dúplex y tipo 2 con dos llamadas**

El repetidor de tipo 1 soporta una sola llamada en el interfaz aire, y se subdivide en 1A y 1B según trabaje sobre una portadora o sobre un par separado en dúplex. El de tipo 2 soporta dos llamadas simultáneas.

*Referencia: §2.2.3 [EN396]*

</details>

---

### Pregunta 20

**¿Qué interfaz del modelo de referencia de TETRA es la ISI?**

A) La I1
B) La I3
C) La I6

<details><summary>Respuesta</summary>

**Correcta: B) La I3**

El modelo define seis puntos de referencia: I1 interfaz aire en modo troncalizado, I2 interfaz de línea, I3 interfaz entre sistemas o ISI, I4 interfaz de equipo periférico o PEI, I5 interfaz de gestión de red e I6 interfaz aire en modo directo. La I1 y la I6 son las dos interfaces aire, y están en normas distintas.

*Referencia: §2.3 [ETR300-1]*

</details>

---

### Pregunta 21

**¿Para qué sirve la interfaz PEI de TETRA?**

A) Para interconectar dos redes TETRA de titularidad distinta
B) Para conectar las consolas de despacho a la infraestructura por línea
C) Para conectar el terminal con un equipo de datos del usuario, como un ordenador embarcado

<details><summary>Respuesta</summary>

**Correcta: C) Para conectar el terminal con un equipo de datos del usuario, como un ordenador embarcado**

El PEI, *Peripheral Equipment Interface*, es la I4 del modelo de referencia y está normalizado en la EN 300 392-5. Se basa en un juego de comandos AT extendidos y es lo que convierte al terminal en un módem de datos. La opción A describe la ISI y la opción B, la interfaz de línea.

*Referencia: §2.3.3 [EN392-5]*

</details>

---

### Pregunta 22

**Dos administraciones distintas operan sendas redes TETRA en el mismo territorio y necesitan comunicarse. ¿Cuál es el mecanismo normalizado?**

A) La interfaz PEI de ambas redes
B) El modo directo con clave estática compartida
C) La interfaz entre sistemas (ISI), normalizada en la EN 300 392-3

<details><summary>Respuesta</summary>

**Correcta: C) La interfaz entre sistemas (ISI), normalizada en la EN 300 392-3**

La ISI permite llamadas individuales y de grupo entre abonados de redes distintas, itinerancia y transferencia de mensajes cortos. Conviene saber, además, que su implantación real ha sido desigual y que muchas interconexiones se han resuelto con pasarelas de audio o con acoplamiento de grupos en las consolas de despacho.

*Referencia: §2.3.2 [EN392-3]*

</details>

---

### Pregunta 23

**¿Qué esquema de acceso múltiple emplea TETRA?**

A) FDMA combinado con TDMA: portadoras de 25 kHz divididas en cuatro intervalos
B) CDMA con códigos ortogonales sobre una banda común
C) FDMA puro con canalización de 12,5 kHz

<details><summary>Respuesta</summary>

**Correcta: A) FDMA combinado con TDMA: portadoras de 25 kHz divididas en cuatro intervalos**

Primero se divide el espectro en portadoras, que es FDMA, y después cada portadora en cuatro intervalos de tiempo, que es TDMA. La opción C describe TETRAPOL, que es de acceso FDMA con canalización de 12,5 kHz. TETRA no emplea CDMA.

*Referencia: §3.2 [EN392-2]*

</details>

---

### Pregunta 24

**¿Cuál es la eficiencia espectral de TETRA expresada en anchura de banda por canal de voz?**

A) 12,5 kHz por canal
B) 6,25 kHz por canal
C) 25 kHz por canal

<details><summary>Respuesta</summary>

**Correcta: B) 6,25 kHz por canal**

Resulta de dividir los 25 kHz de la portadora entre los cuatro canales que sostiene: 25 dividido entre 4 son 6,25 kHz por canal de voz. TETRAPOL, con FDMA y 12,5 kHz por canal, obtiene la mitad de eficiencia; los 25 kHz de la opción C son el ancho de la portadora completa, no el de un canal.

*Referencia: §3.2 [UIT-M2014]*

</details>

---

### Pregunta 25

**¿Cuál es el radio máximo de célula en TETRA Release 1 y a qué se debe?**

A) 35 km, por la potencia máxima permitida al terminal
B) 58 km, por la estructura temporal de los intervalos TDMA
C) 120 km, por el límite de propagación en la banda de 400 MHz

<details><summary>Respuesta</summary>

**Correcta: B) 58 km, por la estructura temporal de los intervalos TDMA**

La limitación no es de potencia sino de tiempo: si el terminal está demasiado lejos, su ráfaga llega tan retrasada que invadiría el intervalo siguiente. TETRA Release 2 incorporó mejoras de alcance para superar ese límite en despliegues rurales, marítimos y militares.

*Referencia: §3.2 [EN392-2]*

</details>

---

### Pregunta 26

**¿Cuántos bits transporta cada símbolo en la modulación π/4-DQPSK de TETRA?**

A) 1 bit
B) 4 bits
C) 2 bits

<details><summary>Respuesta</summary>

**Correcta: C) 2 bits**

La letra Q corresponde a *quaternary*: cuatro estados de fase posibles, y como 2 elevado a 2 son 4, cada símbolo transporta 2 bits. Con una tasa de 18.000 símbolos por segundo se obtienen 36.000 bits por segundo brutos por portadora. La GMSK de TETRAPOL y de GSM transporta 1 bit por símbolo.

*Referencia: §3.3 [EN392-2]*

</details>

---

### Pregunta 27

**¿Qué consigue el desplazamiento de π/4 en la modulación de TETRA?**

A) Que las transiciones entre símbolos no pasen por el origen, evitando que la envolvente caiga a cero
B) Que la tasa de símbolo se duplique respecto a una QPSK convencional
C) Que el receptor pueda prescindir de la corrección de errores

<details><summary>Respuesta</summary>

**Correcta: A) Que las transiciones entre símbolos no pasen por el origen, evitando que la envolvente caiga a cero**

Una señal con variaciones muy bruscas de amplitud obliga a usar amplificadores muy lineales, caros e ineficientes en consumo. Al evitar el paso por el origen se mantiene una relación pico-media moderada, lo que en un terminal alimentado por batería se traduce directamente en más autonomía.

*Referencia: §3.3 [EN392-2]*

</details>

---

### Pregunta 28

**¿Cuál es la tasa binaria bruta de una portadora TETRA?**

A) 36 kbit/s
B) 28,8 kbit/s
C) 9,6 kbit/s

<details><summary>Respuesta</summary>

**Correcta: A) 36 kbit/s**

Resulta de multiplicar los 18.000 símbolos por segundo por los 2 bits que transporta cada símbolo. Repartidos entre los cuatro intervalos corresponden 9 kbit/s brutos a cada uno, de los que quedan 7,2 kbit/s netos para el usuario tras descontar sincronización, cabeceras y protección de errores. Los 28,8 kbit/s de la opción B son el resultado de agregar los cuatro intervalos netos.

*Referencia: §3.3 [EN392-2]*

</details>

---

### Pregunta 29

**¿Qué códec de voz emplea TETRA y con qué tasa neta?**

A) AMR a 12,2 kbit/s
B) CELP a 8 kbit/s
C) ACELP a 4,567 kbit/s

<details><summary>Respuesta</summary>

**Correcta: C) ACELP a 4,567 kbit/s**

El códec produce 137 bits por cada trama de voz de 30 milisegundos, lo que da 4.567 bits por segundo. A esos bits se les añade codificación de canal hasta ocupar los 7,2 kbit/s del intervalo: casi el 37 % del caudal se dedica a corregir errores, y es lo que mantiene la voz inteligible en el borde de la cobertura.

*Referencia: §3.3 [EN395]*

</details>

---

### Pregunta 30

**¿Cuánto dura un intervalo de tiempo en el interfaz aire de TETRA?**

A) 4,615 ms
B) 14,167 ms
C) 56,67 ms

<details><summary>Respuesta</summary>

**Correcta: B) 14,167 ms**

Cuatro intervalos forman una trama de 56,67 ms, que es el valor de la opción C. Dieciocho tramas forman una multitrama de 1,02 s y sesenta multitramas, una hipertrama de 61,2 s. Los 4,615 ms de la opción A corresponden a la trama de GSM.

*Referencia: §3.4 [EN392-2]*

</details>
---

### Pregunta 31

**¿Qué trama de cada multitrama TETRA se reserva a señalización?**

A) La primera
B) La decimoctava
C) La novena

<details><summary>Respuesta</summary>

**Correcta: B) La decimoctava**

La multitrama tiene 18 tramas y la número 18 es la trama de control. Eso permite que la red envíe información a un terminal mientras está en conversación, sin interrumpirla, y hace posible la función de entrada tardía. El usuario dispone, por tanto, de 17 de cada 18 tramas para su tráfico.

*Referencia: §3.4 [EN392-2]*

</details>

---

### Pregunta 32

**¿Cuánto dura una hipertrama y qué relevancia tiene?**

A) 61,2 segundos, y su número interviene en la generación del flujo de clave del cifrado de interfaz aire
B) 1,02 segundos, y delimita el ciclo de asignación de canales de tráfico
C) 30 segundos, y marca el periodo de renovación de la clave derivada

<details><summary>Respuesta</summary>

**Correcta: A) 61,2 segundos, y su número interviene en la generación del flujo de clave del cifrado de interfaz aire**

La hipertrama son 60 multitramas de 1,02 segundos. El valor de la opción B es precisamente la duración de una multitrama. Ese papel del tiempo en la generación del flujo de clave es lo que la vulnerabilidad CVE-2022-24401 convirtió en problema, al difundirse el tiempo de red sin autenticar.

*Referencia: §3.4 [TETRABURST]*

</details>

---

### Pregunta 33

**¿Qué diferencia hay entre la ráfaga descendente y la ascendente en TETRA?**

A) La ascendente lleva más bits útiles que la descendente
B) La ascendente es continua y la descendente, discontinua
C) La descendente es continua y da referencia de sincronismo; la ascendente es discontinua

<details><summary>Respuesta</summary>

**Correcta: C) La descendente es continua y da referencia de sincronismo; la ascendente es discontinua**

La estación base transmite sin interrupción, lo que da a los terminales una referencia permanente de temporización, mientras que cada terminal solo transmite en su intervalo. Además, la ráfaga descendente normal lleva 432 bits útiles y la ascendente, 336, de modo que la opción A también es falsa.

*Referencia: §3.4 [EN392-2]*

</details>

---

### Pregunta 34

**¿Qué distingue a una llamada de difusión de una llamada de grupo en TETRA?**

A) Que la de difusión llega a más usuarios que la de grupo
B) Que la de difusión ocupa cuatro intervalos y la de grupo, solo uno
C) Que la de difusión es unidireccional: los receptores solo escuchan y no pueden responder

<details><summary>Respuesta</summary>

**Correcta: C) Que la de difusión es unidireccional: los receptores solo escuchan y no pueden responder**

En una llamada de grupo cualquiera de los participantes puede tomar la palabra apretando el botón; en una llamada de difusión, no. El número de destinatarios no es lo que las diferencia, y ninguna de las dos ocupa cuatro intervalos por sí misma.

*Referencia: §4.1.1 [EN392-9]*

</details>

---

### Pregunta 35

**¿Qué es la función DGNA en una red TETRA?**

A) Un algoritmo de derivación de claves de grupo a partir de la clave común
B) La asignación dinámica de grupos, que permite crear y cargar grupos en los terminales por el aire
C) Un mecanismo de reparto geográfico de las portadoras entre células vecinas

<details><summary>Respuesta</summary>

**Correcta: B) La asignación dinámica de grupos, que permite crear y cargar grupos en los terminales por el aire**

*Dynamic Group Number Assignment* permite montar en segundos un grupo mixto para una emergencia concreta —policía, bomberos y sanitarios de un mismo incidente— y disolverlo al terminar, todo desde una consola. En radio convencional habría que reprogramar físicamente cada equipo.

*Referencia: §4.1.1 [EN392-9]*

</details>

---

### Pregunta 36

**¿En qué consiste la prioridad con desalojo?**

A) En que una llamada de prioridad suficiente corta una comunicación en curso de prioridad inferior cuando no hay canal libre
B) En que las llamadas de mayor prioridad se sitúan al principio de la cola de espera
C) En que el centro de mando puede expulsar a un terminal de la red de forma permanente

<details><summary>Respuesta</summary>

**Correcta: A) En que una llamada de prioridad suficiente corta una comunicación en curso de prioridad inferior cuando no hay canal libre**

La opción B describe el escalón anterior, la prioridad de acceso, que ordena la cola pero no interrumpe a nadie. La opción C describe la inhabilitación remota. La diferencia entre los dos primeros escalones es la que hay entre esperar mejor y echar a otro.

*Referencia: §4.1.2 [EN392-9]*

</details>

---

### Pregunta 37

**¿Cuál es la longitud máxima de datos de usuario de un SDS de tipo 4?**

A) 2.047 bits
B) 64 bits
C) 160 caracteres

<details><summary>Respuesta</summary>

**Correcta: A) 2.047 bits**

Los tipos 1, 2 y 3 admiten 16, 32 y 64 bits respectivamente, y el mensaje de estado, 16 bits precodificados. El tipo 4 es el que se usa en la práctica para texto libre, posiciones y aplicaciones, y sobre él se define el SDS-TL, que añade identificación del protocolo de aplicación, acuse de recibo y encadenamiento.

*Referencia: §4.2.1 [EN392-2]*

</details>

---

### Pregunta 38

**Los mensajes SDS de una red TETRA viajan por los canales de control. ¿Qué consecuencia tiene esto para el dimensionado?**

A) Ninguna: al no ocupar canal de tráfico, el envío de posiciones es gratuito para la red
B) Consumen capacidad de señalización, que es finita y compartida con el establecimiento de llamadas
C) Obligan a reservar una portadora adicional por cada mil terminales

<details><summary>Respuesta</summary>

**Correcta: B) Consumen capacidad de señalización, que es finita y compartida con el establecimiento de llamadas**

Es el error de diseño más común en despliegues de localización sobre TETRA. Las contramedidas habituales son espaciar el envío cuando el vehículo está parado, emitir por distancia recorrida en lugar de por tiempo, distribuir los envíos para que no coincidan y reservar capacidad de señalización para el establecimiento de llamada, que siempre tiene prioridad.

*Referencia: §4.2.1 [EN392-2]*

</details>

---

### Pregunta 39

**¿Cuál es el caudal máximo de datos de TETRA Release 1 agregando los cuatro intervalos y sin protección de errores?**

A) 7,2 kbit/s
B) 14,4 kbit/s
C) 28,8 kbit/s

<details><summary>Respuesta</summary>

**Correcta: C) 28,8 kbit/s**

Cada intervalo aporta 7,2 kbit/s sin protección, 4,8 con protección baja y 2,4 con protección alta. Ese techo permite texto, posiciones, telemetría y consultas breves, pero no vídeo ni cartografía en tiempo real, y es exactamente la razón de ser de TEDS.

*Referencia: §4.2.2 [EN392-2]*

</details>

---

### Pregunta 40

**¿Qué protocolo permite a TETRA transportar tráfico IP en el servicio de datos por paquetes?**

A) CMCE
B) SDS-TL
C) SNDCP

<details><summary>Respuesta</summary>

**Correcta: C) SNDCP**

El *Subnetwork Dependent Convergence Protocol* pertenece a la capa 3 del interfaz aire y hace que, desde el punto de vista de la aplicación, el terminal sea un dispositivo IP más. El SDS-TL es la capa de transporte de la mensajería corta, y el CMCE es la entidad de control de llamada en modo circuito.

*Referencia: §4.2.2 [EN392-2]*

</details>

---

### Pregunta 41

**¿Qué característica define a la clave de autenticación K de TETRA?**

A) Que es compartida por el terminal y la red y nunca se transmite por el aire
B) Que se genera en cada registro y se distribuye cifrada mediante OTAR
C) Que es común a todos los terminales de un mismo grupo de conversación

<details><summary>Respuesta</summary>

**Correcta: A) Que es compartida por el terminal y la red y nunca se transmite por el aire**

La autenticación es de desafío-respuesta con clave simétrica: la red envía un número aleatorio, el terminal calcula la respuesta con K y la red compara. La opción B describe el comportamiento de la clave común CCK, y la opción C, el de la clave de grupo GCK.

*Referencia: §4.3.1 [EN392-7]*

</details>

---

### Pregunta 42

**¿De dónde procede la clave derivada DCK?**

A) De la carga previa en el terminal antes de su puesta en servicio
B) Del propio proceso de autenticación
C) De la combinación de la clave de grupo con la clave común

<details><summary>Respuesta</summary>

**Correcta: B) Del propio proceso de autenticación**

Autenticar y cifrar están encadenados: de la autenticación se deriva una clave de cifrado propia de ese terminal y esa sesión. Por eso una red que no autentica tiene que conformarse con claves estáticas precargadas, que son las mismas para todos y durante mucho tiempo. La opción C describe la MGCK.

*Referencia: §4.3.1 [TTR001-11]*

</details>

---

### Pregunta 43

**¿Qué defensa aporta la autenticación mutua en TETRA?**

A) Impide que se puedan reproducir mensajes cortos capturados previamente
B) Protege frente a una estación base falsa, porque el terminal verifica también a la red
C) Garantiza que el operador de la red no pueda escuchar las comunicaciones

<details><summary>Respuesta</summary>

**Correcta: B) Protege frente a una estación base falsa, porque el terminal verifica también a la red**

Sin autenticación de la red, un atacante puede montar una estación base falsa que atraiga a los terminales de la zona y desde ella degradar la seguridad, capturar tráfico o inyectar mensajes. Que el operador no pueda escuchar es cosa del cifrado extremo a extremo, no de la autenticación.

*Referencia: §4.3.1 [EN392-7]*

</details>

---

### Pregunta 44

**¿Qué caracteriza a la clase de seguridad SC3 del interfaz aire?**

A) Que no aplica cifrado, aunque puede cifrar las identidades mediante ESI
B) Que cifra con clave estática precargada y no exige autenticación
C) Que emplea clave derivada y clave común, y exige autenticación

<details><summary>Respuesta</summary>

**Correcta: C) Que emplea clave derivada y clave común, y exige autenticación**

La opción A describe SC1 y la opción B, SC2, que es además la clase propia del modo directo. SC3 es la configuración recomendada, y admite la variante SC3G cuando se añade cifrado propio por grupo con GCK y MGCK.

*Referencia: §4.3.2 [TTR001-11]*

</details>

---

### Pregunta 45

**¿Qué reveló la vulnerabilidad CVE-2022-24402, divulgada en 2023?**

A) Que la clave de 80 bits del algoritmo TEA1 se reduce deliberadamente a unos 32 bits efectivos
B) Que el algoritmo TEA2 puede descifrarse observando el tiempo de red
C) Que el cifrado extremo a extremo carece de protección antirrepetición

<details><summary>Respuesta</summary>

**Correcta: A) Que la clave de 80 bits del algoritmo TEA1 se reduce deliberadamente a unos 32 bits efectivos**

Esa reducción permite romper la clave por fuerza bruta en minutos con un ordenador doméstico. La TCCA ha confirmado que fue intencionada y la justifica en el cumplimiento del Acuerdo de Wassenaar de control de exportación. La opción B mezcla la CVE-2022-24401 con otro algoritmo, y la opción C corresponde a la divulgación de 2025.

*Referencia: §4.3.2 [TETRABURST]*

</details>

---

### Pregunta 46

**¿A qué algoritmos sustituyen respectivamente TEA5, TEA6 y TEA7 del conjunto TEA set B?**

A) A TEA2, TEA3 y TEA1
B) A TEA1, TEA2 y TEA3
C) A TEA3, TEA4 y TEA2

<details><summary>Respuesta</summary>

**Correcta: A) A TEA2, TEA3 y TEA1**

TEA5 sucede a TEA2 para las redes de emergencia europeas, TEA6 sucede a TEA3 para redes militares y de emergencia extraeuropeas afines, y TEA7 sucede a TEA1 como el único del nuevo conjunto disponible para infraestructuras críticas y uso civil general. El conjunto se liberó en octubre de 2022.

*Referencia: §4.3.2 [TCCA-B]*

</details>

---

### Pregunta 47

**Según la TCCA, ¿qué longitud de clave tienen TEA5 y TEA6, y qué ocurre con TEA7?**

A) Los tres tienen 80 bits, igual que el conjunto anterior
B) Los tres tienen 256 bits, sin ninguna restricción
C) TEA5 y TEA6 tienen 192 bits, y TEA7 conserva una reducción efectiva a 56 bits

<details><summary>Respuesta</summary>

**Correcta: C) TEA5 y TEA6 tienen 192 bits, y TEA7 conserva una reducción efectiva a 56 bits**

La reducción de TEA7 responde a las mismas razones de control de exportación que en su día afectaron a TEA1. La lección de fondo, muy citable, es que la debilidad de TEA1 no fue un error de diseño sino una decisión de política de exportación, y que el algoritmo civil del nuevo conjunto sigue arrastrando esa condición.

*Referencia: §4.3.2 [TCCA-RD]*

</details>

---

### Pregunta 48

**Una red TETRA mantiene TEA1 activo «por compatibilidad» junto a algoritmos más fuertes. ¿Qué problema plantea, según la divulgación de 2025?**

A) Ninguno, siempre que los usuarios sensibles tengan configurado un algoritmo distinto
B) Que soportar TEA1 junto a otros algoritmos permite recuperar también la clave de los demás
C) Que obliga a reducir el número de grupos de conversación de la red

<details><summary>Respuesta</summary>

**Correcta: B) Que soportar TEA1 junto a otros algoritmos permite recuperar también la clave de los demás**

Es la CVE-2025-52943 de 2TETRA:2BURST, presentada en Black Hat USA el 7 de agosto de 2025. Su consecuencia práctica es directa: no basta con dejar de usar TEA1, hay que dejar de soportarlo, y en un pliego eso se traduce en prohibirlo expresamente y no en desaconsejarlo.

*Referencia: §4.3.2 [2TETRA]*

</details>

---

### Pregunta 49

**¿Sobre qué tecnología está construida la red SIRDEE del Estado español?**

A) Sobre TETRA, en la banda de 380 a 400 MHz
B) Sobre TETRAPOL, de acceso FDMA y canalización de 12,5 kHz
C) Sobre DMR, en la banda de 410 a 430 MHz

<details><summary>Respuesta</summary>

**Correcta: B) Sobre TETRAPOL, de acceso FDMA y canalización de 12,5 kHz**

Es la confusión más penalizada del tema. El SIRDEE, en servicio desde el año 2000, se decidió cuando TETRA aún no estaba maduro comercialmente. Las redes autonómicas y municipales, decididas más tarde, sí son en su mayoría TETRA, lo que impide resolver la interoperabilidad entre niveles mediante la ISI.

*Referencia: §5.1 [SIRDEE]*

</details>

---

### Pregunta 50

**¿Qué reserva la nota UN-28 del CNAF en las subbandas 380-385 y 390-395 MHz?**

A) Redes de servicios de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y redes de servicios de emergencia
B) Sistemas digitales de acceso aleatorio de canales para uso civil y profesional
C) Servicios de banda ancha para protección pública y socorro en catástrofes

<details><summary>Respuesta</summary>

**Correcta: A) Redes de servicios de seguridad de las Fuerzas y Cuerpos de Seguridad del Estado y redes de servicios de emergencia**

Son la excepción a la reserva de la banda 235-399,9 MHz para uso exclusivo del Estado en sistemas del Ministerio de Defensa, y se establecen de conformidad con la Decisión CEPT ECC/DEC(08)05. La opción B corresponde a la nota UN-31, y la opción C, a los bloques de 452-457,5 y 462-467,5 MHz.

*Referencia: §3.1 · §5.2 [CNAF]*

</details>

---

### Pregunta 51

**¿Qué subbandas destina el CNAF a «sistemas digitales de acceso aleatorio de canales (TETRA y otros)» y con qué canalización?**

A) 380-385 y 390-395 MHz, con canalización de 12,5 kHz
B) 450-470 MHz, con canalización de 6,25 kHz
C) 410-415,3 y 420-425,3 MHz, con canalización de 25 kHz

<details><summary>Respuesta</summary>

**Correcta: C) 410-415,3 y 420-425,3 MHz, con canalización de 25 kHz**

Es la nota UN-31, dentro de la subbanda 410-430 MHz reservada a banda estrecha en modalidad dúplex con separación de 10 MHz entre transmisión y recepción. Es la única mención expresa de TETRA en el CNAF español, y por eso es un dato de examen de primer orden.

*Referencia: §3.1 [CNAF]*

</details>

---

### Pregunta 52

**¿Cuál es el Cuadro Nacional de Atribución de Frecuencias vigente en España?**

A) La Orden ETU/1033/2017, de 25 de octubre
B) La Orden ETD/1449/2021, de 16 de diciembre
C) La Orden TDF/732/2026, de 10 de julio

<details><summary>Respuesta</summary>

**Correcta: C) La Orden TDF/732/2026, de 10 de julio**

Se publicó en el BOE núm. 173, de 17 de julio de 2026, y deroga la Orden ETD/1449/2021 con efectos de 18 de julio de 2026. Su motivo declarado es incorporar las previsiones de la Conferencia Mundial de Radiocomunicaciones de 2023, en vigor en su mayoría desde el 1 de enero de 2025. Quien estudie con material anterior al verano de 2026 citará una orden derogada.

*Referencia: §3.1 · §5.2 [CNAF]*

</details>

---

### Pregunta 53

**Según la Ley 11/2022, ¿qué naturaleza jurídica tiene el espectro radioeléctrico?**

A) Es un bien patrimonial del Estado, susceptible de enajenación
B) Es un bien de dominio público, cuya titularidad y administración corresponden al Estado
C) Es un recurso de titularidad compartida entre el Estado y las comunidades autónomas

<details><summary>Respuesta</summary>

**Correcta: B) Es un bien de dominio público, cuya titularidad y administración corresponden al Estado**

Lo establece el artículo 85.1 de la Ley 11/2022, General de Telecomunicaciones. De ahí se deduce que nadie es propietario de una frecuencia, que su uso requiere título habilitante estatal y que ese título está sujeto a condiciones, tiene plazo y puede modificarse o revocarse.

*Referencia: §5.2 [LGTel]*

</details>

---

### Pregunta 54

**Un ayuntamiento explota una red TETRA propia para sus servicios de emergencia. ¿Qué título habilitante ampara su uso del espectro?**

A) Una afectación demanial, conforme al artículo 88.5.b) de la Ley 11/2022
B) Una autorización individual de uso privativo para autoprestación
C) Una concesión administrativa, previa inscripción como operador de comunicaciones electrónicas

<details><summary>Respuesta</summary>

**Correcta: A) Una afectación demanial, conforme al artículo 88.5.b) de la Ley 11/2022**

El precepto otorga el uso privativo para autoprestación mediante autorización individual «salvo en el caso de Administraciones públicas, que requerirán de afectación demanial». La concesión de la opción C exigiría además ostentar la condición de operador de comunicaciones electrónicas, según el artículo 88.6, que no es el caso de un ayuntamiento que se autopresta el servicio.

*Referencia: §5.2 [LGTel]*

</details>

---

### Pregunta 55

**¿Cuál es la duración general de los derechos de uso privativo del dominio público radioeléctrico sin limitación de número?**

A) Hasta el 31 de diciembre del año natural en que cumplan su quinto año de vigencia, renovables por periodos de cinco años
B) Veinte años, prorrogables una sola vez
C) Diez años improrrogables

<details><summary>Respuesta</summary>

**Correcta: A) Hasta el 31 de diciembre del año natural en que cumplan su quinto año de vigencia, renovables por periodos de cinco años**

Lo fija el artículo 94.1 de la Ley 11/2022. La duración mínima de veinte años de la opción B corresponde a los derechos de uso privativo con limitación de número, que son los que se otorgan por licitación, como los de la telefonía móvil.

*Referencia: §5.2 [LGTel]*

</details>

---

### Pregunta 56

**Según el artículo 4.1 de la Ley 11/2022, ¿qué servicios de telecomunicaciones tienen la consideración de servicio público?**

A) Todos los servicios disponibles al público, por su condición de servicios de interés general
B) Solo los de seguridad nacional, defensa nacional, seguridad pública, seguridad vial y protección civil
C) Únicamente los incluidos en el servicio universal

<details><summary>Respuesta</summary>

**Correcta: B) Solo los de seguridad nacional, defensa nacional, seguridad pública, seguridad vial y protección civil**

El precepto dice literalmente que «sólo tienen la consideración de servicio público los servicios regulados en este artículo», y el artículo se titula precisamente así. Es la excepción a la regla general del artículo 2, que declara las telecomunicaciones servicios de interés general prestados en régimen de libre competencia.

*Referencia: §5.2 [LGTel]*

</details>

---

### Pregunta 57

**¿Qué exige la medida mp.com.4.2 del Esquema Nacional de Seguridad?**

A) Que todas las comunicaciones se cifren con algoritmos aprobados por el Centro Criptológico Nacional
B) Que se realicen pruebas periódicas del plan de continuidad del servicio
C) Que, si se emplean comunicaciones inalámbricas, sea en un segmento separado

<details><summary>Respuesta</summary>

**Correcta: C) Que, si se emplean comunicaciones inalámbricas, sea en un segmento separado**

Pertenece a la medida mp.com.4, «separación de flujos de información en la red», que no aplica en categoría BÁSICA y cuyos refuerzos son R1 con VLAN, R2 con VPN, R3 con medios físicos separados y R4 en los puntos de interconexión. Es el precepto que se cita cuando alguien propone conectar la red radio al segmento ofimático general.

*Referencia: §5.2 [ENS]*

</details>

---

### Pregunta 58

**¿Cuál de estos NO es un modo degradado propio de un sistema TETRA?**

A) El repliegue local de la estación base, que sigue troncalizando en su célula
B) El paso de la clase de seguridad SC3 a la SC2 al perder el enlace con el centro de autenticación
C) La conmutación automática de los terminales a la red de telefonía móvil comercial

<details><summary>Respuesta</summary>

**Correcta: C) La conmutación automática de los terminales a la red de telefonía móvil comercial**

No es un modo previsto por el estándar: los terminales híbridos que combinan TETRA y banda ancha son una solución de producto, no un modo degradado normalizado. Los tres modos degradados propios son el repliegue local, el modo directo y el repliegue de clase de seguridad.

*Referencia: §5.3 [TTR001-11]*

</details>

---

### Pregunta 59

**¿Qué introduce TEDS respecto de TETRA Release 1?**

A) Anchos de canal de 25, 50, 100 y 150 kHz y modulaciones de orden superior con adaptación al enlace
B) La sustitución del acceso TDMA por acceso ortogonal por división de frecuencia
C) La incorporación del modo directo y de los repetidores de modo directo

<details><summary>Respuesta</summary>

**Correcta: A) Anchos de canal de 25, 50, 100 y 150 kHz y modulaciones de orden superior con adaptación al enlace**

Las modulaciones añadidas son π/8-D8PSK, 4-QAM, 16-QAM y 64-QAM, y el sistema elige entre ellas según la calidad de la señal, reservando el 4-QAM para el borde de la cobertura. TEDS es una mejora dentro de TETRA, no una tecnología distinta. El modo directo de la opción C existe desde la Release 1.

*Referencia: §5.4 [TR102580]*

</details>

---

### Pregunta 60

**¿En qué versión del 3GPP se normalizó el servicio MCPTT de voz de misión crítica?**

A) En la Release 8, junto con la introducción de LTE
B) En la Release 13, culminada en 2016
C) En la Release 17, junto con las primeras funciones de 5G avanzado

<details><summary>Respuesta</summary>

**Correcta: B) En la Release 13, culminada en 2016**

La especificación de requisitos es la TS 22.179. MCVideo y MCData llegaron en la Release 14. Los habilitadores previos del propio 3GPP fueron GCSE para las comunicaciones de grupo, eMBMS para la difusión eficiente y ProSe para la comunicación de proximidad, que aspira a replicar el modo directo de TETRA.

*Referencia: §5.4 [3GPP-MC]*

</details>
