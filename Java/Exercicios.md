# Método usado para verificar a validade de uma expressao
~~~Java
public static boolean solve(String expression){
    Set<Character> openSymbols = Set.of('(', '[', '{');
    Set<Character> closeSymbols = Set.of(')', ']', '}');
    Stack<Character> stack = new Stack<>();

    for(char c: expression.toCharArray()){
        if(openSymbols.contains(c))
            stack.push(c);
        if (closeSymbols.contains(c)) {
            if (stack.isEmpty())
                return false;

            var open = stack.pop();
            if (open == '(' & c != ')')
                return false;
            if (open == '[' & c != ']')
                return false;
            if (open == '{' & c != '}')
                return false;

        }
    }
    return stack.isEmpty();
}
~~~

# Invertendo `K` elementos de uma fila
- [1, 2, 3, 4, 5] -> K = 2 -> [2, 1, 3, 4, 5]
~~~java
public static Queue<Integer> reverseFirstK(Queue<Integer> queue, int k){
    solveQueue(queue, k);
    int n = queue.size() - k;
    while (n-- > 0){
        int element = queue.remove();
        queue.add(element);
    }

    return queue;
}

private static void solveQueue(Queue<Integer> queue, int k) {
    if(k == 0)
        return;
    int element = queue.remove();
    solveQueue(queue, k-1);
    queue.add(element);
}
~~~

# Identificar o maior valor em cada nível da arvore binária
