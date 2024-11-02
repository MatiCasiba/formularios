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
            <legend> titulo del </legend>
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