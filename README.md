# Flow-Control-Challange
public class NumberSumCalculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input two numbers with a difference of at least 200
        System.out.print("Enter the first number: ");
        int num1 = scanner.nextInt();

        System.out.print("Enter the second number: ");
        int num2 = scanner.nextInt();

        // Check if the difference is less than 200
        if (Math.abs(num1 - num2) < 200) {
            System.out.println("The difference between the numbers must be at least 200.");
            return;
        }

        // Calculate the sums
        int sum4 = 0;
        int sum8 = 0;
        int sumNotEvenNotDivisibleBy5 = 0;

        // Simulate a switch statement to select the appropriate loop
        System.out.print("Enter loop type (for, while, do-while): ");
        String loopType = scanner.next().toLowerCase();

        switch (loopType) {
            case "for":
                sum4 = calculateSumWithFor(num1, num2, 4);
                sum8 = calculateSumWithFor(num1, num2, 8);
                sumNotEvenNotDivisibleBy5 = calculateSumNotEvenNotDivisibleBy5(num1, num2);
                break;
            default:
                System.out.println("Invalid loop type.");
                return;
        }

        // Display the sums
        System.out.println("Sum of even numbers divisible by 4: " + sum4);
        System.out.println("Sum of even numbers divisible by 8: " + sum8);
        System.out.println("Sum of not even numbers not divisible by 5: " + sumNotEvenNotDivisibleBy5);
    }

    private static int calculateSumWithFor(int num1, int num2, int divisor) {
        int sum = 0;
        for (int i = num1; i <= num2; i++) {
            if (i % 2 == 0 && i % divisor == 0) {
                sum += i;
            }
        }
        return sum;
    }

    private static int calculateSumWithWhile(int num1, int num2, int divisor) {
        int sum = 0;
        int currentNum = num1;

        while (currentNum <= num2) {
            if (currentNum % 2 == 0 && currentNum % divisor == 0) {
                sum += currentNum;
            }
            currentNum++;
        }

        return sum;
    }

    private static int calculateSumWithDoWhile(int num1, int num2, int divisor) {
        int sum = 0;
        int currentNum = num1;

        do {
            if (currentNum % 2 == 0 && currentNum % divisor == 0) {
                sum += currentNum;
            }
            currentNum++;
        } while (currentNum <= num2);

        return sum;
    }

    private static int calculateSumNotEvenNotDivisibleBy5(int num1, int num2) {
        int sum = 0;
        int currentNum = num1;

        do {
            if (currentNum % 2 != 0 && currentNum % 5 != 0) {
                sum += currentNum;
            }
            currentNum++;
        } while (currentNum <= num2);

        return sum;
    }
}
