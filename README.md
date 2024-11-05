* Nombre: Matias Casiba
* Link Github Repo:
* Link Netlify:

# Formularios

## Armando la estructura
Al momento de armar este formuliario, utilizare los elementos: 
```sh
<h1> Titulo </h1>
<div>
    <form action="dirección" method="post">
        <fieldset> #lo utilizo para agrupar campos dentro del formulario
            <legend> titulo del fieldset </legend>
            <label> texto para el input<label>
            <input> #entradas
        </fieldset>

        <div> # dentro de esto, estaré usando inputs de tipo radio, con la finalidad de que solamente se pueda seleccionar una opción, a diferecia de los checkbox que podremos seleccionar varias
            <label>Sexo:*</label>
            <div class="genero-contenedor">
              <input id="femenino" type="radio" name="genero" value="femenino">
              <label for="femenino">Femenino</label>
              <input id="masculino" type="radio" name="genero" value="masculino">
              <label for="masculino">Masculino</label>
              <input id="otro" type="radio" name="otro" value="otro">
              <label for="otro">Otro</label>
            </div>
        </div> # es importante que los name="" contengan el mismo nombre en cada input, al igual que en los checkbox 

        <div> # lo usare sin fieldset para colocar dos opciones, uno para aceptar las condiciones y otro para que seleccion si quiere recibir novedades
            <input id="lbl-condiciones" type="checkbox" name="terminos" value="condiciones" required>
            <label for="lbl-condiciones">Acepto las condiciones*</label>
        </div>
        <div>
            <input id="lbl-novedades" type="checkbox" name="terminos" value="novedades">
            <label for="lbl-novedades">Deseo recibir novedades</label>
        </div>
    </form>
</div>
```
En el archivo de css a los div les estaré dando espacio para que no queden tan pegados:
```sh
div{
  margin: 3px 0 3px 0; # arriba(3px) derecha(0) abajo(3px) izquierda(0)
}
```

### Pattern
En dos inputs relacionado con números, en vez de usar type="number", usaré type="text" pattern="[0-9]+", con la finalidad de que el usuario solamente ingrese números:
```sh
<div> 
    <label>Documento:*</label>
    <input type="text" pattern="[0-9]+" title="solo números" name="dni" required> #cuando me para en el input, con el title me mostrará el mensaje "solo números"
</div>

<div>
    <label>Teléfono:</label>
    <input type="text" pattern="[+0-9]+" name="telefonno" placeholder="Código de área y número" required> # en este pattern, vez que dentro de [] se encuentra el símbolo +, esto me permite ingresar el símbolo + y tambien los números.
</div>
```

### FOR y ID
En algunos labels notarás los for="" y en inputs notarás algunos ID="", lo que logra esto es una vinculación del input con el texto del label. Para lograrlo el for y el id deberá contener el mismo valor (sino no se logra la vinculacion), entonces cuando me pare sobre el texto y lo seleccione, lograrás acceder al input, sea de tipo texto, email, number, checkbox, radio, etc. Veremos un ejemplo:
```sh
<div class="genero-contenedor">
    <input id="femenino" type="radio" name="genero" value="femenino">
    <label for="femenino">Femenino</label>

    <input id="masculino" type="radio" name="genero" value="masculino">
    <label for="masculino">Masculino</label>

    <input id="otro" type="radio" name="otro" value="otro">
    <label for="otro">Otro</label>
</div>
```
Cuando aprete en el texto masculino, se marcará el circulito, entonces no tengo necesidad de si o si ir al circulo al lado del texto para seleccionarlo.

### Button
Usaré botones (siempre se encuentra dentro del formulario), uno para enviar toda la info ingresada y el otro para restablecer:
```sh
<form>
    <button type="submit">Iniciar afiliación</button> # envia los datos
    <button type="reset">Restablecer</button> # resetea
<form>
```

