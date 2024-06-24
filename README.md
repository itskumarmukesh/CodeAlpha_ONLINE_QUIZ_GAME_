# CodeAlpha_ONLINE_QUIZ_GAME_
This repository contains an online quiz game.

## Features
- Multiple choice questions
- feedback on answers
- Score tracking
- User-friendly interface

## code_
-----------------------------------------------------------------------------
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>

using namespace std;

struct Question {
    string questionText;
    vector<string> options;
    char correctAnswer;
};

struct User {
    string username;
    string password;
};

void registerUser(User &user) {
    cout << "Enter a username: ";
    cin >> user.username;
    cout << "Please enter passward: ";
    cin >> user.password;
    cout << "You are successfully registered!\n";
}

void takeQuiz(const User &user, const vector<Question> &questions) {
    cout << "\nWelcome to the World of Quiz Game!  , " << user.username << "!\n";
    int score = 0;
    unordered_map<string, char> incorrectAnswers;

    for (size_t i = 0; i < questions.size(); ++i) {
        cout << "Question " << i + 1 << ": " << questions[i].questionText << "\n";
        for (size_t j = 0; j < questions[i].options.size(); ++j) {
            cout << questions[i].options[j] << "\n";
        }

        char answer;
        cout << "Select your answer (A, B, C, D): ";
        cin >> answer;
        answer = toupper(answer);

        if (answer == questions[i].correctAnswer) {
            ++score;
        } else {
            incorrectAnswers[questions[i].questionText] = questions[i].correctAnswer;
        }

        cout << "\n";
    }

    cout << "Quiz finished! Check your score: " << score << "/" << questions.size() << "\n\n";
    if (!incorrectAnswers.empty()) {
        cout << "Please verify the correct answers for the questions you missed:\n";
        for (const auto &pair : incorrectAnswers) {
            cout << "Question: " << pair.first << "\nCorrect Answer: " << pair.second << "\n\n";
        }
    } else {
        cout << "Well Done! You answered all questions correctly!\n";
    }
}

int main() {
    vector<Question> questions = {
        {
            "What is the capital of bihar?",
            {"A) Bilspur", "B) Champaran", "C) Patna", "D) Jaipur"},
            'C'
        },
        {
            "How many union territories are there in india?",
            {"A) 7 Union territories", "B) 8 Union territories", "C) 9 Union territories", "D) 4 Union territories"},
            'B'
        },
        {
            "What is the name of the wheel on the Indian flag?",
            {"A) Ashoka Chakra", "B) Dhammacakka", "C) The Wheel of the Law", "D) A winged wheel "},
            'A'
        },
      {
            "What is the powerhouse of cell?",
            {"A) Nucleus", "B) Cytoplasm.", "C) Mitochondria", "D) Cell membrane"},
            'C'
        },
        {
            "What is the largest ocean on Earth?",
            {"A) Atlantic Ocean", "B) Indian Ocean", "C) Arctic Ocean", "D) Pacific Ocean"},
            'D'
        },
    };

    User user;
    cout << "Welcome to the World of Quiz Game! \n\n";
    registerUser(user);
    takeQuiz(user, questions);

    return 0;
}


