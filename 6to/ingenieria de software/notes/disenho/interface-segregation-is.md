# Principio de Segregación de Interfaces

_Original: https://www.danielsanmartin.cl/blog/interface-segregation-is/_


Al igual que el principio de Responsabilidad Única, este principio es una aplicación de la idea de cohesión. Más específicamente, es un caso particular del Principio de Responsabilidad Única, pero enfocado en las interfaces. El principio establece que las interfaces deben ser pequeñas, cohesionadas y, lo más importante, específicas para cada tipo de cliente. El objetivo es evitar que los clientes dependan de interfaces con métodos que no van a utilizar. Para evitar esto, dos o más interfaces específicas pueden, por ejemplo, sustituir a una interfaz de propósito general.

Se produce una violación del principio, por ejemplo, cuando una interfaz tiene dos conjuntos de métodos $M_x$ y $M_y$. El primer conjunto es utilizado por los clientes $C_x$ (que no usan los métodos $M_y$). Inversamente, los métodos $M_y$ son utilizados solo por los clientes $C_y$ (que no usan los métodos $M_x$). En consecuencia, esta interfaz debería dividirse en dos interfaces más pequeñas y específicas: una interfaz que contenga solo los métodos $M_x$ y otra que contenga solo los métodos $M_y$.

Ejemplo: Supongamos una interfaz ‘‘Funcionario’’ con los siguientes métodos: (1) retornar salario, (2) retornar contribución mensual al FGTS (Fondo de Garantía por Tiempo de Servicio) y (3) retornar SIAPE (es decir, el número de matrícula de todo funcionario público). Esta interfaz viola el Principio de Segregación de Interfaces, ya que solo los empleados de empresas privadas, contratados bajo el régimen de CLT, tienen una cuenta en el FGTS. Por otro lado, solo los empleados públicos tienen una matrícula en el SIAPE.

```java
interface Funcionario {

  double getSalario();

  double getFGTS();// solo funcionários CLT

  int getSIAPE();// solo funcionários públicos

  ...
}
```

Una alternativa que atiende el Principio de Segregación de Interfaces consiste en crear interfaces específicas (‘‘FuncionarioCLT’’ e ‘‘FuncionarioPublico’’) que extiendadn la interfaz genérica (‘‘Funcionario’’).

```java
interface Funcionario {
  double getSalario();
  ...
}

interface FuncionarioCLT extends Funcionario {
  double getFGTS();
  ...
}

interface FuncionarioPublico extends Funcionario {
  int getSIAPE();
  ...
}
```

[← Volver](index.md)