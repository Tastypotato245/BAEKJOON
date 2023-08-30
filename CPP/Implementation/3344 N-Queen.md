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


아래는 타임아웃 난 코드 (골드 n queen과 유사)

```cpp
#include <stdio.h>

int n;
int queens[99999];

void    print_queens()
{
    int i;

    i = -1;
    while (++i < n)
    {
        printf("%d\n", queens[i]);
    }
}

int	ex08_check_queen(int y, int x)
{
    int	i;

    i = 0;
    while (i < y)
    {
        if (x == queens[i] || x - queens[i] == y - i || x - queens[i] == i - y)
            return (0);
        i++;
    }
    return (1);
}

void	ex08_recur_ten_queens(int y, int *found)
{
    int	x;

    if (y == n)
    {
        print_queens();
        *found = 1;
        return ;
    }
    x = -1;
    while (++x < n && !(*found))
    {
        if (ex08_check_queen(y, x))
        {
            queens[y] = x;
            ex08_recur_ten_queens(y + 1, found);
        }
    }
}

void	ft_ten_queens_puzzle(void)
{
    int i;
    int found = 0;
    i = -1;
    while (++i < n)
        queens[i] = 0;
    ex08_recur_ten_queens(0, &found);
}

int main(void)
{
    scanf("%d", &n);
    ft_ten_queens_puzzle();
    return (0);
}
```