## Colores y ajustes en el formulario
Al momento de dar colores en el formulario, trabajare con los elementos que se encuentran en el index.html y clases:
```sh
html{
  background-color: rgb(43, 41, 41); # generaré un color oscuro (no tanto) de fondo en la página
}
h1{
  text-align: center; # el titulo se colocará en el medio
  color: white; # el color del texto será de blanco
}

fieldset{ 
  background-color: rgb(196, 203, 202); # usaré de fondo un color claro en los campos de estos del formulario.
  border: 2px solid rgb(35, 81, 55); # tendrá un dorde solido de color verde oscuro, el 2px es el grosor del borde.
  border-radius: 4px; # hará que las esquinas no sean puntiagudas.
  margin-bottom: 20px; # esto generará espacio en el margen de abajo del fieldset.
}
legend{
  background-color: rgb(67, 106, 85); # trabajo en el fondo con un color verde oscuro para los titulos que se encuentran en los fildset.
  color: white; # el color de estos titulos sera blanco .
  padding: 1.5%; # esto me dará un relleno que hará que se agrande un poco el cuadrado de color verde oscuro.
  border-radius: 5px;
}

label{
  display: block; # los label se comportarán cómo elementos de bloque, se posiciona en una nueva linea por defecto, colocando cualquier contenido siguiente (como el input) debajo de este
}

input, select, textarea{
  border: 1px solid rgb(45, 72, 57); # le asigno a los elementos de input, select y textarea un borde solido con un color verde oscuro.
}

button{ # los botones tendrá de fondo un color verde oscuro, el texto estará en blacnco, tendra un grosor de 2% y en los bordes usaré un color verde claro.
  background-color: rgb(67, 106, 85);
  color: white;
  padding: 2%;
  border-color: rgb(170, 191, 188);
  border-radius: 5px; # las esquinas no será tan puntiagudas.
}
```

### Trabajando con las clases
En varios elementos que están en el archivo index.html, tendrán clases, me va a servir para darles diseño y color, lo cual afectará a los elementos que contengan estas clases:
```sh
.datos{
  text-align: center; # sirve para centran lo que haya dentro de los div con esta clase
}

.contenedor-cuadrados-circulos input, .contenedor-cuadrados-circulos label{ 
  display: inline-block;
}

.ancho-i-s-t{ # la clase sera para los inputs(i), select(s) y textarea(t), el objetivo es no afectar a los inputs de tipo radio y checkbox
  width: 60%; #ancho
  padding: 1%;
}

.sede{ # usaré margin de arriba y abajo, para lo que haya dentro del contenedor div, se separe maás del label.
  margin-top: 20px;
  margin-bottom: 20px;
}
.color-p{ # color para el texto del elemento p
  color: white;
}
.terminos{ # servirá para darle color al texto de las 2 opciones finale, la condicion y novedades.
  color: white;
}
```
* Nota: la clase contenedor-cuadrados-circulos indicando al input y label, hace que estos dos elementos dentro del contenedor con la clase, se comporten como elementos inline-block. Con esto, ambos elemetos se alinean uno al lado del otro (en la misma linea), siempre que haya espacio, ¿por que cuadrados y circulos? me refiero que esto tambien se aplicará para los inputs de tipo checkbox y radio. Dentro de algunos elementos notarás más de una clase, servirá para aplicar tanto diseño como color a la vez en los elementos que lo contengan. Ejemplo:
```sh
<div>
    <label>Sede Palermo</label>
    <div class="sede contenedor-cuadrados-circulos">
        <input type="checkbox" name="actividad" value="basquet">
        <label>Básquet</label>
        <input type="checkbox" name="actividad" value="boxeo">
        <label>Boxeo</label>
        <input type="checkbox" name="actividad" value="futbol">
        <label>Fútbol</label>
        <input type="checkbox" name="actividad" value="tenis">
        <label>Tenis</label>
    </div> <!-- sede palermo -->

    <label>Sede Rosario</label>
    <div class="sede contenedor-cuadrados-circulos">
        <input type="checkbox" name="actividad" value="basquet">
        <label>Básquet</label>
        <input type="checkbox" name="actividad" value="futbol">
        <label>Fútbol</label>
        <input type="checkbox" name="actividad" value="rugby">
        <label>Rugby</label>
        <input type="checkbox" name="actividad" value="voley">
        <label>Voley</label>
    </div> <!-- sede rosario -->

</div> <!-- sedes -->
``` 

## FOCUS
En el archivo css, estaré trabajando con focus, ¿la finlidad? que cuando seleccione un input o textarea, cambie tanto su color de fondo en estos elementos como en el elemento fieldset y mantenga el el color asignado:
```sh
input:focus, textarea:focus{
  background-color: rgb(43, 98, 69);
}
fieldset:focus-within{
  background-color: rgb(170, 191, 188);
}
```
* Nota: focus-within, es una pseudoclase que aplica estilos a un elemento (ene este caso fieldset), cuando cualquiera de sus elementos descendientes tengan el foco. Entonces si sleccion un input, cambia su color de fondo y el color de fondo del elemento fieldset.

## Diseño en el título, barras, inputs, textarea e actualizaciones
### Bordes con diseño
Eh agregado bordes con estilo, el primero se encuentra en el título, y el segundo los utilizo como divisiones, acá te muestro como arme el del título:
```sh
.bordes-titulo{
  border: 15px solid #4d6d63; # grosor del borde (15px), solido y su color
  border-left-color: transparent;
  border-right-color: transparent;
  width: 80%; # esto se ajustará al 80% de la pantalla
  margin: auto; # lo colocará en medio ya que el elemento h1 está ahora dentro de un contenedor div
  margin-bottom: 20px; # el espacio deabajo
}
```
Eh rodeado el título con bordes, pero como verás, falta el de los laterales, verás que tendrá un estilo de diagonales en el borde de arriba y debajo, esto lo logro haciendo transparente los laterales (izquierdo y derecho). Este borde creado lo tendrá un div con la clase que se ha creado:
```sh
<div class="bordes-titulo">
    <h1>Vení al Gym! 💪🏼</h1>
</div>
```

