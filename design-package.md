# AutoGarage — Paquete de diseño

Tier 1, un plano continuo. Escrito antes de generar. La copia de este documento
se monta literal en la web: la escritura pasa aquí, el cableado pasa en el build.
Los números de las bandas son puntos de partida, los valida el flick test.

## 1. La premisa de marca

Una palabra del mundo del cliente: **el expediente**.

AutoGarage no busca un coche, entrega un expediente cerrado: qué coche es, de dónde
viene, qué se ha verificado punto por punto, qué cuesta el coche y qué cuesta el
trabajo, por separado. Esa idea responde al miedo número uno del mercado (entre el
15% y el 25% de los coches de ocasión vendidos en España arrastran algún fraude) y a
las dos objeciones que frenan a cualquiera ante un servicio así: la comisión y el
"me sale más barato ir yo". Toda sección de la página sirve a esa idea o no aparece.

## 2. La paleta como tokens CSS

Sacada del mundo del plano: hormigón mojado de noche, azul petróleo, un solo faro frío.

```css
:root{
  --canvas:#0A131B;        /* azul petróleo profundo, nunca negro puro */
  --canvas-deep:#070E14;   /* fondo del entorno fijo */
  --panel:#101C25;         /* fichas y superficies elevadas */
  --panel-2:#16242F;       /* superficie elevada sobre panel */
  --line:#223341;          /* filete decorativo */
  --line-strong:#4C687D;   /* borde interactivo, 3.21:1 sobre canvas */
  --accent:#5CB8FF;        /* faro frío. CTA, foco, dos énfasis */
  --accent-hover:#86CCFF;
  --accent-muted:rgba(92,184,255,.14);
  --text-primary:#EEF4F8;  /* 16.8:1 sobre canvas */
  --text-secondary:#9DB2C0;/* 8.46:1 sobre canvas */
  --ink:#06131C;           /* texto sobre el acento, 8.7:1 */
}
```

## 3. El trío tipográfico

- **Display:** Archivo variable, eje de anchura 100 a 125, pesos 500 a 700. Tiene aire
  de placa y de hoja de especificaciones. No es Inter ni Roboto.
- **Texto:** Instrument Sans 400 y 500.
- **Mono:** JetBrains Mono 400 y 500, para referencias de expediente y etiquetas.

## 4. El mapa de bandas

Héroe de 600vh, recorrido de 500vh. Rampas f = min(0.02, (b-a)/3). Banda 1 sin
entrada suave de opacidad, banda 4 sin salida. Meseta resultante de unos 90vh.

| Banda | Rango | Momento del plano | Copia (literal) | Entrada |
|---|---|---|---|---|
| 1 | 0.00 a 0.22 | nave vacía, faros pequeños al fondo entre la niebla | "El coche que quieres ya existe." | approach-from-depth, la línea crece desde el fondo como los faros |
| 2 | 0.26 a 0.48 | el coche avanza, reflejos largos en el suelo mojado | "Está en algún sitio. Vamos a por él." | drift-down por palabras |
| 3 | 0.52 a 0.72 | el coche casi encima, luz lateral, haz cruzando | "Y no llega hasta que está verificado." | grid snap-align, los caracteres se alinean como una lista que se cuadra |
| 4 | 0.78 a 1.00 | el coche en reposo dentro del charco de luz | H1 + subtítulo + CTA (abajo) | word-by-word rise, tres llegadas escalonadas |

Banda 4, literal:

- H1: "Tú lo describes. Nosotros lo entregamos."
- Subtítulo: "Buscamos, verificamos y negociamos el coche exacto que nos pides. Llega a tu puerta con el expediente completo y el precio por escrito."
- CTA primario: "Abrir mi expediente" hacia #solicitud
- CTA secundario: "Ver cómo funciona" hacia #proceso

## 5. Bloque de copia del héroe estático

Para móvil y para movimiento reducido, compuesto sobre el fotograma final.

- Kicker mono: "Coches a la carta"
- H1: "Tú lo describes. Nosotros lo entregamos."
- Subtítulo: "Buscamos, verificamos y negociamos el coche exacto que nos pides. Llega a tu puerta con el expediente completo y el precio por escrito."
- CTA: "Abrir mi expediente"

## 6. El esquema de abajo

Cada sección empuja al único ancla de conversión, #solicitud. Ninguna sección vecina
repite esqueleto de maquetación.

### S1. Barra de datos (tira fina, mono, hechos de mercado citables)

- "1,8 M de coches de ocasión vendidos al año en España"
- "15% a 25% arrastran algún tipo de fraude"
- "30 € es lo que cuesta trucar un cuentakilómetros"

### S2. El problema (editorial a dos columnas con cifra grande)

