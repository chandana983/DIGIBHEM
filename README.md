import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        boolean playAgain = true;

        System.out.println("Welcome to the Number Guessing Game!");

        while (playAgain) {
            int rangeStart = 1;
            int rangeEnd = 100;
            int numberToGuess = random.nextInt(rangeEnd - rangeStart + 1) + rangeStart;
            int attempts = 5;
            boolean hasWon = false;

            System.out.println("I have selected a number between " + rangeStart + " and " + rangeEnd + ".");
            System.out.println("You have " + attempts + " attempts to guess the number.");

            for (int i = 0; i < attempts; i++) {
                System.out.print("Enter your guess: ");
                int playerGuess = scanner.nextInt();

                if (playerGuess == numberToGuess) {
                    System.out.println("Congratulations! You've guessed the correct number.");
                    hasWon = true;
                    break;
                } else if (playerGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }

                System.out.println("Attempts remaining: " + (attempts - i - 1));
            }

            if (!hasWon) {
                System.out.println("Sorry, you've run out of attempts. The correct number was: " + numberToGuess);
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("Thanks for playing!");
        scanner.close();
    }
}
