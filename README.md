# 17.AFA-While

## 5.2.3 Loops

### `while` loop

The simplest form of a loop is the so-called `while`-loop. It looks like this:

```java
while (condition) {
    // ...
    if (cond1) break; // optional
    // ...
    if (cond2) continue; // optional
    // ...
}
```

where `condition` is an expression yielding a Boolean value (`true` or `false`). The loop is executed as follows:

1. `condition` is evaluated, and if it is false, the flow of control jumps out of the loop;
2. if `condition` evaluates to true, the body of the loop (everything inside the block) is executed and then the flow of control goes back to item 1.

Inside the loop, you can (but do not have to) use `break` and `continue` instructions. When `break` is executed, the flow of control goes out of the loop immediately. When `continue` is encountered, the current iteration of the loop is considered completed, and we go back to the next iteration (so the condition is checked again).

The following loop will print square roots of integers read from the keyboard, but only of positive ones; the loop ends when the user enters 0:

```java
Scanner scan = new Scanner(System.in);
while (true) {
    int n = scan.nextInt();
    if (n == 0) break;
    if (n < 0) {
        System.out.println("Negative - try again!");
        continue;
    }
    System.out.println("square root of " + n + " is " + Math.sqrt((double)(n)));
}
```

Note that assignment is an expression — it has a value. Therefore, we could have rewritten the above snippet as:

```java
Scanner scan = new Scanner(System.in);
int n;
while ((n = scan.nextInt()) != 0) {
    if (n < 0) {
        System.out.println("Negative - try again!");
        continue;
    }
    System.out.println("square root of " + n + " is " + Math.sqrt((double)(n)));
}
```

In the following example, we read numbers and print the information if they are prime or not:

## Listing 17 AFA-While/Prime.java Page 37

```java
import java.util.Scanner;

public class Prime {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        while (true) {
            System.out.print("Enter natural number (0 to exit) -> ");
            int n = scan.nextInt();

            if (n == 0) break;

            boolean prime = true;

            if (n == 1) {
                System.out.println("Number 1 is neither prime nor composite");
                continue;
            } else if (n > 2 && n % 2 == 0) {
                prime = false;
            } else {
                int p = 3;
                while (p * p <= n) {
                    if (n % p == 0) {
                        prime = false;
                        break;
                    }
                    p += 2;
                }
            }
            System.out.println("Number " + n + " is " + (prime ? "prime" : "composite"));
        }
        scan.close();
    }
}
```
