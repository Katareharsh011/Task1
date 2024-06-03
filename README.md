 import java.util.Scanner;
import java.util.Random;
class Task1{

        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            Random random = new Random();

            int minRange = 1;
            int maxRange = 100;
            int attemptsLimit = 5;
            int score = 0;

            System.out.println("Welcome to Guess the Number!");
            System.out.println("I've selected a random number between " + minRange + " and " + maxRange + ". Try to guess it!");

            boolean playAgain = true;
            while (playAgain) {
                int randomNumber = random.nextInt(maxRange - minRange + 1) + minRange;
                int attempts = 0;
                boolean guessedCorrectly = false;

                while (attempts < attemptsLimit) {
                    System.out.print("Enter your guess (between " + minRange + " and " + maxRange + "): ");
                    int guess = scanner.nextInt();
                    attempts++;

                    if (guess == randomNumber) {
                        System.out.println("Congratulations! You guessed the number correctly in " + attempts + " attempts.");
                        score++;
                        guessedCorrectly = true;
                        break;
                    } else if (guess < randomNumber) {
                        System.out.println("Too low! Try again.");
                    } else {
                        System.out.println("Too high! Try again.");
                    }
                }

                if (!guessedCorrectly) {
                    System.out.println("Sorry, you've run out of attempts. The correct number was: " + randomNumber);
                }

                System.out.print("Do you want to play again? (yes/no): ");
                String playAgainResponse = scanner.next();
                if (!playAgainResponse.equalsIgnoreCase("yes")) {
                    playAgain = false;
                }
            }

            System.out.println("Game over! Your final score is: " + score);
            scanner.close();
        }
    }