- Kicker: "Por qué existimos"
- H2: "Buscar tú solo sale más caro de lo que parece."
- Cuerpo: "Semanas yendo de un concesionario a otro. El comercial que te mete prisa. El precio que nunca acaba de llegar por escrito. La entrega que se alarga y el teléfono que ya no coge nadie. Y por debajo de todo eso, un mercado donde trucar un cuentakilómetros cuesta 30 euros y un coche que marca 80.000 km puede valer entre 3.000 y 8.000 euros más que ese mismo coche con sus 180.000 reales."
- Cifra: "15–25 %" con pie "de los coches de ocasión que se venden en España arrastran algún tipo de fraude."

### S3. El proceso (#proceso, tres pasos, imagen generada en cada uno, línea de ruta que se dibuja)

- Kicker: "Cómo funciona"
- H2: "Tres pasos y una sola persona al otro lado."
- Paso 01 "El encargo": "Nos cuentas el coche: modelo, motor, color, extras, kilómetros máximos y tu techo de precio. Si no lo tienes cerrado, lo acotamos contigo en una llamada."
- Paso 02 "La búsqueda y el peritaje": "Rastreamos concesionarios, stock profesional y subastas en España y en Europa. Cuando aparece el candidato, va a peritaje mecánico independiente antes de que tú lo veas."
- Paso 03 "La entrega": "Negociamos, cerramos el precio por escrito y te lo llevamos a tu puerta con la documentación hecha y el expediente completo en la mano."

### S4. El expediente (#expediente, elemento firma y momento interactivo)

- Kicker: "Qué te llega con el coche"
- H2: "Ningún coche sale sin su expediente."
- Cuerpo: "Seis comprobaciones, una por una. Si alguna no pasa, el coche no llega a tus manos y seguimos buscando."
- Instrucción del interactivo: "Mantén pulsado para verificar"
- Estado final: sello "VERIFICADO" y referencia mono "EXP. AG-2026-0847"
- Los seis puntos:
  1. "Kilómetros reales contrastados" / "Cruzamos el odómetro con el historial de ITV y de mantenimiento."
  2. "Sin daños estructurales" / "Medición de chasis y comprobación de reparaciones tapadas."
  3. "Historial completo" / "Revisiones, propietarios anteriores y uso real del vehículo."
  4. "Libre de cargas" / "Sin deudas, sin embargos y sin reserva de dominio."
  5. "Peritaje mecánico independiente" / "Lo revisa un perito que no cobra de quien vende."
  6. "Precio por escrito" / "Lo que cuesta el coche y lo que cuesta nuestro trabajo, por separado."

### S5. Compromisos (cuatro promesas, no testimonios inventados)

- Kicker: "Lo que firmamos"
- H2: "Cuatro cosas que no se negocian."
  1. "Tarifa fija, dicha antes de empezar." / "Sabes lo que cuesta nuestro trabajo desde la primera llamada. No cobramos del vendedor, ni del concesionario, ni de la financiera."
  2. "Un solo lado al que defender." / "Nos pagas tú. Por eso negociamos contra el precio, no a favor de él."
  3. "Tú decides sobre el expediente." / "Ves fotos, vídeo, peritaje y precio antes de que se cierre nada. Si algo no te cuadra, se descarta y seguimos."
  4. "La misma persona, todo el proceso." / "El mismo interlocutor desde el encargo hasta que te damos las llaves."

### S6. Preguntas (las objeciones reales de la investigación)

1. "¿Cuánto os lleváis de comisión?" / "Una tarifa fija que conoces antes de que empecemos a buscar. No cobramos nada del vendedor, ni del concesionario, ni de la financiera. Nuestro trabajo te lo facturamos a ti, y por eso solo tenemos un lado al que defender."
2. "¿No me saldría más barato ir yo?" / "A veces sí, y te lo vamos a decir. Nuestro trabajo se paga solo cuando hay margen que negociar, cuando el coche está lejos de tu provincia o cuando comprar mal te puede costar miles de euros. Si el coche que quieres está en el concesionario de tu calle al precio correcto, te lo decimos y no te cobramos."
3. "¿Y si cuando llega no me gusta?" / "No llega sin que lo hayas aprobado. Recibes el expediente con fotos, vídeo, peritaje y precio antes de cerrar la compra. La decisión de comprar es siempre tuya."
4. "¿Solo trabajáis coche de ocasión?" / "Nuevo, kilómetro cero o de ocasión. En coche nuevo el trabajo es sobre todo configuración y plazos, y ahí lo que te ahorras es tiempo y sorpresas de entrega."
5. "¿Buscáis fuera de España?" / "Sí. Buena parte del stock interesante está en Alemania, Bélgica u Holanda. Nos ocupamos del transporte, de la matriculación y de los impuestos, y todo eso entra cerrado en el expediente."
6. "¿Cuánto se tarda?" / "Depende de lo cerrado que sea el encargo. Un coche común, con margen de color y de extras, suele aparecer en dos o tres semanas. Una configuración muy concreta puede llevar dos meses. Te damos un plazo en la primera llamada y te contamos cómo va cada semana."

