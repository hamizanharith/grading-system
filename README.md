students = {}

def add_student_grades():
    name = input("Enter student's name: ")
    grades = {}
    grades["Bahasa Melayu"] = float(input("Enter mark for Bahasa Melayu: "))
    grades["English"] = float(input("Enter mark for English: "))
    grades["Math"] = float(input("Enter mark for Math: "))
    students[name] = grades
    print(f"Grades have been added for {name}.\n")

def calculate_average_grade(name):
    if name in students:
        grades = students[name]
        return sum(grades.values())/len(grades)
    else:
        print(f"Student {name} not found.\n")
        return None
    
def determine_letter_grade(average):
    if average >= 80:
        return 'A'
    elif average >= 60:
        return 'B'
    elif average >= 50:
        return 'C'
    elif average >= 40:
        return 'D'
    else:
        return 'F'
    
def display_report():
    for name, grades in students.items():
        average =  calculate_average_grade(name)
        letter_grade =  determine_letter_grade(average)
        print(f'''
Student: {name}
Bahasa Melayu: {grades["Bahasa Melayu"]:.2f}
English: {grades["English"]:.2f}
Math: {grades["Math"]:.2f}
Average: {average:.2f}
Letter Grade: {letter_grade}
''')

def menu():
    while True:
        print("Welcome to Simple Grading System")
        print("1. Add student grades")
        print("2. Display report")
        print("3. Exit")
        choice = input("Enter your choice: ")
        if choice == "1":
            add_student_grades()
        elif choice == "2":
            display_report()
        elif choice == "3":
            break
        else:
            print("Invalid choice. Please try again.")

menu()
