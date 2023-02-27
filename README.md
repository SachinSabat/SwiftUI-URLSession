# Practice-iOS

Before starting this task, note that understanding and following the instructions is valued more 
than the final outcome of the project! Please read and understand the tasks carefully and we're happy 
to help if you have questions about an instruction, step or any given requirement.

Critical steps:

#### Step 1. Create a branch named `dev` where all the development of this project will take place. 
This branch must originate from the `master` branch. Do not bring any file/s from other projects into this project. 

#### Step 2. Understand the project and the given tasks. 
Read the README file in full, analyse each file in this template and understand the design of the project. 
Ask questions if there is anything unclear.

#### Step 3. There are 3 tasks and one additional bonus task. The first 3 tasks must be commited at each stage. 
This means, make sure to push a commit with a clear commit message at the end of each task. 
Do not wait until the whole project is complete to push commits of each stage. 
You may have more than 3 commits however the minimum is 3 commits (at least 1 for each task) in this project. 


It is advised to commit the progress of the task and create a pull request with ``nets-dev``
Github account as reviewer when the task is complete. 

Please actively participate in the pull request review discussion during the review period
which will take place in the github pull request comments section. 

## Task description in order of importance:

(Please reach out if any part of the task description is unclear, we'll be happy to elaborate)

### Use:

* SwiftUI 
* URLSession

---

* Git - intelligible and short commit messages at each stage of the project progress 
* Code comment - add code comment when necessary (Do not comment everything). (See how the template code comments look like)
* Indentation - according to Apple's official guidelines/conventions 
* Naming (properties, functions, classes…) - according to Apple's official guidelines/conventions 

### Summary: 

The app should show list of users in rows. 
(This list is retrieved from: [https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users) )

Each row should show: id, name, email, city and company name.
**Note:** Do not include any other information, e.g. phone number, zipcode...

Upon selecting a row from the list,
display Name and id of the selected user on top and
the app should re-fetch the list and exclude the user on the selected row.
e.g. If a user with id = 3 is selected, exclude this user from fetch result.
Subsequently, if a user with id = 1 is selected, exclude only this user
(and not the previously selected user with id = 3)

### Task 1: SwiftUI implementation of given UI design

* Implement a UI using SwiftUI according to the design in the image Design.png located in the project folder. 
* You may use dummy data to populate the list at this stage. 

### Task 2: Implement a simple REST client that asynchronously fetches JSON 

Fetch a users list from source: `https://jsonplaceholder.typicode.com/users`.
Use URLSession, however, the implementation should not contain any unused code, e.g. from another project or template. 
This project contains an ``API`` with a `fetchUsers` contract (shown below) that should be used to achieve this task.

```
    /// Asynchronously fetch users list and return the response in reverse order than received.
    /// Upon failure, return the error through the `failure` callback. otherwise, return the list in `success` callback.
    /// The  user with an ID that matches the given `ownerID` must be excluded (filtered out) from the list.
    ///
    /// - Parameters:
    ///   - ownerID: A user ID indicating the owner of this API. (This user must not appear in the user list returned to the caller)
    ///   - success: Invoked with users list upon successful fetch.
    ///   - failure: Invoked with an error of type `FetchError` indicating the specific failure case.
    func fetchUsers(
        ownerID: String,
        success: @escaping (UsersList) -> Void,
        failure: @escaping (FetchError) -> Void
    )
```

* Use Swift's Decoding Custom Type to deserialize the JSON response. Define these data-types in `APITypes.swift` file. 
* After obtaining the users list, always return the list to the caller in reverse order

### Task 3: Integrate networking client
In this step, integrate the data retreived via the networking client and the UI implemented in task 1. 
When user selects a row in the list, the user ID in this row should be passed to the API as the `ownerID` 
and the new list should populate list view in the UI. 

### Task 4 (Bonus) : Write unit tests for the units you see need testing
