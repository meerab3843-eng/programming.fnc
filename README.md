#include <iostream>
#include <fstream>
using namespace std;

// Function to take input from user and store in array
void inputArray(int arr[], int size) {
    for(int i = 0; i < size; i++) {
        cout << "Enter element " << i + 1 << ": ";
        cin >> arr[i];
    }
}

// Function to display array elements
void displayArray(int arr[], int size) {
    cout << "Array Elements: ";
    for(int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

// Function to calculate sum of array elements (value-returning function)
int calculateSum(int arr[], int size) {
    int sum = 0;
    for(int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

// Function to write array data into a file
void writeToFile(int arr[], int size) {
    ofstream file("data.txt");

    if(!file) {
        cout << "Error opening file for writing!" << endl;
        return;
    }

    for(int i = 0; i < size; i++) {
        file << arr[i] << " ";
    }

    file.close();
    cout << "Data written to file successfully." << endl;
}

// Function to read data from file and display it
void readFromFile(int arr[], int size) {
    ifstream file("data.txt");

    if(!file) {
        cout << "Error opening file for reading!" << endl;
        return;
    }

    for(int i = 0; i < size; i++) {
        file >> arr[i];
    }

    file.close();

    cout << "Data read from file: ";
    displayArray(arr, size);
}

// Main function
int main() {
    const int SIZE = 10;
    int arr[SIZE];

    // Part (A): Input
    inputArray(arr, SIZE);

    // Part (B): Display
    displayArray(arr, SIZE);

    // Part (E): Calculate and display sum
    int sum = calculateSum(arr, SIZE);
    cout << "Sum of elements: " << sum << endl;

    // Part (C): Write to file
    writeToFile(arr, SIZE);

    // Part (D): Read from file
    readFromFile(arr, SIZE);

    return 0;
}
