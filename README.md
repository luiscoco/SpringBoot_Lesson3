# SpringBoot_Lesson3

## Propmt for the Code Agent (Codex, Gemini Code Assistant or Copilot)

**Context**:

You are an AI assistant that helps refactor Spring Boot projects.

We are expanding the "Hello World" application from Lesson 2 to create a simple in-memory REST API for managing tasks.

We will not use a database yet; we will use a simple in-memory List.

**Task**:

Modify the previous Spring Boot project to implement a full CRUD API for tasks.

**Constraints**:

Spring Boot version: 3.3.0, Java 17, Maven.

Use @RestController, @GetMapping, @PostMapping, @GetMapping with @PathVariable, @RequestBody.

All data will be stored in an in-memory list within the controller for simplicity.

**Steps**:

Create a Java record named Task with fields: long id, String description, boolean completed. Records are a concise way to create immutable data classes in Java.

Create a new controller class named TaskController.java.

Inside TaskController, initialize a List<Task> to store the tasks and a counter for generating IDs.

Implement the following methods:

a. A method for GET /tasks that returns the list of all tasks.

b. A method for POST /tasks that accepts a Task object in the request body (without an ID), assigns a new ID, adds it to the list, and returns the newly created task with a 201 Created status code. You'll need to use the @RequestBody and @ResponseStatus(HttpStatus.CREATED) annotations.

c. A method for GET /tasks/{id} that finds a task by its ID in the list and returns it. If not found, it should ideally return a 404 error (the default behavior for returning null is often a 200 OK with an empty body, which is less ideal, but acceptable for this exercise).

Remove the old HelloController.java.

Provide a series of curl commands to test the new functionality: one to create a task, one to get all tasks, and one to get the specific task you created.

**Deliverables**:

src/main/java/com/example/demo/Task.java (new record)

src/main/java/com/example/demo/TaskController.java (new controller)

A list of curl commands to test the API.

**Acceptance Criteria**:

The application compiles and runs.

POST /tasks with a JSON body like {"description": "Learn Spring Boot", "completed": false} successfully adds a task to the in-memory list and returns a JSON response for the created task with an ID and a 201 Created status.

GET /tasks returns a JSON array containing the task(s) created.

GET /tasks/1 (assuming the first task got ID 1) returns the JSON for that specific task with a 200 OK status.
