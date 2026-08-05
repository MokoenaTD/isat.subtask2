 #include <iostream>
#include <string>

using namespace std;

// Function 1: Decimal to Binary
string decimalToBinary(int decimal) {
    if (decimal == 0) return "0";
    string binary = "";
    while (decimal > 0) {
        binary = to_string(decimal % 2) + binary;
        decimal = decimal / 2;
    }
    return binary;
}

// Function 2: Binary to Decimal
int binaryToDecimal(string binary) {
    int decimal = 0;
    int power = 1;
    for (int i = binary.length() - 1; i >= 0; i--) {
        if (binary[i] == '1')
            decimal += power;
        power *= 2;
    }
    return decimal;
}

// Function 3: Decimal to Hexadecimal
string decimalToHex(int decimal) {
    if (decimal == 0) return "0";
    string hex = "";
    char hexChars[] = {'0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F'};
    while (decimal > 0) {
        hex = hexChars[decimal  16] + hex;
        decimal = decimal / 16;
    }
    return hex;
}

// Function 4: Hexadecimal to Decimal
int hexToDecimal(string hex) {
    int decimal = 0;
    int power = 1;
    for (int i = hex.length() - 1; i >= 0; i--) {
        char c = toupper(hex[i]);
        int value = (c >= 'A')? (c - 'A' + 10) : (c - '0');
        decimal += value * power;
        power *= 16;
    }
    return decimal;
}

void showMenu() {
    cout << "\nConversion Menu:\n";
    cout << "1. Convert Decimal to Binary\n";
    cout << "2. Convert Binary to Decimal\n";
    cout << "3. Convert Hexadecimal to Decimal\n";
    cout << "4. Convert Decimal to Hexadecimal\n";
    cout << "5. Demo (Generate and convert random integers to binary)\n";
    cout << "6. Exit\n";
    cout << "Enter your choice (1-6): ";
}

int main() {
    
    int choice;
    do {
        showMenu();
        cin >> choice;

        if (choice == 1) {
            int num; cout << "Enter a decimal number: "; cin >> num;
            cout << "Binary representation: " << decimalToBinary(num) << endl;
        }
        else if (choice == 2) {
            string num; cout << "Enter a binary number: "; cin >> num;
            cout << "Decimal representation: " << binaryToDecimal(num) << endl;
        }
        else if (choice == 3) {
            string num; cout << "Enter a hexadecimal number: "; cin >> num;
            cout << "Decimal representation: " << hexToDecimal(num) << endl;
        }
        else if (choice == 4) {
            int num; cout << "Enter a decimal number: "; cin >> num;
            cout << "Hexadecimal representation: " << decimalToHex(num) << endl;
        }
        else if (choice == 5) {
            int randNum = rand() % 100;
            cout << "Generated random integer: " << randNum << endl;
            cout << "Binary representation: " << decimalToBinary(randNum) << endl;
        }
    } while (choice!= 6);

    cout << "Exiting the program." << endl;
    return 0;
}
 
