    // Name: Emiliano Cardoso Aguiniga
    // Course: CISC 192 - C++ Programming
    // Date: 11/2/2025
    // Assignment: Non-Duplicated Integer Array Operations




---
    #include <iostream>
    #include <array>
  
    const int N = 5;
  
    // Check if a number already exists
    bool isDuplicate(const std::array<int, N>& arr, int number, int currentIndex) {
      for (int i = 0; i < currentIndex; i++) {
          if (arr[i] == number) {
              return true;
          }
      }
      return false;
    }
  
    void sortAscending(std::array<int, N>& arr) {
      for (int i = 0; i < N - 1; i++) {
          for (int j = 0; j < N - i - 1; j++) {
              if (arr[j] > arr[j + 1]) {
                  int temp = arr[j];
                  arr[j] = arr[j + 1];
                  arr[j + 1] = temp;
              }
          }
      }
    }
  
    void sortDescending(std::array<int, N>& arr) {
      for (int i = 0; i < N - 1; i++) {
          for (int j = 0; j < N - i - 1; j++) {
              if (arr[j] < arr[j + 1]) {
                  int temp = arr[j];
                  arr[j] = arr[j + 1];
                  arr[j + 1] = temp;
              }
          }
      }
    }
  
    // Function to find the maximum number
    int findMaximum(const std::array<int, N>& arr) {
      int max = arr[0];
      for (int i = 1; i < N; i++) {
          if (arr[i] > max) {
              max = arr[i];
          }
      }
      return max;
    }
  
    // Function to display the array
    void displayArray(const std::array<int, N>& arr) {
      for (int i = 0; i < N; i++) {
          std::cout << arr[i] << " ";
      }
      std::cout << std::endl;
    }
  
    int main() {
      std::array<int, N> numbers;

    std::cout << "Enter 5 unique integers:" << std::endl;

    // Get the # from the inputs
    for (int i = 0; i < N; i++) {
        int input;
        std::cout << "Element " << (i + 1) << ": ";
        std::cin >> input;

        // This checks for duplicates numbers
        while (isDuplicate(numbers, input, i)) {
            std::cout << "Duplicate found! Enter a different number." << std::endl;
            std::cout << "Element " << (i + 1) << ": ";
            std::cin >> input;
        }

        numbers[i] = input;
    }

    int choice;
    do {
        std::cout << "1. Sort by Ascending numbers" << std::endl;
        std::cout << "2. Sort Descending numbers" << std::endl;
        std::cout << "3. Find Maximum" << std::endl;
        std::cout << "Enter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1: {
                std::array<int, N> tempArray = numbers; // Create a copy to preserve original
                sortAscending(tempArray);
                std::cout << "\nThe ascending order:" << std::endl;
                displayArray(tempArray);
                break;
            }
            case 2: {
                std::array<int, N> tempArray = numbers; // Create a copy to preserve original
                sortDescending(tempArray);
                std::cout << "\nDescending order:" << std::endl;
                displayArray(tempArray);
                break;
            }
            case 3: {
                // Find the maximum number
                int maxNumber = findMaximum(numbers);
                std::cout << "\nThe Maximum number is #" << maxNumber << std::endl;
                break;
            }
        }
    } while (choice != 3);
    return 0;
    }
