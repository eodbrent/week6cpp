#include <iostream>
#include <string>
using namespace std;

class Person {
public:
	int id;
	string name;
	Person* next;
	Person(int id, const string &name, Person *next) : id(id), name(name), next(next) {}
	Person() {}
	~Person() {}
	virtual void printAbout() {}
};

class Teacher : public Person {
public:
	string title;
	string dept;
	Teacher(const string& title, const string& dept) : title(title), dept(dept) {}
	Teacher(int id, const string& name, const string& title, const string& dept) : Person(id, name, next), title(title), dept(dept) {}
	~Teacher() {}
	void printAbout() {
		cout << "Teacher name: " << name << ", Id: " << id << ", title: " << title << ", dept: " << dept << endl;
	}
};

class Student : public Person {
public:
	int year;
	char avg;
	Student(int year) : year(year) {}
	Student(int id, const string &name, int year, char avg) : Person(id, name, next), year(year), avg(avg) {}
	~Student() {}
	void printAbout() {
		cout << "Student name: " << name << ", Id: " << id << ", year: " << year << ", Average grade: " << avg << endl;
	}
};

Teacher* newTeacher(int id, const string& name, const string& title, const string& dept) {
	Teacher* teacher = new Teacher(id, name, title, dept);
	teacher->next = NULL;
	return teacher;
}

Student *newStudent(int id, const string &name, int year, char avg) {
	Student* student = new Student(id, name, year, avg);
	student->next = NULL;
	return student;
}

void displayRecords(Person* head) {
	Person* temp = head;
	while (temp != NULL) {
		temp->printAbout();
		temp = temp->next;
	}
	delete temp;
}

bool recCheck(Person* head, int id) {
	Person* temp = head;
	while (temp != NULL) {
		if (temp->id == id) {
			return true;
		}
		temp = temp->next;
	}
	delete temp;
	return false;
}
int main() {
	bool loop = true;
	bool idcheck;
	int id, year, choice, ititle;
	string name, dept, stitle;
	char avg;
	Person* head = NULL;
	Student* st;
	Teacher* t;
	while (loop) {
		bool title = true;
		cout << "\t\tWelcome to RU Record Management System" << endl;
		cout << "\n\tPress" << endl;
		cout << "\t1 for new student record" << endl;
		cout << "\t2 for new teacher record" << endl;
		cout << "\t3 to display all records" << endl;
		cout << "\t4 to exit" << endl;
		cout << "\nEnter your choice" << endl;
		cin >> choice;
		cin.ignore();
		switch(choice){
			case 1:
				cout << "Enter student name: " << endl;
				getline(cin, name);
				cout << "Enter student id: " << endl;
				cin >> id;
				idcheck = recCheck(head, id);
				if (idcheck) {
					cout << "Id number is already in database." << endl;
					break;
				}
				cout << "Enter student year: " << endl;
				cin >> year;
				cout << "Enter student's average grade: " << endl;
				cin >> avg;
				st = newStudent(id, name, year, avg);
				st->next = head;
				head = st;
				break;
			case 2:
				cout << "Enter teacher name: " << endl;
				getline(cin, name);
				cout << "Enter teacher id : " << endl;
				cin >> id;
				idcheck = recCheck(head, id);
				if (idcheck) {
					cout << "Id number is already in database." << endl;
					break;
				}
				while (title) {
					cout << "Enter teacher title: 1 for lecturer, 2 for assistance professor or 3 for associate professor." << endl;
					cin >> ititle;
					if (ititle == 1) {
						stitle = "lecturer";
						title = false;
					} else if (ititle == 2) {
						stitle = "assistance professor";
						title = false;
					} else if (ititle == 3) {
						stitle = "associate professor";
						title = false;
					} else {
						cout << "You must enter one of the valid choices: 1 for lecturer, 2 for assistance professor or 3 for associate professor." << endl;
						cin.get();
						title = true;
					}
				}
				cin.ignore();
				cout << "Enter teacher department: " << endl;
				getline(cin, dept);
				t = newTeacher(id, name, stitle, dept);
				t->next = head;
				head = t;
				break;
			case 3:
				displayRecords(head);
				cout << endl;
				break;
			case 4:
				loop = false;
				break;
			default:
				cout << "Please make a valid selection" << endl;
				break;
		}
	}
}