### S7. Solicitud (#solicitud, la única conversión)

- Kicker: "Tu expediente"
- H2: "Cuéntanos qué coche quieres."
- Cuerpo: "Rellena esto y te llamamos con una primera lectura: si es fácil de encontrar, qué debería costar y cuánto puede tardar."
- Campos y etiquetas: "Nombre y apellidos", "Email", "Teléfono", "Qué coche buscas", "Presupuesto máximo", "Para cuándo lo quieres", "Algo más que debamos saber"
- Placeholders: "Nombre y apellidos" / "tu@correo.com" / "600 000 000" / "Marca, modelo, motor, color, extras, kilómetros máximos" / "Ej. 35.000 €" / "Ej. antes de junio" / "Opcional"
- Botón: "Enviar mi expediente"
- Éxito: "Expediente recibido. Te llamamos en menos de 24 horas laborables."
- Error: "No ha salido. Escríbenos directamente y lo resolvemos."
- Envío: endpoint de Formspree en una constante marcada al principio del script. Sin
  endpoint configurado, el formulario muestra el estado de éxito y no envía nada.

### S8. Pie

Marca, navegación, datos de contacto (marcados como pendientes de confirmar), aviso
legal y privacidad. Negocio real, así que no lleva aviso de marca ficticia.

## 7. La capa vectorial

- **Ruta del proceso:** polilínea SVG dibujada a mano que une los tres pasos, con
  stroke-dashoffset gobernado por el scroll. Se dibuja al entrar la sección.
- **Sello del expediente:** SVG circular. El anillo se dibuja y la marca de verificación
  se traza cuando el interactivo se completa.
- **Cantoneras** tipo marca de recorte en las fichas de expediente.
- **Entorno fijo:** una sola capa detrás de todo, resplandor radial en deriva muy lenta
  más grano fino y filetes verticales tenues, ciclo de 90 segundos.
- **Partículas susurro:** catorce motas en deriva, solo en el escenario del héroe.
- **Favicon:** SVG en línea con el monograma de la marca.
- Todo con movimiento reducido honrado: estados finales mostrados, motores parados.

## 8. La lista de ingeniería

Blob con anillo de carga, lerp normalizado por dt, seeks con compuerta, escrituras al
DOM solo al cambiar, bandas paceadas y validadas con el flick test, sistema de
legibilidad de cuatro capas, las cinco compuertas del héroe estático vivas con
listeners de cambio, página completa sin vídeo, y el suelo de calidad entero.

## 9. La compuerta de copia

Toda línea visible de arriba se monta literal. La página construida tiene que pasar la
compuerta de la fase 9: cero rayas largas, cero palabras de catálogo, y el barrido de
tics de IA en el cuerpo de texto. Los recursos deliberados de marca (el tríptico de
pasos, los remates cortos) son oficio y se quedan.

---

## Anexo: lo que cambió en la construcción, y por qué

El paquete se escribió para un héroe de vídeo generado con Higgsfield. Al llegar
a la generación, la política de red de esta sesión resultó bloquear el CDN de
Higgsfield, así que los ficheros generados no se podían descargar para
inspeccionarlos, reencodearlos con intervalo de fotograma corto ni auditarlos.
Con esa información sobre la mesa, el cliente eligió que el héroe se dibujara
con código.

Lo que cambia: el plano deja de ser vídeo fotorrealista y pasa a ser una escena
dibujada en canvas, la nave de entrega contada como arquitectura de luz. La
cámara avanza de verdad por un túnel de portales mientras el suelo mojado los
duplica, y al final espera la firma luminosa del coche. El coche nunca se
dibuja, y eso es deliberado: el coche es el que tú pidas.

Lo que no cambia: el motor de scroll entero (lerp normalizado por dt, escrituras
al DOM solo al cambiar, bandas paceadas y validadas con el flick test, las
cuatro capas de legibilidad, las cinco compuertas del héroe estático vivas en
los dos sentidos), la premisa, la paleta, el trío tipográfico, el mapa de bandas
y toda la copia, que se monta literal.

Lo que mejora: cero peticiones a terceros, las fuentes se sirven desde el propio
sitio, la página pesa 232 KB con la caché vacía y carga en 106 ms medidos, y no
existe el riesgo de que aparezca el logotipo de una marca ajena en la web.
