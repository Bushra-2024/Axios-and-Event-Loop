# Axios-and-Event-Loop

![image](https://github.com/user-attachments/assets/6b1fcb49-cdf1-46ca-85a8-91db74b0350c)



# What is Axios?

Axios is a library that makes it simple to send HTTP requests from a browser or a Node.js environment. It's like the built-in fetch API, but with extra features that make it more powerful and easier to use.


### Why use Axios?

- **Simpler Syntax**: Axios automatically formats the request and handles common tasks like JSON parsing.
- **Node.js and Browser Support**: Works seamlessly in both environments.
- **Automatic JSON Handling**: Parses JSON responses and converts request data to JSON if needed.
- **Built-in Features**: Includes request cancellation, timeout settings, and response interceptors.

EXAMPLE :
```javascript
//Get
async function getUsers(params = "") {
    try {
        let {data} = await axios.get(`${apiURL}${params}`)
        get(data)         
    } catch (error) {
        console.error("Error fetching data:", error.message);
    }
} 
getUsers()
```

```javascript
//Delete
async function DeleteUser(id){
    try {
        await axios.delete(`${apiURL}/${id}`)
        getUsers()
    } catch (error) {
        console.error(error);  
    }
}
```

```javascript
//post,add
async function postUser(user) {
    try {
        await axios.post(apiURL,user)
      getUsers()
    } catch (error) {
        console.error(error);
    }
}
```

```javascript
//edit,put
async function putUser(user) {
    try {
        await axios.put(`${apiURL}/${user.id}`,user)
        getUsers()
    } catch (error) {
        console.error(error);
    }
}
```

---

![image](https://github.com/user-attachments/assets/90010753-7aa0-4788-bc3b-d52c6fe7be6d)



# Event Loop

The Event Loop in JavaScript is a mechanism that ensures smooth execution of code, especially when dealing with asynchronous tasks. It enables JavaScript to handle non-blocking operations and allows multiple tasks to run without halting the main thread.

### Key Components 

1. **Call Stack**: 
   - The call stack is where synchronous code is executed. 
   - Each function call is added to the stack, and once completed, it is removed.
   - Only synchronous code runs directly on the call stack.

2. **Web APIs**:
   - Asynchronous tasks like setTimeout, setInterval, or DOM events are handled by Web APIs provided by the browser or Node.js.
   - These tasks run outside the main call stack to avoid blocking the execution.

3. **Callback Queue**:
   - Once an asynchronous task completes in the Web API, its associated callback is sent to the **callback queue**.
   - The event loop checks the callback queue and moves tasks to the call stack when it is empty.

4. **Microtasks and Macrotasks**:
   - **Microtasks**: Include tasks like Promises or MutationObserver. They have higher priority than macrotasks.
   - **Macrotasks**: Include tasks like setTimeout, setInterval, or setImmediate.
   - After each synchronous execution, the event loop clears all microtasks before moving on to the macrotasks.

---

### Simplified Explanation of the Event Loop Workflow:

1. **Synchronous Code**:
   - All synchronous tasks are executed first, one by one, on the call stack.

2. **Asynchronous Code**:
   - Functions like setTimeout or fetch are sent to Web APIs. These APIs process them and send their callbacks to the respective queues (microtask or macrotask) once completed.

3. **Microtasks First**:
   - The event loop prioritizes microtasks (like `Promise.then) and executes them before processing any macrotask.

4. **Macrotasks Next**:
   - After clearing all microtasks, the event loop moves to macrotasks (like setTimeout).

---

### Example to Clarify the Event Loop:

```javascript
console.log('Start'); // Synchronous, added to the call stack

setTimeout(() => {
  console.log('Timeout'); // Macrotask
}, 0);

Promise.resolve().then(() => {
  console.log('Promise'); // Microtask
});

console.log('End'); // Synchronous, added to the call stack
```

**Output**:
```
Start
End
Promise
Timeout
```


