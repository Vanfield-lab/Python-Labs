import json

def load_tasks():
    try:
        with open("tasks.json", "r") as file:
            tasks = json.load(file)
    except FileNotFoundError:
        tasks = []
    return tasks

def save_tasks(tasks):
    with open("tasks.json", "w") as file:
        json.dump(tasks, file)

def show_menu():
    print("\n==== To-Do List App ====")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task as Completed")
    print("4. Delete Task")
    print("5. Exit")

def add_task(tasks):
    task = input("Enter the task: ")
    tasks.append({"task": task, "completed": False})
    save_tasks(tasks)
    print("Task added successfully!")

def view_tasks(tasks):
    if tasks:
        print("\n==== Tasks ====")
        for index, task in enumerate(tasks, start=1):
            status = "Completed" if task["completed"] else "Pending"
            print(f"{index}. {task['task']} - {status}")
    else:
        print("No tasks found.")

def mark_task_completed(tasks):
    view_tasks(tasks)
    try:
        index = int(input("Enter the task number to mark as completed: ")) - 1
        tasks[index]["completed"] = True
        save_tasks(tasks)
        print("Task marked as completed!")
    except (ValueError, IndexError):
        print("Invalid task number.")

def delete_task(tasks):
    view_tasks(tasks)
    try:
        index = int(input("Enter the task number to delete: ")) - 1
        del tasks[index]
        save_tasks(tasks)
        print("Task deleted successfully!")
    except (ValueError, IndexError):
        print("Invalid task number.")

def main():
    tasks = load_tasks()
    while True:
        show_menu()
        choice = input("Enter your choice: ")
        if choice == '1':
            add_task(tasks)
        elif choice == '2':
            view_tasks(tasks)
        elif choice == '3':
            mark_task_completed(tasks)
        elif choice == '4':
            delete_task(tasks)
        elif choice == '5':
            print("Exiting...")

            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")

if __name__ == "__main__":
    main()
