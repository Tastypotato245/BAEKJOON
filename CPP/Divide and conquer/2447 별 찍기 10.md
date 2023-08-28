```cpp
#include <iostream>

using namespace std;

bool arr[10000][10000] = {false,};

void fill(int a, int b, int n) {

    for (int i = 0; i < n;i++) {
        for (int j = 0; j < n; j++) {
            arr[a + i][b + j] = arr[i][j];
        }
    }
}

void solve(int n) {
    if (n==1) {
        arr[0][0] = true;
        return;
    }
    solve(n/3);
    int i, j;
    for (i = 0; i < 3;i++) {
        for (j = 0; j < 3;j++) {
            if (i==1&&j==1) {
                continue;
            }
            fill(i * (n / 3), j * (n / 3), n/3);
        }
    }
}


int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    int N, i, j;

    cin >> N;
    solve(N);
    for (i = 0; i < N;i++) {
        for (j = 0; j < N;j++) {
            //cout << arr[i][j];
            cout << (arr[i][j] ? '*' : ' ');
        }
        cout << "\n";
    }

    return 0;
}
```



```cpp
#include <iostream>
using namespace std;

void drawStar(int n, int x, int y) {
    if ((x / n) % 3 == 1 && (y / n) % 3 == 1) {
        cout << ' ';
    }
    else {
        if (n / 3 == 0) {
            cout << '*';
        }
        else {
            drawStar(n / 3, x, y);
        }
    }
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    int N;
    cin >> N;

    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            drawStar(N, i, j);
        }
        cout << '\n';
    }

    return 0;
}

```