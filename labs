L01_01 Составить программу вычисления Y:
Y = 3*x^2 – 1/x при x > 1,
Y = x + 5 при x <= -5
Напечатать:
При x = … функция вычисляется по формуле … Результат = …
double Y ;
double x ;


try
{
    Console.Write("Введите x:");
    x = Convert.ToDouble(Console.ReadLine());
}
catch (FormatException)
{
      Console.WriteLine("Неверный формат ввода. Введите числa");
      throw;
}

//мат блок
    if (x > 1)
    {
        Y = 3 * x * x - 1 / x;
        Console.WriteLine("При x = " + x + " функция вычисляется по формуле Y = 3*x^2 – 1/x " +
                          " Результат = " + Y);
    }
    if (x <= -5)
    {
        Y = x + 5;
        Console.WriteLine("При x = " + x + " функция вычисляется по формуле Y = x + 5 " + " Результат = " + Y);
    }
    if (-5 < x && x <= 1)
    {
        Console.WriteLine("Введённое число не входит в необходимые рамки");
    }


// L02_1. Исходные данные: расход каждого из К материалов на единицу каждой из М
// изготавливаемых деталей. Исходные данные определяются путем обращения к датчику случайных чисел. Задание:
// а. Для любого материала определить среднюю величину расхода.
// б. Для любой детали определить наиболее расходуемый материал.


base
объявляем необходимые материалы
 int K;
 int k;
 int M;
 int m;
 int sum1 = 0;
 int maxx = 0;
// используем конструкцию try catch,чтобы ловить ошибки на протяжении всего кода
 try
 {
     Console.Write("Введите кол-во видов материалов: ");
     K = Convert.ToInt32(Console.ReadLine()); 
     if (K <= 0)
     {
         Console.WriteLine("Неверный формат ввода. Введите числa числа больше 0");
     }
     
 }
 catch (FormatException)
 {
     Console.WriteLine("Неверный формат ввода. Введите числa");
     throw;
 }
 
 
 try
 {
     Console.Write("Введите кол-во видов деталей: ");
     M = Convert.ToInt32(Console.ReadLine());
     if (M <= 0)
     {
         Console.WriteLine("Неверный формат ввода. Введите числa числа больше 0");
     }

    
 }
 catch (FormatException)
 {
     Console.WriteLine("Неверный формат ввода. Введите числa");
     throw;
 }
 

     
     int[,] array = new int[K, M];
     Random random = new Random();
     for (int i = 0; i < K; i++)
     {
         for (int j = 0; j < M; j++)
         {
             array[i, j] = random.Next(100);
             Console.Write("{0,4}", array[i, j]);
         }
         Console.WriteLine();
     }
     // part a Для любого материала определить среднюю величину расхода.
 
 
    
 
 try
 {
     Console.Write("Введите номер материала: ");
     k = Convert.ToInt32(Console.ReadLine()) - 1;
     if (k <= 0)
     {
         Console.WriteLine("Неверный формат ввода. Введите числa числа больше 0");
     }
 }
 catch (FormatException)
 {
     Console.WriteLine("Неверный формат ввода. Введите числa");
     throw;
 }

 
     for (int c = 0; c < M ; c++)
     {
         sum1 = sum1 + array[k, c];
     }
     sum1 = sum1 / M;
     Console.Write("Cредняя величина расхода равна " + sum1 );    
     Console.WriteLine();
     // part b Для любой детали определить наиболее расходуемый материал.
 
 try
 {
     Console.Write("Введите номер детали: ");
     m = Convert.ToInt32(Console.ReadLine()) - 1; 
     if (m <= 0)
     {
         Console.WriteLine("Неверный формат ввода. Введите числa числа больше 0");
     }
 }
 catch (FormatException)
 {
     Console.WriteLine("Неверный формат ввода. Введите числa");
     throw;
 }

 
    
     for (int v = 0; v < K ; v++)
     {
         if (array[v, m] > maxx)
         {
             maxx = array[v, m];
         }
     }
     Console.Write("наиболее расходуемый материал для выбранной детали " + maxx );    
     Console.WriteLine();
 




ПРАКТИКА 1 ( калькулятор ) 
try
{
    double x;
    double y;
    string z;
    Console.Write("Введите первое число:");
    x = Convert.ToDouble(Console.ReadLine());
    Console.Write("Введите знак:");
    z = Console.ReadLine();
    Console.Write("Введите второе число:");
    y = Convert.ToDouble(Console.ReadLine());
    if (z == "+")
    {
        Console.Write(x + y);
    }
    if (z == "-")
    {
        Console.Write(x - y);
    }
    if (z == "%")
    {
        Console.Write(x % y);
    }
    if (z == "*")
    {
        Console.Write(x * y);
    }
}

catch (FormatException)
{
    Console.WriteLine("Неверный формат ввода. Введите числa");
    throw;
}
