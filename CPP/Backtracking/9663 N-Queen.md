```cpp
#include <stdio.h>

int n;
short queens[15];

short	ex08_check_queen(short y, short x)
{
    short	i;

    i = 0;
    while (i < y)
    {
        if (x == queens[i] || x - queens[i] == y - i || x - queens[i] == i - y)
            return (0);
        i++;
    }
    return (1);
}

void	ex08_recur_ten_queens(short y, int *cnt)
{
    short	x;

    if (y == n)
    {
        (*cnt)++;
        return ;
    }
    x = -1;
    while (++x < n)
    {
        if (ex08_check_queen(y, x))
        {
            queens[y] = x;
            ex08_recur_ten_queens(y + 1, cnt);
        }
    }
}

int	ft_ten_queens_puzzle(void)
{
    short	i;
    int	cnt;

    i = -1;
    while (++i < n)
        queens[i] = 0;
    cnt = 0;
    ex08_recur_ten_queens(0, &cnt);
    return (cnt);
}

int main(void)
{
    scanf("%d", &n);
    printf("%d", ft_ten_queens_puzzle());
    return (0);
}
```

#### 참고
[[1799 비숍]]
[[3344 N-Queen]]