### Bordes para separar
Se agregaron 2 bordes que están en formato de circulos, para lograr esto usé el elemento hr entre elementos fieldsets y en css le di el estilo:
```sh
hr {
  border: none;
  width: 55%;
  border-top: 15px dotted #a9c0b8;
  margin-bottom: 20px;
}
```
* Nota: saqué los demás bordes y solo trabajé con el border-top, quien hace que esté en formato de circulos es el estilo "dotted", este borde tendrá un espacio de 20px en el margen de abajo y contendrá un ancho del 55% de la pantalla.

## Ajuste en los inputs y textarea
Eh agregado espacios en los márgenes de arriba y abajo de los inputs, textarea y select, también al momento de escribir, se iniciará del lado derecho, al igual que los placeholders notarás que se encuentran del lado derecho.
* Espacio y inicio del lado derecho: En estos elementos habrá espacio arriba y debajo.
```sh
input, select, textarea{
  margin-top: 10px;
  margin-bottom: 10px;
}
```

* Text-derecho: eh creado una clase solamente para que lo contengan inputs y el textarea, de esta manera solo esos elementos se iniciará a la derecha, al igual que los placeholders lo notarás del lado derecho:
```sh
.texto-derecha{
  text-align: right;
}
```

## Actualización en algunos sectores
Retoqué algunos elementos:
* Fieldset: tendrá un ancho del 80% de la pantalla y un margen de manera automática. 
* Se ha agregado un ajuste solo para el textarea, tendrá unn alto que no te permitirá achicar menos de la altura asignada pero si agrandar y de manera vertical, todo eso lo logro de la siguiente manera:
```sh
textarea{
  resize: vertical; # al momento de agrandar, solo lo podrás hacer vertical mente
  height: 100px; # su alto
  min-height: 100px; # no podrás minimizar menos de esto
}
```

## Importandon fuente para los textos, actualizacion de elementos y sus colores

### Importando tipografías
Importe tipografías, son las que verás al inicio del archivo css, me serviran para darle una fuente al titulo y todo texto que se encuentre dentro del elemento html (menos el titulo que tendrá otra distinta):
```sh
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

html{
  font-family: "Poppins", sans-serif;
}

h1{
  font-size: 50px; # el tamañao del titulo
  font-family: "Roboto", sans-serif; 
  font-weight: 900; # el grosor del titulo
}
```
### Espacios de margen en algunos elementos
Fuí agregando espacios de margen en algunos elementos y clases, te los mostraré:
```sh
p{
  margin-bottom: 40px;
  margin-left: 8.5%;
}

button{
  margin-bottom: 20px;
  margin-left: 20px;
}

.terminos{
  margin-left: 8.5%;
}
```
* Nota: en el elemento button, su padding no estará en 2%, lo actualicé a 20px, el motivo es porque al momento de que se agranda la página, se va agrandando los dos botones, mientras que con 20px mantiene el mismo tamaño asignado.

### Actualizando colores en los elementos
Ya noe estaré usando rgb, pasaré a usar hexadecimales:
```sh
#a9c0b8 # verde claro
-
#84a59d # verde poco oscuro (#a9c0b8 similar poco oscuro)
-
#2d6a4f # verde oscuro
-
#4d6d63 # verde mate oscuro
-
#1b4332 # verde mate mas oscuro
-
#252323 # negro mate
```
estos colores fueron usados en bordes y fondos, de elementos y clase.
* Nota: cambie el color del texto dentro de los inputs y de los placeholders, a un color claro para que sea más notoria las letras cuando en su fondo se oscurezca el color:
```sh
input:focus, textarea:focus{
  color: white;
}
input:focus::placeholder{
  color: white;
}
```

### Actualización del elemento bottom con hover
En los botones estaré usando hover, con la finalidad de que cada vez que me pare sobre los botones, cambieen de color tanto sus bordes como el fondo, al igual que el texto que contienen dentro, lo eh hecho de la siguiente forma:
```sh
button:hover{
  color: #2d6a4f; # el color del texto
  background-color: #a9c0b8;
  border-color: #2d6a4f;
}
```


## FUTURE FORMULARIO
Cree otro archivo css y realicé una temática futuristica, para esto usé una imágen de fondo, utilicé colores llamativos y eh aplicado un neon en el título y los legends, también eh importado otra dos fuentes y trabajé un poco con los tamaños del texto.

