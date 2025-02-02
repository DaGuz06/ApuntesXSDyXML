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


