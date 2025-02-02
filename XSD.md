XSD es un lenguaje utilizado para definir la estructura de los archivos [[XML]]. Es una especie de "Manual".
Con estos archivos se puede especificar reglas como:
- Que elementos tiene un archivo XML
- Que tipo de datos puede tener cada elemento
- Si los elementos son obligatorios o pueden faltar
- Que tan repetitivo puede ser un elemento
La estructura de XSD es más formal y está orientada a definir tipos de datos, restricciones y relaciones entre los elementos.
```
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
                <xs:element name="edad" type="xs:int"/>
                <xs:element name="ciudad" type="xs:string"/>
                <xs:element name="direccion" maxOccurs="unbounded">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="calle" type="xs:string"/>
                            <xs:element name="numero" type="xs:int"/>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>

```

>El elemento `<persona>` tiene un tipo complejo (`<xs:complexType>`) que define una secuencia de subelementos (nombre, edad, ciudad, y dirección).
> El elemento `<direccion>` tiene un tipo complejo que contiene los subelementos `<calle>` y `<numero>`.
> También se define que el elemento `<direccion>` puede aparecer varias veces (`maxOccurs="unbounded"`).

### Etiquetas
- La etiqueta raíz es  ```<xs:schema>``` que se utiliza para definir que el documento es un XSD
```
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <!-- El codigo va aquí -->
</xs:schema>
```
 >**`xmlns:xs`** es un atributo que define el espacio de nombres para los elementos XSD.
> Dentro de `<xs:schema>`, se definen los elementos, tipos, y restricciones que compondrán el esquema.

- La etiqueta ```<xs:element>``` se usa para definir un elemento que aparecerá dentro del XML. Dentro de esta etiqueta, los atributos mas comunes son:
	-  **`name`**: El nombre del elemento.
	- **`type`**: El tipo de dato del elemento (como `xs:string`, `xs:int`, etc..).
	- **`minOccurs`**: Número mínimo de veces que el elemento puede aparecer.
	- **`maxOccurs`**: Número máximo de veces que el elemento puede aparecer.
```
<xs:element name="nombre" type="xs:string" minOccurs="1" maxOccurs="1"/>
```

- La etiqueta ```<xs:complexType>``` define un elemento que contiene otros elementos (cadena de texto, números, fechas...)
```
<xs:complexType>
    <xs:sequence>
        <xs:element name="calle" type="xs:string"/>
        <xs:element name="numero" type="xs:int"/>
    </xs:sequence>
</xs:complexType>

```
- La etiqueta ```<xs:simpleType>``` define un elemento que solo tiene un elemento
```
<xs:simpleType name="telefono">
    <xs:restriction base="xs:string">
        <xs:length value="10"/>
    </xs:restriction>
</xs:simpleType>
```
- La etiqueta ```<xs:sequence>``` se utiliza para para especificar el orden los elementos dentro de un ```<xs:complexType>``` mientras que con la etiqueta ```<xs:all>``` el orden puede ser el que queramos 
```
<xs:sequence>
    <xs:element name="nombre" type="xs:string"/>
    <xs:element name="edad" type="xs:int"/>
</xs:sequence>
```
>El orden tendría que ser primero nombre y luego edad
```
<xs:sequence>
    <xs:element name="nombre" type="xs:string"/>
    <xs:element name="edad" type="xs:int"/>
</xs:sequence>
```
>No hay orden
- La etiqueta ```<xs:choice>``` se utiliza para permitir que un ```<xs:complexType>``` tenga 1 solo elemento de la lista dentro de esta etiqueta
```
<xs:complexType name="contacto">
    <xs:choice>
        <xs:element name="direccion" type="xs:string"/>
        <xs:element name="telefono" type="xs:string"/>
    </xs:choice>
</xs:complexType>
```
> El elemento tendrá o dirección o teléfono pero no ambos
