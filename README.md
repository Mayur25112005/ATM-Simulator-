# ATM-Simulator-
#include <iostream>
using namespace std;

class ATM {
private:
    double balance;

public:
    ATM(double initial_balance) {
        balance = initial_balance;
    }

    void checkBalance() {
        cout << "Your current balance is: $" << balance << endl;
    }

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "$" << amount << " has been deposited to your account." << endl;
        } else {
            cout << "Invalid deposit amount." << endl;
        }
    }

    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "$" << amount << " has been withdrawn from your account." << endl;
        } else {
            cout << "Invalid or insufficient funds for the withdrawal." << endl;
        }
    }
};

int main() {
    ATM myATM(1000.0); // Initial balance of $1000
    int choice;
    double amount;

    do {
        cout << "\nATM Simulator\n";
        cout << "1. Check Balance\n";
        cout << "2. Deposit Money\n";
        cout << "3. Withdraw Money\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                myATM.checkBalance();
                break;
            case 2:
                cout << "Enter the amount to deposit: $";
                cin >> amount;
                myATM.deposit(amount);
                break;
            case 3:
                cout << "Enter the amount to withdraw: $";
                cin >> amount;
                myATM.withdraw(amount);
                break;
            case 4:
                cout << "Thank you for using the ATM. Goodbye!\n";
                break;
            default:
                cout << "Invalid choice. Please try again.\n";
                break;
        }
    } while (choice != 4);

    return 0;
}
