# LABORATORY-EXERCISE-1-Directory-Management-System
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <direct.h>
#include <windows.h>

void displayFiles() {
system("dir");
system("pause")
}

void createDirectory() {
    std::cout << "\nEnter the Directory name: ";
    std::string dirName;
    std::cin >> dirName;

    if (_mkdir(dirName.c_str()) == 0) {
        std::cout << "\nDirectory '" << dirName << "' Successfully Created\n";
    } else {
        std::cout << "\nFailed to Create Directory '" << dirName << "'\n";
    }

    system("pause");
    
}
void changeDirectory() {
    char currentDir[FILENAME_MAX];
    _getcwd(currentDir, sizeof(currentDir));
    std::cout << "\nCurrent Directory: " << currentDir << '\n';

    std::cout << "1. Step by Step Backward\n";
    std::cout << "2. Goto Root Directory\n";
    std::cout << "3. Forward Directory\n";
    std::cout << "Enter the Number: ";
    int choice;
    std::cin >> choice;

    
