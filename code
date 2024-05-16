#include <bits/stdc++.h>
using namespace std;

struct Student {
    int ID;
    string name;
    string surname;
    vector<string> courses;
};

struct Course {
    int code;
    string name;
};

//Vectors to store data
vector<Student> students;
vector<Course> courses;

string studentFile = "students.txt";
string courseFile = "courses.txt";

// Function prototypes
void createStudent(int ID, string name, string surname);
void displayStudents();
void deleteStudent(int ID);
void createCourse(int code, string name);
void displayCourses();
void updateCourse(int code);
void deleteCourse(int code);
void readStudentsFromFile();
void writeStudentsToFile();
void readCoursesFromFile();
void writeCoursesToFile();

int main() {
    // Read data from files
    readStudentsFromFile();
    readCoursesFromFile();

    // Main loop to interact with the user
    int choice;
    do {
        cout << "\nCourse Enrollment Management System\n";
        cout << "1. Add Student\n";
        cout << "2. Display Students\n";
        cout << "3. Delete Student\n";
        cout << "4. Add Course\n";
        cout << "5. Display Courses\n";
        cout << "6. Update Course\n";
        cout << "7. Delete Course\n";
        cout << "0. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

            if (choice == 1) {
   
                int ID;
                string name, surname;
                cout << "Enter student ID: ";
                cin >> ID;
                cout << "Enter student name: ";
                cin.ignore(); //to clear input buffer
                getline(cin, name);
                cout << "Enter student surname: ";
                getline(cin, surname);
                createStudent(ID, name, surname);
                
            } else if (choice == 2) {
                
                displayStudents();
                
            } else if (choice == 3) {
               
                int ID;
                cout << "Enter student ID to delete: ";
                cin >> ID;
                deleteStudent(ID);
                
            } else if (choice == 4) {
                
                int code;
                string name;
                cout << "Enter course code: ";
                cin >> code;
                cout << "Enter course name: ";
                cin.ignore();
                getline(cin, name);
                createCourse(code, name);
                
            } else if (choice == 5) {
                
                displayCourses();
                
            } else if (choice == 6) {
                
                int code;
                cout << "Enter course code to update: ";
                cin >> code;
                updateCourse(code);
                
            } else if (choice == 7) {
                
                int code;
                cout << "Enter course code to delete: ";
                cin >> code;
                deleteCourse(code);
                
            } else if (choice == 0) {
                
            } else {
                
                cout << "Invalid choice. Please try again.\n";
            }


    } while (choice != 0);

    // Write data to files before exiting
    writeStudentsToFile();
    writeCoursesToFile();

    cout << "Exiting...\n";

    return 0;
}

void createStudent(int ID, string name, string surname) {
    Student newStudent;
    newStudent.ID = ID;
    newStudent.name = name;
    newStudent.surname = surname;
    students.push_back(newStudent);
    cout << "Student added successfully." << endl;
}

void displayStudents() {
    if (students.empty()) {
        cout << "No students to display." << endl;
        return;
    }
    cout << "List of Students:" << endl;
    for (const auto& student : students) {
        cout << "ID: " << student.ID << ", Name: " << student.name << ", Surname:" << student.surname << endl;
    }
}

void deleteStudent(int ID) {
    for (auto it = students.begin(); it != students.end(); ++it) {
        if (it->ID == ID) {
            students.erase(it);
            cout << "Student with ID " << ID << " deleted successfully." << endl;
            return;
        }
    }
    cout << "Student with ID " << ID << " not found." << endl;
}

void createCourse(int code, string name) {
    Course newCourse;
    newCourse.code = code;
    newCourse.name = name;
    courses.push_back(newCourse);
    cout << "Course added successfully." << endl;
}

void displayCourses() {
    if (courses.empty()) {
        cout << "No courses to display." << endl;
        return;
    }
    cout << "List of Courses:" << endl;
    for (const auto& course : courses) {
        cout << "Code: " << course.code << ", Name: " << course.name << endl;
    }
}

void updateCourse(int code) {
    for (auto& course : courses) {
        if (course.code == code) {
            string newName;
            cout << "Enter new name for course " << code << ": ";
            cin.ignore(); // Clear input buffer
            getline(cin, newName);
            course.name = newName;
            cout << "Course updated successfully." << endl;
            return;
        }
    }
    cout << "Course with code " << code << " not found." << endl;
}

void deleteCourse(int code) {
    for (auto it = courses.begin(); it != courses.end(); ++it) {
        if (it->code == code) {
            courses.erase(it);
            cout << "Course with code " << code << " deleted successfully." << endl;
            return;
        }
    }
    cout << "Course with code " << code << " not found." << endl;
}


void readStudentsFromFile() {
    ifstream file(studentFile);
    if (file.is_open()) {
        students.clear(); // Clear existing data
        string line;
        while (getline(file, line)) {
            istringstream iss(line);
            int ID;
            string name;
            string surname;
            if (iss >> ID >> name >> surname) {
                createStudent(ID, name, surname);
            }
        }
        file.close();
    } 
}

void writeStudentsToFile() {
    ofstream file(studentFile);
    if (file.is_open()) {
        for (const auto& student : students) {
            file << student.ID << " " << student.name << " " << student.surname << endl;
        }
        file.close();
    }
}

void readCoursesFromFile() {
    ifstream file(courseFile);
    if (file.is_open()) {
        courses.clear(); // Clear existing data
        int code;
        string name;
        while (file >> code >> ws && getline(file, name)) {
            createCourse(code, name);
        }
        file.close();
    }
}

void writeCoursesToFile() {
    ofstream file(courseFile);
    if (file.is_open()) {
        for (const auto& course : courses) {
            file << course.code << " " << course.name << endl;
        }
        file.close();
    }
}

