@Override
    public void checkBalance(String accountNumber) {
        for (int i = 0; i < numAccounts; i++) {
            if (accounts[i].getAccountNumber().equals(accountNumber)) {
                System.out.println("Balance: " + accounts[i].getBalance());
                break;
            }
        }
    }

    private String generateAccountNumber() {
        return "A" + System.currentTimeMillis();
    }
}

public class Main {
    public static void main(String[] args) {
        Bank bank = new BankSystem();
        Scanner scanner = new Scanner(System.in);
        String input;

        while (true) {
            System.out.println("\nEnter a command: (open, close, deposit, withdraw, balance, quit)");
            input = scanner.nextLine();

            switch (input) {
                case "open":
                    System.out.println("Enter account type: (savings, checking)");
                    String accountType = scanner.nextLine();
                    bank.openAccount(accountType);
                    break;
                case "close":
                    System.out.println("Enter account number:");
                    String accountNumber = scanner.nextLine();
                    bank.closeAccount(accountNumber);
                    break;
                case "deposit":
                    System.out.println("Enter account number:");
                    accountNumber = scanner.nextLine();
                    System.out.println("Enter amount:");
                    double amount = scanner.nextDouble();
                    bank.deposit(accountNumber, amount);
                    break;
                case "withdraw":
                    System.out.println("Enter account number:");
                    accountNumber = scanner.nextLine();
                    System.out.println("Enter amount:");
                    amount = scanner.nextDouble();
                    bank.withdraw(accountNumber, amount);
                    break;
                case "balance":
                    System.out.println("Enter account number:");
                    accountNumber = scanner.nextLine();
                    bank.checkBalance(accountNumber);
                    break;
                case "quit":
                    return;
                default:
                    System.out.println("Invalid command.");
                    break;
            }
        }
    }
}
