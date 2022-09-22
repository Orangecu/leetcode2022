
```java

void dfs(int[] coins, int level, int left_balance, int[] solution, List<int[]> result) {
    if (level == coins.length - 1) {
        sol[level] = left_balance;
        int[] newSolution = new int[solution.length];
        for (i = 0; i < solution.length; i++) {
            newSolution[i] = solution[i];
        }
        result.add(newSolution);
        return;
    }
    int num = left_balance / coins[level] + 1;
    for (int i = 0; i < num; i++) {
        solution[level] = i;
        dfs(coins, level + 1, left_balance - i * coins[level], solution, result);
    }
}

```
