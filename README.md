# codsoft_2
GUI to-do list
```python
import tkinter as tk

def add_task():
    task = task_entry.get()
    if task != "":
        var = tk.BooleanVar()
        checkbox = tk.Checkbutton(task_frame, text=task, variable=var, font="Arial 14", anchor="w")
        checkbox.var = var  # attach variable to widget
        checkbox.grid(row=len(tasks), column=0, sticky="nsew", padx=5, pady=2)
        tasks.append(checkbox)
        task_entry.delete(0, tk.END)

def delete_task():
    to_remove = [task for task in tasks if task.var.get()]
    for task in to_remove:
        task.grid_forget()
        tasks.remove(task)

def update_task():
    for task in tasks:
        if task.var.get():
            updated_text = task_entry.get()
            if updated_text:
                task.config(text=updated_text)
                task.var.set(False)
                task_entry.delete(0, tk.END)
            break

root = tk.Tk()
root.title("Responsive To-Do List with Features")

tasks = []
root.rowconfigure(2, weight=1)
root.columnconfigure(0, weight=1)

task_entry = tk.Entry(root, font="Arial 16")
task_entry.grid(row=0, column=0, sticky="ew", padx=10, pady=10)

button_frame = tk.Frame(root)
button_frame.grid(row=0, column=1, sticky="ew", padx=10)

add_btn = tk.Button(button_frame, text="Add", command=add_task, font="Arial 12")
add_btn.pack(side=tk.LEFT, fill=tk.X)

update_btn = tk.Button(button_frame, text="Update", command=update_task, font="Arial 12")
update_btn.pack(side=tk.LEFT, fill=tk.X)

delete_btn = tk.Button(button_frame, text="Delete", command=delete_task, font="Arial 12")
delete_btn.pack(side=tk.LEFT, fill=tk.X)

task_frame = tk.Frame(root)
task_frame.grid(row=2, column=0, columnspan=2, sticky="nsew", padx=10, pady=10)
task_frame.columnconfigure(0, weight=1)

root.mainloop()
```
