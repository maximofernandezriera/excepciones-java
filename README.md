# Uso de Excepciones en Java

## 1- Excepciones
El término excepción es una abreviatura de situación excepcional. Se trata de una situación que altera la ejecución normal de un programa. Por ejemplo, en una calculadura, un usuario intenta realiza la división 2 / 0. En ese momento, el sistema crea un objeto, que se llama objeto de excepción y lo pasa de una llamada de método a otra, buscando quien pueda hacerse cargo. Si no existe nadie, será la propia JVM quien lo haga.

El uso de excepciones tiene varias ventajas:

- Permiten separar el código de tratamiento de errores del código normal.
- Evitan que haya errores inadvertidos.
- Permiten la propagación de los errores.
- Permiten agrupar en un lugar común el tratamiento de errores.

## 2- Tipos de Excepciones
Podemos agrupar las excepciones en 3 grandes tipos:

Excepciones comprobadas (checked exceptions): son aquellas excepciones que pueden surgir internamente en un programa, pero que al estar bien escrito, podemos tratar y de las que nos podremos recuperar.
Errores (errors): situaciones externas que no son anticipables, y de las que puede que no podamos recuperarnos (por ejemplo, un error hardware). Son un tipo no comprobado (unchecked)
Errores de ejecución (Runtime errors): son situaciones interas de la aplicación, de las que probablemente no podamos recuperarnos. Son un tipo no comprobado (unchecked).

# 3- Tratamiento de excepciones en el código Java

Se realiza utilizando la siguiente sintaxis:

        try {
            instrucciones;
        } catch (Exception e) {
            instruccinoes;
        } finally {
            instrucciones
        }
        finally no es obligatorio, y podemos incluir más de un bloque catch.

# 4- Bloque try
Debe envolver las sentencias que son susceptibles de provocar uno o varios tipos de excepción. Debemos agrupar las sentencias que vayan a tener un tratamiento idéntico de la situación excepcional.

    try {
            int a = 2;
            int b = 0;
            System.out.println(a/b); //Error de división entre 0            
        } catch(ArithmeticException ex) {
            //ex.printStackTrace();
            System.err.println("Error: " + ex.getMessage());
        }
# 5- Bloque catch
Sirven como manejadores de las situaciones excepcionales. Puede haber más de uno. Cada bloque puede manejar uno o más tipos de excepciones:

        try {
            for (int i = 0; i < 5; i++) {
                System.out.println(mensajes[i].toUpperCase());
            }
        } catch (ArrayIndexOutOfBoundsException | NullPointerException ex) {
            System.err.println("Tratamiento común a las excepciones");
        }
 
        try {
            for (int i = 0; i < 5; i++) {
                System.out.println(mensajes[i].toUpperCase());
            }
        } catch (ArrayIndexOutOfBoundsException ex) {
            System.err.println("Tratamiento particular a las excepción ArrayIndex...");
        } catch (NullPointerException ex) {
            System.err.println("Tratamiento particular a la excepción NullPointer...");
        }
# 6- Bloque finally
Se ejecuta siempre, tanto si hemos terminado correctamente el bloque try como el bloque catch. Se suele utilizar como código que asegura el cierre de recursos abiertos (ficheros, bases de datos, …).
