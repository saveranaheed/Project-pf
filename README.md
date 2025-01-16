# Project-pf
```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

struct Student {
    int studentID;
    string name;
    int age;
    string grade;
};

void addStudent(vector<Student> &students);
void displayStudents(const vector<Student> &students);
void searchStudent(const vector<Student> &students);
void updateStudent(vector<Student> &students);
void deleteStudent(vector<Student> &students);

int main() {
    vector<Student> students;
    int choice;

    do {
        cout << "\nStudent Management System\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Search Student\n";
        cout << "4. Update Student\n";
        cout << "5. Delete Student\n";
        cout << "6. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                addStudent(students);
                break;
            case 2:
                displayStudents(students);
                break;
            case 3:
                searchStudent(students);
                break;
            case 4:
                updateStudent(students);
                break;
            case 5:
                deleteStudent(students);
                break;
            case 6:
                cout << "Exiting program. Thank you!\n";
                break;
            default:
                cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 6);

    return 0;
}

void addStudent(vector<Student> &students) {
    Student newStudent;
    cout << "Enter Student ID: ";
    cin >> newStudent.studentID;
    cin.ignore(); 
    cout << "Enter Name: ";
    getline(cin, newStudent.name);
    cout << "Enter Age: ";
    cin >> newStudent.age;
    cout << "Enter Grade: ";
    cin >> newStudent.grade;

    students.push_back(newStudent);
    cout << "Student added successfully!\n";
}

void displayStudents(const vector<Student> &students) {
    if (students.empty()) {
        cout << "No students available to display.\n";
        return;
    }

    cout << "\nStudent Details:\n";
    cout << "ID    | Name       | Age | Grade\n";
    cout << "-----------------------------\n";
    for (const auto &student : students) {
        cout << student.studentID << "   | " << student.name << "   | " 
             << student.age << "  | " << student.grade << "\n";
    }
}

void searchStudent(const vector<Student> &students) {
    if (students.empty()) {
        cout << "No students to search.\n";
        return;
    }

    int searchID;
    cout << "Enter Student ID to search: ";
    cin >> searchID;

    bool found = false;
    for (const auto &student : students) {
        if (student.studentID == searchID) {
            cout << "\nStudent Found!\n";
            cout << "ID: " << student.studentID << "\n";
            cout << "Name: " << student.name << "\n";
            cout << "Age: " << student.age << "\n";
            cout << "Grade: " << student.grade << "\n";
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Student with ID " << searchID << " not found.\n";
    }
}

void updateStudent(vector<Student> &students) {
    if (students.empty()) {
        cout << "No students to update.\n";
        return;
    }

    int searchID;
    cout << "Enter Student ID to update: ";
    cin >> searchID;

    bool found = false;
    for (auto &student : students) {
        if (student.studentID == searchID) {
            cout << "\nStudent Found! Enter new details.\n";

            cout << "Enter Name: ";
            cin.ignore(); 
            getline(cin, student.name);
            cout << "Enter Age: ";
            cin >> student.age;
            cout << "Enter Grade: ";
            cin >> student.grade;

            cout << "Student details updated successfully!\n";
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Student with ID " << searchID << " not found.\n";
    }
}

void deleteStudent(vector<Student> &students) {
    if (students.empty()) {
        cout << "No students to delete.\n";
        return;
    }

    int searchID;
    cout << "Enter Student ID to delete: ";
    cin >> searchID;

    bool found = false;
    for (auto it = students.begin(); it != students.end(); ++it) {
        if (it->studentID == searchID) {
            students.erase(it);
            cout << "Student with ID " << searchID << " deleted successfully!\n";
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Student with ID " << searchID << " not found.\n";
    }
}
```
