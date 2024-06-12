# Lista encadeada/Ligada

* Estrutura de dados dinâmica, linear formada por nós, cada nó armazena uma informação e referencia o próximo nó.

## Vantagens
1. Estrutura dinâmica;
2. Utilização de memória;
3. Utilizado na construção de outras estruturas;

## Desvantagens
1. Acesso sequencial;
2. Difuculdade de implementação;

## Principais operações
1. Adicionar item:
    * No início (prepend)
    * No fim (append)
    * Em determinada posição (insert)
2. Ler item
    * No início (getHead)
    * No fim (getTail)
    * Em determinada posição (get)
3. Remover item
    * No início (removeFirst)
    * No fim (removeLast)
    * Em determinada posição (delete)
4. Imprimir

5. Operações "opcionais"
    * Tamanho atual (getLenght)
    * Está vazia? (isEmpty)
    * Esvaziar Lista (makeEmpty)

~~~JAVA
public class LinkedList {

    private Node head;
    private Node tail;
    private int length;

    class Node{
        String data;
        Node next;

        Node(String data){
            this.data = data;
        }
    }

    public LinkedList(String data){
        this.length = 1;
        Node newNode = new Node(data);
        this.head = newNode;
        this.tail = newNode;
    }

    public void getHead(){
        if(this.head == null){
            System.err.println("Lista vazia");
        }else {
            System.out.println("Head: " + this.head.data);
        }
    }

    public void getTail(){
        if(this.head == null){
            System.err.println("Lista vazia");
        }else {
            System.out.println("Tail: " + this.tail.data);
        }
    }

    public void getLength(){
        System.out.println("Length: " + this.length);
    }

    public void makeEmpty(){
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    public void print(){
        System.out.println("##########");
        Node temp = this.head;
        while(temp != null) {
            System.out.println(temp.data);
            temp = temp.next;
        }
        System.out.println("##########");
    }

    public void append(String data){
        Node newNode = new Node(data);
        if(length == 0){
            this.head = newNode;
            this.tail = newNode;
        } else{
            this.tail.next = newNode;
            this.tail = newNode;
        }
        length++;
    }

    public Node removeLast(){
        if (length == 0) return null;
        Node pre = this.head;
        Node temp = null;
        while(pre.next != tail){
            pre = pre.next;
        }

        temp = tail;
        tail = pre;
        tail.next = null;

        length--;
        if(length == 0){
            this.tail = null;
            this.head = null;
        }

        return temp;
    }

    public void prepend(String dataNode){
        Node newNode = new Node(dataNode);
        if(this.length == 0){
            this.head = newNode;
            this.tail = newNode;
        }else {
            newNode.next = this.head;
            this.head = newNode;
        }
            length++;
    }

    public Node removeFirst(){

        if(length == 0) return null;

        Node temp = this.head;
        this.head = this.head.next;
        temp.next = null;
        length --;

        if(length == 0){
            this.head = null;
            this.tail = null;
        }
        return temp;
    }

    public Node get(int index){
        if(index < 0 | index >= this.length) return null;
        Node temp = this.head;

        for(int i = 0; i < index; i++){
            temp = temp.next;
        }
        return temp;
    }

    public boolean insert(int index, String newData){

        if(index < 0 | index > this.length) return false;

        if(index == 0){
            prepend(newData);
            return true;
        }

        if (index == length){
            append(newData);
            return true;
        }

        Node newNode = new Node(newData);
        Node temp = get(index -1);
        newNode.next = temp.next;
        temp.next = newNode;
        length ++;
        return true;
    }

    public boolean set(int index, String newData){
        Node temp = get(index);
        if(temp != null) {
            temp.data = newData;
            return true;
        }
        return false;
    }

    public Node remove(int index){
        if(index < 0)
            return null;
        if (index == 0)
            return removeFirst();
        if (index == length - 1)
            return removeLast();

        Node prev = get(index -1);
        Node temp = prev.next;

        prev.next = temp.next;
        temp.next = null;
        length --;

        return temp;
    }

}
~~~


# Arvores Binárias

~~~JAVA
package dataStructure;

import java.util.LinkedList;
import java.util.Queue;

public class Tree {

