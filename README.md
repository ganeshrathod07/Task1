# Task1
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    private static final int MAX_ATTEMPTS = 10;
    private static final int MAX_NUMBER = 100;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int roundsWon = 0;

        System.out.println("Welcome to the Number Guessing Game!");

        do {
            int numberToGuess = random.nextInt(MAX_NUMBER) + 1;
            int attempts = 0;

            System.out.println("I've picked a number between 1 and " + MAX_NUMBER + ". Can you guess it?");

            while (attempts < MAX_ATTEMPTS) {
                System.out.print("Enter your guess: ");
                int userGuess;

                if (scanner.hasNextInt()) {
                    userGuess = scanner.nextInt();
                } else {
                    System.out.println("Invalid input. Please enter a number.");
                    scanner.next(); // consume invalid input
                    continue;
                }

                attempts++;

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You've guessed the correct number!");
                    roundsWon++;
                    break; // Exit the loop when guessed correctly
                } else if (userGuess < numberToGuess) {
                    System.out.println("Your guess is too low.");
                } else {
                    System.out.println("Your guess is too high.");
                }

                System.out.println("Attempts remaining: " + (MAX_ATTEMPTS - attempts));
            }

            if (attempts == MAX_ATTEMPTS) {
                System.out.println("Sorry, you've run out of attempts. The correct number was " + numberToGuess);
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainInput = scanner.next();
            playAgain = playAgainInput.equalsIgnoreCase("yes");
        } while (playAgain);

        System.out.println("Game over! You won " + roundsWon + " round(s).");
        scanner.close();
    }
}
