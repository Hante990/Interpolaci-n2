# Metodos_Numericos
Realizado por:
  <li>Diego Alonso Fernández Delagadillo</li>
 
<h2 align = "center"> <font color = "darkorange" size = "+6"  font face = "bauhaus 93">  Indice </font> </h2>
<header> <font color = "red" size="+1" font face = "aharoni">
                <nav class="navegacion">
                    <ul class="Indice">
                       <li> <a href="#Descripción del Problemario"> Descripción del Problemario </a> <br> </li>
                            </ul>
     <li> <a href="#Métodos numéricos para encontrar las raíces de ecuaciones que se encuentran en nuestro repositorio"> Metodos de interpolación </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Método de Bisección"> Interpolación lineal (5 ejemplos). </a> </li>
                                <li> <a href="#Método de la Falsa Posición"> Interpolación cuadratica (1 ejemplo). </a> </li>
                                <li> <a href="#Método de la Secante"> Interpolación langrage (5 ejemplos). </a> </li> 
                                <li> <a href="#Método de Newton-Raphson"> Interpolación de newton (5 ejemplos). </a> </li> 
                            </ul>
                    </ul>
                </nav>
            </font> </header>

# Descripción
En este documento vamos a ver varios ejercicios sobre los distintos metodos de interpolación como lo son:
  <li>1.-Interpolación lineal</li>
  <li>2.-Interpolación cuadratica</li>
  <li>3.-Interpolación langrage</li>
  <li>4.-Interpolación de newton</li>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

<h2 align = "center"> <font font face = "forte">  1. Interpolación lineal </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación lineal es un procedimiento numérico que permite aproximar valores desconocidos dentro de un intervalo conocido, asumiendo una relación lineal entre los puntos extremos. Este método es ampliamente utilizado en diversas áreas, como la ingeniería, la física y las matemáticas, para estimar valores intermedios de manera rápida y eficiente.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

    public class Ejercicio4 {
    public static double interpolate(double[] x, double[] y, double xTarget) {
        int n = x.length;
        double yTarget = 0;

        int i = 0;
        while (i < n - 1 && x[i] < xTarget) {
            i++;
        }

        if (i == 0) {
            yTarget = y[0];
        } else if (i == n - 1) {
            yTarget = y[n - 1];
        } else {
            double x0 = x[i - 1];
            double x1 = x[i];
            double y0 = y[i - 1];
            double y1 = y[i];

            double m = (y1 - y0) / (x1 - x0);
            double b = y0 - m * x0;
            yTarget = m * xTarget + b;
        }

        return yTarget;
    }

    public static void main(String[] args) {
    double[] x = {0.8, 1.6, 2.8, 3.2, 4.6};
    double[] y = {1.2, 3.2, 5.2, 7.2, 9.2};
    double xTarget = 2.0;
    double yTarget = interpolate(x, y, xTarget);
    System.out.println("El valor de y para x = " + xTarget + " es " + yTarget);
     }
    }

  ![Lineal](https://github.com/Hante990/Interpolaci-n2/assets/107586879/0037a026-e06c-45ce-8827-166931a2d22e)

<h2 align = "center"> <font font face = "forte">  2.- Interpolación cuadratica </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación cuadrática es una herramienta útil en la aproximación de funciones suaves y en la predicción de valores intermedios entre puntos conocidos. Sin embargo, es importante tener en cuenta que su uso debe ser cuidadoso para evitar problemas de sobreajuste y garantizar la validez de los resultados obtenidos.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

    public class Interpolacion_Cuadratica {

    public static void main(String[] args) {
        System.out.println("Solucion de ecuaciones cuadráticas");
        double a, b, c, x1, x2, producto, cuadrado, diferencia, raiz;
        Scanner scanner = new Scanner(System.in);

        System.out.println("Ingresa el coeficiente a");
        a = scanner.nextDouble();
        System.out.println("Ingresa el coeficiente b");
        b = scanner.nextDouble();
        System.out.println("Ingresa el coeficiente c");
        c = scanner.nextDouble();

        cuadrado = Math.pow(b, 2);
        producto = 4 * a * c;
        diferencia = cuadrado - producto;
        raiz = Math.sqrt(diferencia);

        x1 = (-b + raiz) / (2 * a);
        x2 = (-b - raiz) / (2 * a);

        System.out.println("La ecuacion es: " + a + "x^2 + " + b + "x + " + c + " = 0");
        System.out.println("Las raices son:");
        System.out.println("El valor de x1 es: " + x1);
        System.out.println("El valor de x2 es: " + x2);
      }
    } 
    
  ![Cua](https://github.com/Hante990/Interpolaci-n2/assets/107586879/88a62d83-01c4-421a-a441-54eec1a2f964)

<h2 align = "center"> <font font face = "forte">  3.- Interpolación langrage </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación de Lagrange es una técnica fundamental en el campo de los métodos numéricos y es ampliamente utilizada en diversas áreas, como la aproximación de funciones, la predicción de valores intermedios y la resolución de problemas matemáticos y computacionales que requieren el ajuste preciso de curvas a datos conocidos.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

      public class Ejercicio5 {
        public static double interpolate(double[] x, double[] y, double xTarget) {
        double result = 0;

        for (int i = 0; i < x.length; i++) {
            double term = y[i];
            for (int j = 0; j < x.length; j++) {
                if (j != i) {
                    term = term * (xTarget - x[j]) / (x[i] - x[j]);
                }
            }
            result += term;
        }

        return result;
    }

    public static void main(String[] args) {
        double[] x = {1.1, 2.2, 3.3, 4.4, 5.5};
    double[] y = {1.1, 3.1, 5.1, 7.1, 9.1};
    double xTarget = 4.5;

        double yTarget = interpolate(x, y, xTarget);

        System.out.println("El valor interpolado de y para x = " + xTarget + " es " + yTarget);
     }
    }

![langrage](https://github.com/Hante990/Interpolaci-n2/assets/107586879/dd6934bc-7890-444a-b38d-b6dcecd0ac99)
    
<h2 align = "center"> <font font face = "forte">  4.Interpolación de newton </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

La interpolación de Newton es una técnica ampliamente utilizada en el campo de los métodos numéricos y es fundamental para la aproximación de funciones suaves y la resolución de problemas matemáticos y computacionales que requieren el ajuste preciso de curvas a datos conocidos.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>
  
     public static double interpolate(double[] x, double[] y, double xTarget) {
        double yTarget = y[0];
        for (int i = 0; i < x.length - 1; i++) {
            if (x[i] <= xTarget && x[i + 1] > xTarget) {
                double h = x[i + 1] - x[i];
                double k = (xTarget - x[i]) / h;
                double y0 = y[i];
                double y1 = y[i + 1];
                yTarget = y0 + k * (y1 - y0);
                break;
            }
        }
        return yTarget;
    }

    public static void main(String[] args) {
        double[] x = {1.0, 2.0, 3.0, 4.0, 5.0};
        double[] y = {2.0, 4.0, 6.0, 8.0, 10.0};

        double xTarget = 2.5;

        double yTarget = interpolate(x, y, xTarget);

        System.out.println("El valor interpolado de y para x = " + xTarget + " es " + yTarget);
      }
    }

  ![Screenshot 2024-05-14 204415](https://github.com/Hante990/Interpolaci-n2/assets/107586879/a5a337a4-8aac-4526-8771-3b708eac912c)


