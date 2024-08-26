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

