

'''C++
print (This is assignment Lab: Decision and switch statements )

# Challenges
The hardest part was how to hadle an invalid input. As it required learing the cin label which was brand new and making it so that the code can reject invalid inputs in leter or integer form.
# Below is the the code for the calculator for C++

  

    #include <iostream>
    #include <limits>
        using namespace std;
    //Function serves as a caculator
        enum class MenuOption {
    //if # from 1-5 is inserted perform program
        ADD = 1,
        SUBTRACT,
        MULTIPLY,
        DIVIDE,
        QUIT
    };
    //if valid input, input numbers
    double getValidatedDouble(const string& prompt) {
    double value;
    while (true) {
        cout << prompt;
        cin >> value;
        //if # not inserted for a or b
        if (cin.fail()) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "Please Enter a Real Number" << endl;
        } else {
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            return value;
            }
        }
    }

    int main() {
    MenuOption choice;
    double a, b, result;

    while (true) {
        cout << "\nLab: Menu-driven calculator" << endl;
        cout << "1. Add" << endl;
        cout << "2. Subtract" << endl;
        cout << "3. Multiply" << endl;
        cout << "4. Divide" << endl;
        cout << "5. Quit" << endl;
        cout << "Enter a # from 1 to 5: ";

        int input;
        cin >> input;
            //if a valid # is not input give text
        if (cin.fail()) {
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
            cout << "A number between 1 and 5." << endl;
            continue;
        }
            //choice = 5 then give text
        choice = static_cast<MenuOption>(input);

        if (choice == MenuOption::QUIT) {
            cout << "bye" << endl;
            break;
        }

        if (choice < MenuOption::ADD || choice > MenuOption::QUIT) {
            cout << "Please enter a number between 1 and 5." << endl;
            continue;
        }

        a = getValidatedDouble("Enter a #: ");
        b = getValidatedDouble("Enter a second #: ");

        switch (choice) {
            case MenuOption::ADD:
                result = a + b;
                cout << a << " + " << b << " = " << result << endl;
                break;

            case MenuOption::SUBTRACT:
                result = a - b;
                cout << a << " - " << b << " = " << result << endl;
                break;

            case MenuOption::MULTIPLY:
                result = a * b;
                cout << a << " * " << b << " = " << result << endl;
                break;

            case MenuOption::DIVIDE:
                if (b == 0) {
                    cout << "CANNOT DIVIDE BY 0" << endl;
                    //if b=0 then add text
                } else {
                    result = a / b;
                    cout << a << " / " << b << " = " << result << endl;
                }
                break;

            default:
                cout << "Invalid choice. Please try again." << endl;
                break;
        }
    }

    return 0;
    }   
Video link here:
https://youtu.be/uI6L3-3WmBM
