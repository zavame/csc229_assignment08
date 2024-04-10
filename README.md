import java.util.Scanner;

class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class SinglyLinkedList {
    Node head;

    SinglyLinkedList() {
        head = null;
    }

    void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) {
                temp = temp.next;
            }
            temp.next = newNode;
        }
    }
}

public class PrimeLinkedList {
    // Function to see if a number is prime
    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i = i + 6) {
            if (n % i == 0 || n % (i + 2) == 0)
                return false;
        }
        return true;
    }

    // Function to see if a number contains the number 3
    public static boolean containsThree(int n) {
        while (n > 0) {
            if (n % 10 == 3) {
                return true;
            }
            n /= 10;
        }
        return false;
    }

    // The calculation of the sum of elements in a linked list
    public static int sumLinkedList(SinglyLinkedList list) {
        int sum = 0;
        Node current = list.head;
        while (current != null) {
            sum += current.data;
            current = current.next;
        }
        return sum;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number (n < 1000000): ");
        int n = scanner.nextInt();
        
        // The linked lists
        SinglyLinkedList primeList = new SinglyLinkedList(); 
        SinglyLinkedList primeWithThreeList = new SinglyLinkedList(); 

        for (int i = 0; i <= n; i++) {
            if (isPrime(i)) {
                primeList.insert(i);
                if (containsThree(i)) {
                    primeWithThreeList.insert(i);
                }
            }
        }

        // Printing the prime numbers
        System.out.println("Prime numbers:");
        Node current = primeList.head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }

        // Printing prime numbers with number 3
        System.out.println("\nPrime numbers with digit 3:");
        current = primeWithThreeList.head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }

        // Calculating and printing the sum of prime numbers with number 3
        int sum = sumLinkedList(primeWithThreeList);
        System.out.println("\nSum of prime numbers with digit 3: " + sum);
    }
}
