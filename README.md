1. Leer la edad del asegurado.
2. Leer el estado civil del asegurado.
3. Si el asegurado es menor de 18 años, mostrar un mensaje indicando que no es elegible para el seguro.
4. Si el asegurado tiene entre 18 y 24 años:
     a. Calcular el recargo como el 10% del precio base.
5. Si el asegurado tiene entre 25 y 49 años:
     a. Calcular el recargo como el 20% del precio base.
6. Si el asegurado tiene 50 años o más:
     a. Calcular el recargo como el 30% del precio base.
7. Si el asegurado está casado:
     a. Leer la edad del cónyuge.
     b. Si el cónyuge tiene menos de 18 años, mostrar un mensaje indicando que no es elegible para el seguro.
     c. Aplicar el recargo correspondiente al cónyuge basado en su edad.
     d. Sumar el recargo del cónyuge al recargo total.
8. Leer la cantidad de hijos del asegurado.
9. Calcular el recargo por cantidad de hijos como el 20% del precio base por cada hijo.
10. Sumar todos los recargos al precio base para obtener el precio total de la cotización.
11. Mostrar el precio total de la cotización.


Codigo

public class CotizadorSeguros {

    public static double calcularCotizacion(int edadAsegurado, String estadoCivil, Integer edadConyuge, int cantidadHijos, double precioBase) {
        double recargoTotal = 0;

        // Verificar si el asegurado es mayor de edad
        if (edadAsegurado < 18) {
            System.out.println("El asegurado no es elegible para el seguro.");
            return -1;
        }

        // Calcular recargo basado en la edad del asegurado
        if (edadAsegurado >= 18 && edadAsegurado <= 24) {
            recargoTotal += precioBase * 0.1;
        } else if (edadAsegurado >= 25 && edadAsegurado <= 49) {
            recargoTotal += precioBase * 0.2;
        } else {
            recargoTotal += precioBase * 0.3;
        }

        // Calcular recargo basado en el estado civil y edad del cónyuge
        if (estadoCivil.equals("casado")) {
            if (edadConyuge == null || edadConyuge < 18) {
                System.out.println("El cónyuge no es elegible para el seguro.");
                return -1;
            }
            if (edadConyuge >= 18 && edadConyuge <= 24) {
                recargoTotal += precioBase * 0.1;
            } else if (edadConyuge >= 25 && edadConyuge <= 49) {
                recargoTotal += precioBase * 0.2;
            } else {
                recargoTotal += precioBase * 0.3;
            }
        }

        // Calcular recargo por cantidad de hijos
        recargoTotal += cantidadHijos * (precioBase * 0.2);

        // Calcular precio total de la cotización
        double precioTotal = precioBase + recargoTotal;

        return precioTotal;
    }

    public static void main(String[] args) {
        // Ejemplo de uso:
        double precioCotizacion = calcularCotizacion(23, "casado", 26, 2, 2000);
        if (precioCotizacion != -1) {
            System.out.println("Precio total de la cotización: " + precioCotizacion);
        }
    }
}
