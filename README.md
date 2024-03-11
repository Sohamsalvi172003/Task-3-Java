# Task-3-Java
import java.util.Scanner; 

  

class BankAccount { 

    private double balance; 

  

    public BankAccount(double balance) { 

        this.balance = balance; 

    } 

  

    public void deposit(double amount) { 

        if (amount > 0) { 

            this.balance += amount; 

            System.out.println("Deposit of $" + amount + " successful."); 

        } else { 

            System.out.println("Invalid amount for deposit."); 

        } 

    } 

  

    public void withdraw(double amount) { 

        if (amount > 0 && amount <= this.balance) { 

            this.balance -= amount; 

            System.out.println("Withdrawal of $" + amount + " successful."); 

        } else { 

            System.out.println("Insufficient funds or invalid amount for withdrawal."); 

        } 

    } 

  

    public void checkBalance() { 

        System.out.println("Current Balance: $" + this.balance); 

    } 

} 

  

class ATM { 

    private BankAccount bankAccount; 

    private Scanner scanner; 

  

    public ATM(BankAccount bankAccount) { 

        this.bankAccount = bankAccount; 

        this.scanner = new Scanner(System.in); 

    } 

  

    public void displayOptions() { 

        System.out.println("ATM Options:"); 

        System.out.println("1. Withdraw"); 

        System.out.println("2. Deposit"); 

        System.out.println("3. Check Balance"); 

        System.out.println("4. Exit"); 

    } 

  

    public void withdraw() { 

        System.out.print("Enter amount to withdraw: $"); 

        double amount = scanner.nextDouble(); 

        bankAccount.withdraw(amount); 

    } 

  

    public void deposit() { 

        System.out.print("Enter amount to deposit: $"); 

        double amount = scanner.nextDouble(); 

        bankAccount.deposit(amount); 

    } 

  

    public void checkBalance() { 

        bankAccount.checkBalance(); 

    } 

  

    public void start() { 

        while (true) { 

            displayOptions(); 

            System.out.print("Enter option number: "); 

            int option = scanner.nextInt(); 

            switch (option) { 

                case 1: 

                    withdraw(); 

                    break; 

                case 2: 

                    deposit(); 

                    break; 

                case 3: 

                    checkBalance(); 

                    break; 

                case 4: 

                    System.out.println("Exiting ATM. Thank you!"); 

                    return; 

                default: 

                    System.out.println("Invalid option. Please choose again."); 

                    break; 

            } 

        } 

    } 

} 

  

public class Main { 

    public static void main(String[] args) { 

        BankAccount userAccount = new BankAccount(1000); 

        ATM atmMachine = new ATM(userAccount); 

        atmMachine.start(); 

    } 

} 

 

 
