# shopping-order-history-system
#include <iostream>
#include <fstream>
using namespace std;

struct Order {
    string customer;
    string product;
    int quantity;
    float price;
};

int main() {
    Order o;
    ofstream file("orders.txt", ios::app);
    cout << "Enter Customer Name: ";
    cin >> o.customer;
    cout << "Enter Product Name: ";
    cin >> o.product;
    cout << "Enter Quantity: ";
    cin >> o.quantity;
    cout << "Enter Price: ";
    cin >> o.price;

    file << o.customer << " "
         << o.product << " "
         << o.quantity << " "
         << o.price << endl;
    file.close();

    ifstream readFile("orders.txt");
    cout << "\nOrder History:\n";
    while(readFile >> o.customer >> o.product >> o.quantity >> o.price) {
        cout << o.customer << " " << o.product << " "
             << o.quantity << " " << o.price << endl;
    }
    readFile.close();
    return 0;
}
