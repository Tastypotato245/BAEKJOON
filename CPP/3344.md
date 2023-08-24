```cpp
#include <cstdio>

int main()
{
	int n;
	bool isOdd = false;
	scanf("%d", &n);

	if (n % 2)	isOdd = true;

	if ((!isOdd && n % 6 != 2) || (isOdd && (n - 1) % 6 != 2))
	{
		if (isOdd)	n--;
		for (int i = 1; i <= n / 2; i++)
			printf("%d\n", 2 * i);
		for (int i = 1; i <= n / 2; i++)
			printf("%d\n", 2 * i - 1);
		if (isOdd)	printf("%d\n", n + 1);
	}

	else if ((!isOdd && n / 6 != 0) || (isOdd && (n - 1) / 6 != 2))
	{
		if (isOdd)	n--;
		for (int i = 1; i <= n / 2; i++)
			printf("%d\n", 1 + (2 * i + n / 2 - 3) % n);
		for (int i = n / 2; i > 0; i--)
			printf("%d\n", n - (2 * i + n / 2 - 3) % n);
		if (isOdd)	printf("%d\n", n + 1);
	}

	return 0;
}
```