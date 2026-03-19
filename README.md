# CodeAlpha-fourth-Task
bank.cpp
#include <iostream>
#include <vector>
using namespace std;

// Transaction Class
class Transaction {
public:
    string type;
    double amount;

    Transaction(string t, double a) {
        type = t;
        amount = a;
    }

    void showTransaction() {
        cout << type << ": " << amount << endl;
    }
};

// Account Class
class Account {
private:
    string name;
    int accNo;
    double balance;
    vector<Transaction> history;

public:
    void createAccount() {
        cout << "Enter Name: ";
        cin >> name;
        cout << "Enter Account Number: ";
        cin >> accNo;
        cout << "Enter Initial Balance: ";
        cin >> balance;
    }

    void deposit() {
        double amount;
        cout << "Enter amount to deposit: ";
        cin >> amount;

        balance += amount;
        history.push_back(Transaction("Deposit", amount));

        cout << "Deposit Successful!\n";
    }

    void withdraw() {
        double amount;
        cout << "Enter amount to withdraw: ";
        cin >> amount;

        if(amount <= balance) {
            balance -= amount;
            history.push_back(Transaction("Withdraw", amount));
            cout << "Withdrawal Successful!\n";
        } else {
            cout << "Insufficient Balance!\n";
        }
    }

    void showDetails() {
        cout << "\nName: " << name;
        cout << "\nAccount No: " << accNo;
        cout << "\nBalance: " << balance << endl;
    }

    void showTransactions() {
        cout << "\nTransaction History:\n";
        for(int i = 0; i < history.size(); i++) {
            history[i].showTransaction();
        }
    }
};

int main() {
    Account acc;
    int choice;

    acc.createAccount();

    do {
        cout << "\n1. Deposit\n2. Withdraw\n3. Show Details\n4. Show Transactions\n5. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        switch(choice) {
            case 1: acc.deposit(); break;
            case 2: acc.withdraw(); break;
            case 3: acc.showDetails(); break;
            case 4: acc.showTransactions(); break;
            case 5: cout << "Thank You!\n"; break;
            default: cout << "Invalid Choice!\n";
        }

    } while(choice != 5);

    return 0;
}
