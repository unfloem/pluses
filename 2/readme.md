## Семинар 2
#### 1. Написать функцию проверяющую число на простоту. Функция должна иметь сигнатуру:
bool is_prime(unsigned long long value);
```
bool is_prime(unsigned long long value)
{
    for (unsigned long long i = value / 2; i > 1; i--)
    {
        if (value % i == 0)
        {
            return false;
        }
    }
    
    return true;
}

int main()
{
    string result = is_prime(53) ? "Простое" : "Не простое";
    cout << result;
}
```

#### 2. Написать функцию читающую целое число из "замусоренного" не числовыми символами cin. Гарантируется, что в cin будет передано число, помещающееся в unsigned long long и оно будет единственно.
unsigned long long read_int_value();<br />
На входных данных вида: weqe123sad2err34 функция должна вернуть: 123234.<br />
*(для желающих) Добавить поддержку знаковых чисел. 
```
long double read_int_value()
{
	string input;
	cout << "Строка: ";
	cin >> input;

	long double result = 0;
	bool wasComma = false;  // Была ли запятая во вводе
	int decimalPlaces = 0;

	for (char symbol : input)
	{
		if (!wasComma && (symbol == 44 || symbol == 46))
		{
			wasComma = true;
		}
		else if (symbol >= 48 && symbol <= 57)
		{
			result = result * 10 + symbol - '0';

			if (wasComma)
			{
				decimalPlaces++;
			}
		}
	}

	while (decimalPlaces > 0)
	{
		result /= 10;
		decimalPlaces--;
	}

	return result;
}

int main()
{
	setlocale(LC_ALL, "Russian");
	long double result = read_int_value();
	printf("%f", result);
}
```

#### 3. Написать функцию возвращающую новое простое число (начиная с 2) при каждом своём вызове. 
unsigned long long next_prime();<br />
Последовательность вызовов<br />
auto a = next_prime();<br />
auto b = next_prime();<br />
auto c = next_prime();<br />
должна записать в переменные a, b и c значения 2 3 и 5 соответственно.
```
unsigned long long currentSimple = 1;

// Является ли текущее значение currentSimple простым числом
bool current_is_prime()
{
    for (unsigned long long i = currentSimple / 2; i > 1; i--)
    {
        if (currentSimple % i == 0)
        {
            return false;
        }
    }

    return true;
}

unsigned long long next_prime()
{
    do
    {
        currentSimple++;
    } while (!current_is_prime());

    return currentSimple;
}

int main()
{
    cout << next_prime() << endl;
    cout << next_prime() << endl;
    cout << next_prime() << endl;
}
```

#### 4. В дополнение к задаче 3 сделать функцию которая будет перезапускать генерацию простых чисел функцией next_prime(); После вызова требуемой функции next_prime() начинает возвращать значения по новой (2 3 5 и т. д.). 
void reset_prime();
```
void reset_prime()
{
    currentSimple = 1;
}
```

## --- рекурсия --- 

#### 5. Написать функцию вычисляющую факториал числа N. N < 20 
unsigned long long factorial(int N);
```
unsigned long long factorial(int N)
{
	if (N == 1)
	{
		return 1;
	}

	return N * factorial(N - 1);
}

int main()
{
	setlocale(LC_ALL, "Russian");

	int N;
	cout << "Число: ";
	cin >> N;
 
	cout << factorial(N);
}
```
