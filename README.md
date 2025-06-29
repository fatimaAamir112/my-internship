#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    int numCourses;
    cout << "Enter number of courses: ";
    cin >> numCourses;

    vector<char> grades(numCourses);
    vector<int> credits(numCourses);
    double totalPoints = 0.0;
    int totalCredits = 0;

    for (int i = 0; i < numCourses; i++) {
        cout << "Course " << i + 1 << ":\n";
        cout << "  Grade (A/B/C/D/F): ";
        cin >> grades[i];
        cout << "  Credit hours: ";
        cin >> credits[i];

        // Convert grade to points
        double points;
        switch (toupper(grades[i])) {
            case 'A': points = 4.0; break;
            case 'B': points = 3.0; break;
            case 'C': points = 2.0; break;
            case 'D': points = 1.0; break;
            default: points = 0.0;
        }

        totalPoints += points * credits[i];
        totalCredits += credits[i];
    }

    double gpa = totalPoints / totalCredits;
    
    cout << "\n--- Results ---\n";
    for (int i = 0; i < numCourses; i++) {
        cout << "Course " << i + 1 << ": Grade " << grades[i] 
             << " | Credits: " << credits[i] << endl;
    }
    cout << fixed << setprecision(2);
    cout << "Semester GPA: " << gpa << endl;
    cout << "Overall CGPA: " << gpa << endl; // Same as semester GPA

    return 0;
