# Advanced C++ Calculator

A feature-rich command-line calculator built in C++ that handles basic arithmetic, trigonometry, and logarithmic operations with robust input validation.

## ✨ Features
- **Basic Arithmetic:** Addition, Subtraction, Multiplication, Division, Modulo.
- **Advanced Math:** Power ($x^y$), Square Root, Factorial, Absolute Value, Exponential ($e^x$).
- **Trigonometry:** Sine, Cosine, Tangent (with automatic Degree to Radian conversion).
- **Robust Input Validation:** Prevents infinite loops caused by invalid character inputs and handles edge cases like division by zero or negative square roots.

## 🚀 How to Run
1. Clone the repository or download the source code.
2. Open a terminal and compile using `g++`:
   ```bash
   g++ -o calculator main.cpp
#include <iostream>
#include <cmath>
#include <limits>
#include <iomanip>

using namespace std;

void clearInput() {
    cin.clear();
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
}

double readDouble(const string &prompt) {
    double value;
    while (true) {
        cout << prompt;
        if (cin >> value) {
            clearInput();
            return value;
        }
        cout << "Invalid input. Please enter a number.\n";
        clearInput();
    }
}

int readInt(const string &prompt) {
    int value;
    while (true) {
        cout << prompt;
        if (cin >> value) {
            clearInput();
            return value;
        }
        cout << "Invalid input. Please enter an integer.\n";
        clearInput();
    }
}

unsigned long long factorial(int n) {
    if (n < 0) return 0ULL;
    unsigned long long result = 1ULL;
    for (int i = 1; i <= n; ++i) {
        result *= i;
    }
    return result;
}

void showMenu() {
    cout << "\n=== Advanced Calculator ===\n";
    cout << "1) Addition\n";
    cout << "2) Subtraction\n";
    cout << "3) Multiplication\n";
    cout << "4) Division\n";
    cout << "5) Power (x^y)\n";
    cout << "6) Square root\n";
    cout << "7) Factorial\n";
    cout << "8) Sine\n";
    cout << "9) Cosine\n";
    cout << "10) Tangent\n";
    cout << "11) Natural logarithm (ln)\n";
    cout << "12) Log base 10\n";
    cout << "13) Exponential (e^x)\n";
    cout << "14) Absolute value\n";
    cout << "15) Modulo (integer)\n";
    cout << "0) Exit\n";
}

int main() {
    cout << fixed << setprecision(6);
    while (true) {
        showMenu();
        int choice = readInt("Choose an operation: ");

        if (choice == 0) {
            cout << "Goodbye!\n";
            break;
        }

        double a, b, result;
        switch (choice) {
            case 1:
                a = readDouble("Enter first number: ");
                b = readDouble("Enter second number: ");
                result = a + b;
                cout << "Result: " << result << "\n";
                break;
            case 2:
                a = readDouble("Enter first number: ");
                b = readDouble("Enter second number: ");
                result = a - b;
                cout << "Result: " << result << "\n";
                break;
            case 3:
                a = readDouble("Enter first number: ");
                b = readDouble("Enter second number: ");
                result = a * b;
                cout << "Result: " << result << "\n";
                break;
            case 4:
                a = readDouble("Enter dividend: ");
                b = readDouble("Enter divisor: ");
                if (b == 0) {
                    cout << "Error: division by zero is not allowed.\n";
                } else {
                    result = a / b;
                    cout << "Result: " << result << "\n";
                }
                break;
            case 5:
                a = readDouble("Enter base: ");
                b = readDouble("Enter exponent: ");
                result = pow(a, b);
                cout << "Result: " << result << "\n";
                break;
            case 6:
                a = readDouble("Enter number: ");
                if (a < 0) {
                    cout << "Error: square root of a negative number is not supported.\n";
                } else {
                    result = sqrt(a);
                    cout << "Result: " << result << "\n";
                }
                break;
            case 7: {
                int n = readInt("Enter a non-negative integer: ");
                if (n < 0) {
                    cout << "Error: factorial is defined for non-negative integers only.\n";
                } else {
                    unsigned long long fact = factorial(n);
                    cout << "Result: " << fact << "\n";
                }
                break;
            }
            case 8:
                a = readDouble("Enter angle in degrees: ");
                result = sin(a * M_PI / 180.0);
                cout << "Result: " << result << "\n";
                break;
            case 9:
                a = readDouble("Enter angle in degrees: ");
                result = cos(a * M_PI / 180.0);
                cout << "Result: " << result << "\n";
                break;
            case 10:
                a = readDouble("Enter angle in degrees: ");
                result = tan(a * M_PI / 180.0);
                cout << "Result: " << result << "\n";
                break;
            case 11:
                a = readDouble("Enter number: ");
                if (a <= 0) {
                    cout << "Error: natural logarithm is defined for positive numbers only.\n";
                } else {
                    result = log(a);
                    cout << "Result: " << result << "\n";
                }
                break;
            case 12:
                a = readDouble("Enter number: ");
                if (a <= 0) {
                    cout << "Error: log base 10 is defined for positive numbers only.\n";
                } else {
                    result = log10(a);
                    cout << "Result: " << result << "\n";
                }
                break;
            case 13:
                a = readDouble("Enter exponent: ");
                result = exp(a);
                cout << "Result: " << result << "\n";
                break;
            case 14:
                a = readDouble("Enter number: ");
                cout << "Result: " << fabs(a) << "\n";
                break;
            case 15: {
                int x = readInt("Enter first integer: ");
                int y = readInt("Enter second integer: ");
                if (y == 0) {
                    cout << "Error: modulo by zero is not allowed.\n";
                } else {
                    cout << "Result: " << (x % y) << "\n";
                }
                break;
            }
            default:
                cout << "Invalid option. Please choose a number from the menu.\n";
                break;
        }
    }

    return 0;
}
