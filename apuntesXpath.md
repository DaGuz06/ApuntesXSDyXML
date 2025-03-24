
#### **Selección de Nodos**

1. **Selección absoluta** (`/`):
    
    - `/raíz/elemento/subelemento` → selecciona un nodo específico desde la raíz.
        
2. **Selección relativa** (`//`):
    
    - `//elemento` → selecciona todos los nodos con ese nombre en cualquier parte del documento.
        
3. **Nodo actual (`.`) y nodo padre (`..`)**:
    
    - `./elemento` → selecciona desde el nodo actual.
        
    - `../elemento` → selecciona desde el nodo padre.
#### **Uso de atributos**

- `//elemento[@atributo='valor']` → selecciona nodos con un atributo específico.
    
- `//elemento[@id='123']` → busca un elemento con `id="123"`.

#### **Operadores avanzados**

- `//elemento[text()='valor']` → selecciona nodos cuyo texto sea "valor".
    
- `//elemento[contains(text(), 'parcial')]` → busca un texto parcial.
    
- `//elemento[position()=1]` → selecciona el primer elemento.
    
- `//elemento[last()]` → selecciona el último elemento.


### Ejemplos
```xml
<personas>
    <persona id="1">
        <nombre>Ana</nombre>
        <edad>30</edad>
    </persona>
    <persona id="2">
        <nombre>Carlos</nombre>
        <edad>25</edad>
    </persona>
</personas>
```

Consulta para extraer los nombres --> //persona/nombre o //nombre

```xml
<personas>
    <persona id="1">
        <nombre>Ana</nombre>
        <edad>30</edad>
    </persona>
    <persona id="2">
        <nombre>Carlos</nombre>
        <edad>25</edad>
    </persona>
    <departamento>
		<nombre>Marketing</nombre>
		<personas>20</personas>
	</departamento>
</personas>
```

Aquí no serviría con //nombre ya que sacaría también el nombre del departamento

```xml
<empresa>
    <empleado id="1" departamento="IT">
        <nombre>Ana</nombre>
        <edad>30</edad>
    </empleado>
    <empleado id="2" departamento="Marketing">
        <nombre>Carlos</nombre>
        <edad>25</edad>
    </empleado>
    <empleado id="3" departamento="IT">
        <nombre>Elena</nombre>
        <edad>28</edad>
    </empleado>
</empresa>
```

```xpath
//empleado[nombre="Carlos"]/@id

//empleado/@departamento

//empleado/concat(nombre, "-", @departamento)

```
- Para sacar el ID de la persona Carlos se saca mediante los atributos (primera consulta)
- Para sacar los nombres de los departamentos (se encuentra en los atributos) se usa @departamento
- Para sacar el nombre de la persona y nombre de departamento en una sola consulta se usa el operador "|" que sirve para enlazar dos o mas consultas
- Para concatenar se usa concat() (Ejemplo 3)
