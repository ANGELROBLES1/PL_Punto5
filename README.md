# Parser descendente recursivo  (Punto 5)
## Descripción

En este punto se diseñó e implementó un parser descendente recursivo capaz de analizar un lenguaje simple que incluye:

- Asignaciones
- Estructuras condicionales

El parser se construyó manualmente en Python, implementando el mecanismo de emparejamiento de tokens, lo que permite validar la sintaxis de las instrucciones y detectar errores de forma explícita.

## Archivos del proyecto
- parser.py: Implementación del parser descendente recursivo
- main.py: Tokenización y ejecución del programa
- pruebas.txt: Casos de prueba (válidos e inválidos)
# Lenguaje diseñado

El lenguaje soporta dos tipos de instrucciones:

1. Asignación
``
x := 5
y := 10
``
2. Condicional
``
when x do y := 3 otherwise y := 4
``
## Gramática utilizada
``
<prog> ::= <stmt>
<stmt> ::= <asig> | <cond>
<asig> ::= ID := <expr>
<cond> ::= when <expr> do <stmt> otherwise <stmt>
<expr> ::= ID | NUM
``
## Funcionamiento del parser

El parser sigue un enfoque descendente recursivo:

Cada regla de la gramática se implementa como una función
Se analiza la entrada de izquierda a derecha
Se utiliza la función match() para validar tokens
Emparejamiento de tokens

El método match() es el núcleo del parser:
``
def match(self, esperado):
    if self.actual() == esperado:
        self.pos += 1
    else:
        raise Exception("Error de sintaxis")
``
Este método garantiza que la entrada cumpla exactamente con la estructura definida.

## Ejecución del programa
1. Abrir terminal
``
cd Descendente
``
3. Ejecutar
``
python3 main.py
``
Salida del programa

Ejemplo:
``
Linea 1: x := 5
ACEPTA
``
``
Linea 3: when x do y := 3 otherwise y := 4
ACEPTA
``
## Pruebas realizadas
1. Casos válidos
``
x := 5
when x do y := 3 otherwise y := 4
``
Resultado:

- Las instrucciones cumplen la gramática
- El parser acepta correctamente
2. Casos inválidos
``
x 5 :=
``
Salida:
``
Error: se esperaba := y se encontró 5
NO ACEPTA
3. Error en estructura condicional
when do x := 3
``
Resultado:

- Falta la expresión
- El parser detecta inconsistencia
4. Error en asignación incompleta
``
when x do y := otherwise z := 2
``
Resultado:

- Falta valor en la asignación
- Error detectado correctamente
- Análisis del comportamiento

## El parser:

- Detecta errores sintácticos
- Indica el punto exacto del fallo
- Evalúa múltiples instrucciones
- Funciona sin librerías externas
## Ventajas del enfoque
- Implementación clara y directa
- Control total sobre el análisis
- Fácil detección de errores
- Representación fiel de la gramática
## Limitaciones
- No soporta gramáticas ambiguas
- No permite recursión izquierda
- Requiere diseño cuidadoso de la gramática
## Conclusiones
- Se implementó exitosamente un parser descendente recursivo
- El método de emparejamiento permite validar la sintaxis de forma precisa
- El sistema detecta errores de manera clara
- El lenguaje diseñado es funcional y extensible
<img width="545" height="467" alt="image" src="https://github.com/user-attachments/assets/eaac2dd9-4fd0-465e-b829-b14b42e43dce" />
