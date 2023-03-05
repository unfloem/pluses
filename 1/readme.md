#### 1. Вывести на экран ФИО, Номер группы и факультет.
```
setlocale(LC_ALL, "Russian");

cout << "Константинов Константин Константинович" << endl;
cout << 303 << endl;
cout << "ФМФ" << endl;
```

#### 2. Получить N и вывести N символов @, если N % 5 == 0 или %, если N % 5 != 0.
```
int n;
cout << "N: ";
cin >> n;

char symbol = n % 5 == 0 ? '@' : '%';

while (n > 0)
{
  cout << symbol;
  n--;
}
```

#### 3. Прочитать x и y и вывести x^y.
```
setlocale(LC_ALL, "Russian");

int basis;
cout << "Основание степени (x): ";
cin >> basis;
int currentValue = basis;

int degree;
cout << "Показатель степени (y): ";
cin >> degree;

while (degree > 1)
{
  currentValue = currentValue * basis;
  degree--;
}

cout << currentValue;
```

#### 4. Прочитать N чисел и вывести минимальное из них.
```
setlocale(LC_ALL, "Russian");

int n, min, current;

cout << "N: ";
cin >> n;

if (n <= 0)
{
  return 0;
}

cout << "1 число: ";
cin >> min;

for (int i = 2; i <= n; i++)
{
  cout << i << " число: ";
  cin >> current;

  if (current < min)
  {
    min = current;
  }
}

cout << "Минимальное: " << min;
```

#### 5. Прочитать множество чисел и вывести число с минимальных остатком от деления на 101.
```
setlocale(LC_ALL, "Russian");

int n, min, current;

cout << "N: ";
cin >> n;

if (n <= 0)
{
  return 0;
}

cout << "1 число: ";
cin >> min;

for (int i = 2; i <= n; i++)
{
  cout << i << " число: ";
  cin >> current;

  if (current % 101 < min % 101)
  {
    min = current;
  }
}

cout << "Минимальное: " << min;
```

#### 6. Прочитать множество чисел и найти наибольшее количество идущих рядом монотонно возрастающих чисел.
```
int numbersCount;
cout << "Количество чисел: ";
cin >> numbersCount;

if (numbersCount <= 0)
{
    return 0;
}

int mainCounter = 1;  // Количество идущих подряд монотонно возрастающих чисел
int counter = 1;  // Текущее количество идущих подряд монотонно возрастающих чисел
int current;  // Текущее введённое число
int prevoius;  // Предыдущее ведённое число

cout << "Введите числа, каждое с новой строки" << endl;
cin >> prevoius;
numbersCount--;

while (numbersCount > 0)
{
    cin >> current;

    counter = current > prevoius
        ? counter + 1
        : 0;

    if (counter > mainCounter)
    {
        mainCounter = counter;
    }

    numbersCount--;
}

cout << "Ответ: " << mainCounter;
```
