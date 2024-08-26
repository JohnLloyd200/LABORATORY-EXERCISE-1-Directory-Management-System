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

void listFilesMenu() {
    int choice;
    cout << "\nList Files Menu\n";
    cout << "1. List all files in the current directory\n";
    cout << "2. List files based on a specific extension\n";
    cout << "3. List files based on a pattern\n";
    cout << "Enter your choice: ";
    cin >> choice;
    
  switch (choice) {
        case 1:
            listAllFiles();
            break;
        case 2:
            listFilesByExtension();
            break;
        case 3:
            listFilesByPattern();
            break;
        default:
            cout << "Invalid choice. Returning to main menu.\n";
    }
}

void listAllFiles() {
    cout << "\nFiles in the current directory:\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        cout << entry.path().filename().string() << endl;
    }
}

void listFilesByExtension() {
    string extension;
    cout << "Enter the file extension (e.g., .txt): ";
    cin >> extension;
    cout << "\nFiles with extension '" << extension << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (entry.path().extension() == extension) {
            cout << entry.path().filename().string() << endl;
        }
    }
}

void listFilesByPattern() {
    string pattern;
    cout << "Enter the pattern (e.g., moha*.*): ";
    cin >> pattern;

  string regex_pattern = regex_replace(pattern, regex("\\*"), ".*");
    
  cout << "\nFiles matching pattern '" << pattern << "':\n";
    for (const auto& entry : fs::directory_iterator(fs::current_path())) {
        if (regex_match(entry.path().filename().string(), regex(regex_pattern))) {
            cout << entry.path().filename().string() << endl;
        }
    }
}

void createDirectory() {
    string dirName;
    cout << "Enter the name of the directory to create: ";
    cin >> dirName;

 fs::path newDir = fs::current_path() / dirName; // Create in the current directory
    if (fs::create_directory(newDir)) {
        cout << "Directory '" << dirName << "' created successfully.\n";
    } else {
        cout << "Error: Directory '" << dirName << "' could not be created.\n";
    }
}





