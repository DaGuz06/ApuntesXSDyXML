Un archivo XML es un lenguaje de marcado enfocado en el almacenamiento y transporte de datos
La estructura de este lenguaje se compone de etiquetas (elementos), contenido de texto y atributos . Los elementos también se pueden anidar para representar relaciones jerárquicas
```
<persona>
    <nombre>Juan</nombre>
    <edad>30</edad>
    <ciudad>Madrid</ciudad>
    <direccion calle="Calle Mayor" numero="10" />
</persona>
```

>*Este archivo XML contiene datos sobre una persona*
> El **elemento `<persona>`** contiene otros tres elementos: `<nombre>`, `<edad>`, y `<ciudad>`.
> El **elemento `<direccion>`** tiene **atributos** (`calle` y `numero`).

XML es muy útil para organizar datos de manera jerárquica, pero no tiene una forma interna de garantizar que esos datos sean correctos o sigan un formato específico. Por ejemplo, puedes tener un archivo XML donde el campo "edad" contenga texto en lugar de un número. Aquí es donde [[XSD]] entra en acción: se utiliza para definir las reglas de cómo debe ser el contenido de un XML, como qué elementos deben estar presentes, qué tipo de datos deben contener y cuántas veces pueden repetirse.

### Conectar XML a XSD
Para conectar un XML con un XSD lo haremos de la siguiente manera:
```
<?xml version="1.0" encoding="UTF-8"?>
<etiqueta-raiz xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="nombreDelXSD.xsd">

	<etiquetas elementos>
	<etiquetas elementos>
	<etiquetas elementos>
<etiqueta-raiz>
```
> Los atributos xmlns:xs y xsi:noNamespaceSchemaLocation son atributos de la etiqueta raíz del XML

### Validar archivo XML con un XSD
En la terminal de linux o de macOS con la herramienta xmllint:
```
xmllint --noout --schema archivo.xsd archivo.xml
```
> Para que dentro de la terminal nos detecte los archivos tenemos que estar en la misma ruta
> Para instalar xmllint en linux se pone el comando ```sudo apt install libxml2-utils```
> Para instalar xmllint en Git Bash se tiene que hacer con Scoop:
> 	1. iwr -useb get.scoop.sh | iex
> 	2. scoop install libxml2