### Imgen de fondo y color
La imagen que esta de fondo, se encuentra dentro de la carpeta public (en una carpeta llamada image), para colocarlo de fondo lo realicé de la siguiente manera:
```sh
html{
  background-image: url(public/image/pesa.png); # la direccion de donde se encuentra la imagen
  background-color: #59189a; # su color de fondo
}
```
### Colores y neon
Como bien mencioné, eh usado colores llamativos, al momento de trabajar con neon lo de esta manera:
```sh
.bordes-titulo{
    box-shadow: 0 0 30px #ccff00;
    border-radius: 20px;
}
```
El box-shadow me va a permitir trabajar con este estilo, la función de este es generar una caja con sombra al rededor, entonces utilicé un color llamativo/fluor para darle un estilo neon, no solo lo eh usado en esto, sino tambien en los elementos de legend y botones. No siempre mantendrá el color asignado (#ccff00, que es el que verás en todo texto, bordes y fondo de botones, del formulario), cuando seleccione un input, cambiará el color a un rojo, tanto los bordes del legened como los del fieldset, input, texto y botones. Para esto lo que hice fue trabajar con los hover (para los elementos button) y los focus, en esto encontrarás el color rojo (#ef233c):
```sh
legend{
  background-color: #240046;
  box-shadow: 0 0 20px #ccff00;
  color: #ccff00; # color del texto
  border: 2px solid #ccff00;
}
input:focus, textarea:focus{
  background-color: #5a189a;
  color: #ef233c;
  border-color: #ef233c;
}
input:focus::placeholder{
  color: #ef233c;
}
  
fieldset:focus-within{
  border-color: #ef233c;
}
fieldset:focus-within legend{
  border-color: #ef233c;
  box-shadow: 0 0 30px #ef233c;
  color: #ef233c;
}
fieldset:focus-within label{
  color: #ef233c;
}
fieldset:focus-within select{
  color: #ef233c;
}
fieldset:focus-within p{
  color: #ef233c;
}
  
# hovers
.bordes-titulo:hover{
  box-shadow: 0 0 30px #ef233c; 
  border-radius: 50px;
}

h1:hover{
  color: #ef233c; # se pone de color rojo el texto
}

 button:hover{
  color: #ef233c;
  background-color: #ccff00;
  box-shadow: 0 0 30px #ef233c;
  border-color: #ef233c;
}
.terminos:hover{ # cuando te pares en el texto donde se encuentran la condicion y novedades (al igual que en el elemento p), se pondrá de color verde fluor (con el que eh estado trabajando en todo el formulario)
  color: #ccff00;
}
p:hover{
  color: #ccff00;
}
```
* Nota, em el fondo de los inputs habrá un color violeta más oscuro y cuando se seleccione, pasará a tener un color violeta un poco claro.
* En los botones notarás que cuando te pares sobre ellos, tendrás un color rojo en el texto, bordes y sombra, eso lo logré hacerlo con el button:hover.

### Color de fondo en los fieldset
Notarás que en los fueldset, conserva su color de fondo, pero se ve transparente, para hacerlo lo hice con los siguiente:
```sh
fieldset{
  background-color: #240046df; 
}
```
### Los 2 bordes entre los fieldset
Lo que eh hecho ahi, fue solamente modificar el color, que tenga un estilo solid y disminuir el grosor
```sh
hr {
  border: 2px solid #ccff00;
  border-radius: 10px;
}
```

### Colores usados:
Los colores que eh usado para este fromulario, fueron:
```sh
ccff00 # verde fluor (en la gama de verdes)
-
ccff006c # verde fluor medio transparente ( en la gama de verdes)
-
ef233c # rojo claro (en la gama de rojos)
-
59189a # violeta (en la gama de violetas)
-
5a189a # violeta similar al #59189a (en la gama de violetas)
-
240046 # violeta oscuro (en la gama de violetas)
-
240046df # violeta oscuro medio transparente (en la gama de violetas)
-
11082e # violeta mas ocuro que #240046 (en la gama de violetas)
```

## Actualizacion del future-style y index.html
Eh modificado el degradado de lña sombra en el título, lo eh reducido
```sh
.bordes-titulo{
  box-shadow: 0 0 15px #ccff00;
}
```
También agregue una nueva clase para un elemento p:
```sh
.p-en-fieldset{
  margin-left: auto; # en el ultimo fieldset habia un elemento p que no se encontraba de todo al lado izquierdo, con esta correción logrue hacerlo.
}
```
index.html:
```sh
<fieldset>
  <p class="p-en-fieldset">texto<p> # nueva clase
  # todas las etiquetas
<fieldset>
```