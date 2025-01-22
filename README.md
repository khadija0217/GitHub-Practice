# GitHub-Practice
this repository is for practicing  GitHub workflows
#include <iostream>  
#include <string>  
using namespace std;  

// Base class for personal information  
class PersonalInfo {  
protected:  
    string name;  
    int age;  

public:  
    void setPersonalInfo(const string& n, int a) {  
        name = n;  
        age = a;  
    }  

    void displayPersonalInfo() const {  
        cout << "Name: " << name << ", Age: " << age << endl;  
    }  
};  

// Base class for academic information  
class AcademicInfo {  
protected:  
    int rollNumber;  
    float GPA;  

public:  
    void setAcademicInfo(int r, float g) {  
        rollNumber = r;  
        GPA = g;  
    }  

    void displayAcademicInfo() const {  
        cout << "Roll Number: " << rollNumber << ", GPA: " << GPA << endl;  
    }  
};  

// Derived class from PersonalInfo  
class Student : public PersonalInfo {  
protected:  
    int studentID;  

public:  
    void setStudentInfo(const string& n, int a, int id) {  
        setPersonalInfo(n, a);  
        studentID = id;  
    }  

    void displayStudentInfo() const {  
        displayPersonalInfo();  
        cout << "Student ID: " << studentID << endl;  
    }  
};  

// Further derived class that uses multiple inheritance  
class FullTimeStudent : public Student, public AcademicInfo {  
public:  
    void setFullTimeInfo(const string& n, int a, int id, int r, float g) {  
        setStudentInfo(n, a, id);  
        setAcademicInfo(r, g);  
    }  

    void displayFullTimeInfo() const {  
        displayStudentInfo();  
        displayAcademicInfo();  
    }  
};  

int main() {  
    FullTimeStudent student;  
    student.setFullTimeInfo("Alice Johnson", 21, 1001, 501, 3.9);  
    
    cout << "Student Information:" << endl;  
    student.displayFullTimeInfo();  

    return 0;  
}