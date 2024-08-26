#include <iostream>
#include <filesystem>
#include <vector>
#include <regex>
#include <string>
#include <cstdlib> 

namespace fs = std::filesystem;
using namespace std;

void displayMainMenu();
void handleMainMenuSelection(int choice);
void listFilesMenu();
void listAllFiles();
void listFilesByExtension();
void listFilesByPattern();
void createDirectory();
void changeDirectory();
void displayDirectoryMenu();
void handleDirectorySelection(int choice);
void exitProgram();

int main() {
    int choice;
    do {
        displayMainMenu();
        cin >> choice;
        handleMainMenuSelection(choice);
    } while (choice != 4);
    return 0;
}

void displayMainMenu() {
    cout << "\nDirectory Management System\n";
    cout << "1. To Display List of Files\n";
    cout << "2. To Create New Directory\n";
    cout << "3. To Change the Working Directory\n";
    cout << "4. Exit\n";
    cout << "Enter your choice: ";
}

void handleMainMenuSelection(int choice) {
    switch (choice) {
        case 1:
            listFilesMenu();
            break;
        case 2:
            createDirectory();
            break;
        case 3:
            changeDirectory();
            break;
        case 4:
            exitProgram();
            break;
        default:
            cout << "Invalid choice. Please try again.\n";
    }
}



