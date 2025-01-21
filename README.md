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

```jvascript
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
# Event Loop
