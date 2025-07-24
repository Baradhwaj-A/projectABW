import java.util.Scanner;
public class sum {

    public static void main(String[] args) {
        Scanner scanner=new Scanner(System.in);
         System.out.print("Enter a number (must be 3 or greater): ");
        int targetSum = scanner.nextInt();
        
        if (targetSum < 3) {
            System.out.println("Error: Input must be 3 or greater.");
            return;
        }
        
        // Generate Fibonacci numbers until the largest number is greater than or equal to targetSum
        int[] fib = new int[targetSum + 1];
        fib[0] = 0;
        fib[1] = 1;      
        int count = 2;
        while (true) {
            int nextFib = fib[count - 1] + fib[count - 2];
            if (nextFib > targetSum) {
                break;
            }
            fib[count] = nextFib;
            count++;
        }
        // Now find three Fibonacci numbers that sum to targetSum
        boolean found = false;
        for (int i = 0; i < count; i++) {
            for (int j = i; j < count; j++) {
                for (int k = j; k < count; k++) {
                    if (fib[i] + fib[j] + fib[k] == targetSum) {
                        System.out.printf("%d = %d + %d + %d\n", targetSum, fib[i], fib[j], fib[k]);
                        found = true;
                    }
                }
            }
        }
        if (!found) {
            System.out.println("No three Fibonacci numbers found that sum to " + targetSum);
        }
    }
}



