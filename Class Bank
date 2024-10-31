import java.util.Scanner;
import java.util.*;

class Account {
    protected String customerName;
    protected String accountNumber;
    protected double balance;

    public Account(String customerName, String accountNumber) {
        this.customerName = customerName;
        this.accountNumber = accountNumber;
        this.balance = 0.0;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: " + amount);
    }

    public void displayBalance() {
        System.out.println("Balance: " + balance);
    }
}

class SavAcct extends Account {
    private double interestRate;

    public SavAcct(String customerName, String accountNumber, double interestRate) {
        super(customerName, accountNumber);
        this.interestRate = interestRate;
    }

    public void computeAndDepositInterest() {
        double interest = balance * interestRate / 100;
        deposit(interest);
        System.out.println("Interest deposited: " + interest);
    }

    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        } else {
            System.out.println("Insufficient balance for withdrawal.");
        }
    }
}

class CurAcct extends Account {
    private double minimumBalance;

    public CurAcct(String customerName, String accountNumber, double minimumBalance) {
        super(customerName, accountNumber);
        this.minimumBalance = minimumBalance;
    }

    public void withdraw(double amount) {
        if (balance - amount < minimumBalance) {
            System.out.println("Insufficient balance after withdrawal. Minimum balance must be maintained.");
        } else {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        }
    }
}

public class Bank {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter customer name:");
        String customerName = scanner.nextLine();

        System.out.println("Enter account number:");
        String accountNumber = scanner.nextLine();

        System.out.println("Select account type (1: Savings, 2: Current):");
        int accountType = scanner.nextInt();

        Account account;
        if (accountType == 1) {
            System.out.println("Enter interest rate (%):");
            double interestRate = scanner.nextDouble();
            account = new SavAcct(customerName, accountNumber, interestRate);
        } else {
            System.out.println("Enter minimum balance:");
            double minimumBalance = scanner.nextDouble();
            account = new CurAcct(customerName, accountNumber, minimumBalance);
        }

        while (true) {
            System.out.println("\nMenu:");
            System.out.println("1. Deposit");
            System.out.println("2. Display Balance");
            System.out.println("3. Withdraw");
            System.out.println("0. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 2:
                    account.displayBalance();
                    break;
                case 3:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    if (account instanceof SavAcct) {
                        ((SavAcct) account).withdraw(withdrawAmount);
                    } else if (account instanceof CurAcct) {
                        ((CurAcct) account).withdraw(withdrawAmount);
                    }
                    break;
                case 0:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
