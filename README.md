# JS---Kanban-board

A minimal kanban board, where you can drag and drop "tasks" that you imput, from ToDo to In Progress and then to Done. There is also a button on each task that has a delete functionality.

![image](https://github.com/user-attachments/assets/d6902ed4-15d1-4657-9072-9dc7297f873f)

The board was developed using HTML, CSS and Vanilla JavaScript.

Each task is saved using the browsers local Storage. There is an event listener that loads the tasks on the page from local storage once the DOM content is loaded.

There is a `addTask()` function that takes in a parameter called 'coloumnId'. This function gets the taskInput from the input html elelment on the page and firstly trims the value, then if the taskContent is not an empty string, a newTask is created and pushed to the task array. The function then updates the local storage and rendersTasks to the page, it then sets the taskInput value to an empty string.

There is a `createTaskElement()` function that takes in two parameters (content and id), this function creates a new div element and adds a number of attributes, also updates the innerHTML with the content that has been inputted.

To render the tasks onto the page, there is a `renderTask()` function that utilises the forEach method and iterates over each column (todo, in progress and done), sets the innerHTML to an empty string, then iterates over each task in the tasks array and using the `createTaskElement()` function, creates the task elements then appends this to the correct column's task container.

The `updateLocalStorage()` function does exactly that, it updates the local storage with and new tasks that has been added or removed from the tasks array. As local browser storage can only store strings, this function takes the tasks array and converts it into a json string, using JSON.stringify.

The `updateTaskStatus()` function takes in the taskId and newStatus as parameters. It then maps over the tasks array and checks if the taskId is a strict match to the task.id in the array, if it is then it then updates the status of that task with the newStatus value, than calls the `updateLocalStorage()` function to update the local storage.

The `deleteTask()` function does exactly that, deletes the task from the tasks array using the taskId, then calls the `updateLocalStorage()` function then `renderTasks()` function.

The drag and drop functionality is created using the below function - 

`drag()` function takes in the event object from the created element that has the attribute 'draggable' set to true, and uses the dataTransfer.setData() method that stores the id of the dragged element for later use. 

`drop()` function takse in the event object and columnId. Using the dataTransfer.getData() method, it grabs the id of the dragged element, checks that it is a valid dragged element, it then calls the `updateTaskStatus()` fuction passing in the task data/id and the taskStatus, then appends the draggedElement to the new task container.

