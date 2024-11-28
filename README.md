class Student:
    def __init__(self, student_id, name, age):
        self.student_id = student_id
        self.name = name
        self.age = age
        self.grades = {}
        self.attendance = {}

    def add_grade(self, subject, grade):
        self.grades[subject] = grade

    def mark_attendance(self, date, status):
        self.attendance[date] = status

    def __str__(self):
        return f"ID: {self.student_id}, Name: {self.name}, Age: {self.age}, Grades: {self.grades}, Attendance: {self.attendance}"
        class StudentManagementSystem:
    def __init__(self):
        self.students = {}

    def add_student(self, student_id, name, age):
        if student_id in self.students:
            print("Student ID already exists.")
        else:
            self.students[student_id] = Student(student_id, name, age)
            print(f"Student {name} added successfully.")

    def view_students(self):
        for student in self.students.values():
            print(student)

    def update_student(self, student_id, name=None, age=None):
        if student_id in self.students:
            if name:
                self.students[student_id].name = name
            if age:
                self.students[student_id].age = age
            print(f"Student {student_id} updated successfully.")
        else:
            print("Student ID not found.")

    def delete_student(self, student_id):
        if student_id in self.students:
            del self.students[student_id]
            print(f"Student {student_id} deleted successfully.")
        else:
            print("Student ID not found.")

    def record_attendance(self, student_id, date, status):
        if student_id in self.students:
            self.students[student_id].mark_attendance(date, status)
            print(f"Attendance recorded for {student_id}.")
        else:
            print("Student ID not found.")

    def record_grade(self, student_id, subject, grade):
        if student_id in self.students:
            self.students[student_id].add_grade(subject, grade)
            print(f"Grade recorded for {student_id}.")
        else:
            print("Student ID not found.")
            def main():
    sms = StudentManagementSystem()
    
    while True:
        print("\n--- Student Management System ---")
        print("1. Add Student")
        print("2. View Students")
        print("3. Update Student")
        print("4. Delete Student")
        print("5. Record Attendance")
        print("6. Record Grade")
        print("7. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            student_id = input("Enter Student ID: ")
            name = input("Enter Name: ")
            age = int(input("Enter Age: "))
            sms.add_student(student_id, name, age)
        
        elif choice == '2':
            sms.view_students()
        
        elif choice == '3':
            student_id = input("Enter Student ID to update: ")
            name = input("Enter new Name (leave blank to skip): ")
            age_input = input("Enter new Age (leave blank to skip): ")
            age = int(age_input) if age_input else None
            sms.update_student(student_id, name if name else None, age)
        
        elif choice == '4':
            student_id = input("Enter Student ID to delete: ")
            sms.delete_student(student_id)
        
        elif choice == '5':
            student_id = input("Enter Student ID for attendance: ")
            date = input("Enter Date (YYYY-MM-DD): ")
            status = input("Enter Status (Present/Absent): ")
            sms.record_attendance(student_id, date, status)
        
        elif choice == '6':
            student_id = input("Enter Student ID for grade: ")
            subject = input("Enter Subject: ")
            grade = float(input("Enter Grade: "))
            sms.record_grade(student_id, subject, grade)
        
        elif choice == '7':
            print("Exiting the system.")
            break
        
        else:
            print("Invalid choice! Please try again.")

if __name__ == "__main__":
    main()