    public Node root;

    public static class Node {

        public int value;
        public Node left;
        public Node right;

        public Node(int value){
            this.value = value;
        }

        public boolean isLeaf(){
            return this.left == null & this.right == null;
        }
    }

    public void insert(int value){
        if(root == null)
            root = new Node(value);
        else{
            Node newNode = new Node(value);
            Queue<Node> queue = new LinkedList<>();
            queue.add(root);
            while (!queue.isEmpty()){
                Node currentNode = queue.remove();

                if(currentNode.left == null) {
                    currentNode.left = newNode;
                    break;
                }else
                    queue.add(currentNode.left);

                if(currentNode.right == null) {
                    currentNode.right = newNode;
                    break;
                }
                else
                    queue.add(currentNode.right);
            }
        }
    }

    public void preOrder(){
        preOrder(this.root);
    }

    private void preOrder(final Node node){
        //Raiz -> Esquerda -> Direita -> igual a busca em profundidade
        if(node == null)
            return;

        System.out.println(node.value);
        preOrder(node.left);
        preOrder(node.right);
    }

    public void inOrder(){
        inOrder(this.root);
    }

    private void inOrder(final Node node){
        //Esquerda -> Raiz -> Direita
        if(node == null)
            return;

        inOrder(node.left);
        System.out.println(node.value);
        inOrder(node.right);
    }

    public void posOrder(){
        posOrder(this.root);
    }

    private void posOrder(final Node node){
        //Esquerda -> Raiz -> Direita
        if(node == null)
            return;

        posOrder(node.left);
        posOrder(node.right);
        System.out.println(node.value);
    }

    public void BFS(){
        //Busca em Largura
        if(root == null)
            return;
        Queue<Node> queue = new LinkedList<>();
        queue.add(root);
        while (!queue.isEmpty()){
            Node node = queue.remove();
            if(node.left != null)
                queue.add(node.left);
            if(node.right != null)
                queue.add(node.right);

            System.out.println(node.value);
        }
    }
}
~~~

## Arvore binária de busca
- Os elementos menores ou iguais, ficam do lado esquerdo do nó, os valores maiores ficam do lado direito.  
- Otimiza as buscas;
~~~Java
//Binary search tree
public class BST {

    public Node root;

    public static class Node{
        public int value;
        public Node left;
        public Node right;

        public Node(int value){
            this.value = value;
        }
    }

    public void insert(int value){
        if(root == null)
            root = new Node(value);
        else
            insert(this.root, value);
    }

    private void insert(Node root, int value) {
        if(root == null)
            return;
        if(value == root.value)
            return;
        if(value > root.value) {
            if (root.right == null)
                root.right = new Node(value);
            else
                insert(root.right, value);
        }else{
            if(root.left == null)
                root.left = new Node(value);
            else
                insert(root.left, value);
        }
    }

    public void inOrder(){
        inOrder(root);
    }

    private void inOrder(Node node){
        if(node == null)
            return;

        inOrder(node.left);
        System.out.println(node.value);
        inOrder(node.right);
    }

    public boolean contains(int value){
        return contains(root, value);
    }

    private boolean contains (Node node, int value){
        if(node == null)
            return false;
        else if(node.value == value)
            return true;

        else if (value > node.value)
            return contains(node.right, value);
        else
            return contains(node.left, value);
    }

    public int minValue(Node currentNode){
        while(currentNode.left != null){
            currentNode = currentNode.left;
        }
        return currentNode.value;
    }

    public void deleteNode(int value){
        root = deleteNode(root, value);
    }

    private Node deleteNode(Node node, int value){
        if(root == null)
            return null;
        else if(value < node.value)
            node.left = deleteNode(node.left, value);
        else if(value > node.value)
            node.right = deleteNode(node.right, value);
        else
            if(node.left == null & node.right == null)
                return null;
            else if (node.left == null)
                return node.right;
            else if (node.right == null)
                return node.left;
            else{
                int minvalue = minValue(node.right);
                node.value = minvalue;
                node.right = deleteNode(node.right, minvalue);
            }
        return node;
    }
}
~~~
