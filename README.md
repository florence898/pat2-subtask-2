#include <iostream>
#include <unordered_map>
#include <string>
#include <cctype>

using namespace std;

// Morse code map for letters only 
unordered_map<char, string> morseCode = {
    {'A', ".-"},   {'B', "-..."}, {'C', "-.-."}, {'D', "-.."},  {'E', "."},
    {'F', "..-."}, {'G', "--."},  {'H', "...."}, {'I', ".."},   {'J', ".---"},
    {'K', "-.-"},  {'L', ".-.."}, {'M', "--"},   {'N', "-."},   {'O', "---"},
    {'P', ".--."}, {'Q', "--.-"}, {'R', ".-."},  
    {'Z', "--.."}
};

// ASCII characters for dot and dash
const char DOT = 46;  // ASCII '.'
const char DASH = 45; // ASCII '-'

string translateToMorse(const string& message) {
    string fullMorse;
    for (char ch : message) {
        if (ch == ' ') continue; // skip space for individual letter output
        char upperCh = toupper(ch);
        if (isalpha(upperCh) && morseCode.find(upperCh) != morseCode.end()) {
            string morse = morseCode[upperCh];
            cout << upperCh << ": ";
            for (char symbol : morse) {
                cout << (symbol == '.' ? DOT : DASH);
            }
            cout << endl;

            for (char symbol : morse) {
                fullMorse += (symbol == '.' ? DOT : DASH);
            }
            fullMorse += "   "; // 
        }
    }
    return fullMorse;
}
