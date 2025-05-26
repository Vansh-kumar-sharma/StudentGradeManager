# StudentGradeManager
def calculate_grade(average):
    if average >= 90:
        return 'A'
    elif average >= 75:
        return 'B'
    elif average >= 60:
        return 'C'
    elif average >= 40:
        return 'D'
    else:
        return 'F'

students = []

def add_student():
    name = input("Enter student name: ")
    marks = []
    for i in range(1, 4):
        mark = float(input(f"Enter marks for subject {i}: "))
        marks.append(mark)

    average = sum(marks) / 3
    grade = calculate_grade(average)

    student = {
        'name': name,
        'marks': marks,
        'average': average,
        'grade': grade
    }

    students.append(student)
    print(f"\n{name} added with Grade: {grade}\n")

def display_students():
    if not students:
        print("No student records yet.\n")
        return

    print("\nStudent Records:")
    for s in students:
        print(f"Name: {s['name']}, Average: {s['average']:.2f}, Grade: {s['grade']}")
    print()

def save_to_file():
    with open("students.txt", "w") as f:
        for s in students:
            f.write(f"{s['name']},{s['marks']},{s['average']:.2f},{s['grade']}\n")
    print("Saved to students.txt\n")

def main():
    while True:
        print("1. Add Student")
        print("2. View All Students")
        print("3. Save to File")
        print("4. Exit")
        choice = input("Choose an option: ")

        if choice == '1':
            add_student()
        elif choice == '2':
            display_students()
        elif choice == '3':
            save_to_file()
        elif choice == '4':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Try again.\n")

main()
