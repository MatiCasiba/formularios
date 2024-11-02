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

