# Backpack 2: React, MongoDB, Node.js, and Express.js

---

## **Part 1: React JS (30 Questions)**

### **1. React Lifecycle (6 Questions)**

1. **What are the main phases of the React component lifecycle?**  
   The React component lifecycle consists of three main phases: **Mounting**, **Updating**, and **Unmounting**.

2. **What is the purpose of `componentDidMount()`?**  
   `componentDidMount()` is called after a component is rendered for the first time. It is used for tasks like fetching data or setting up subscriptions.

   **Example:**  
   ```javascript
   componentDidMount() {
       console.log("Component has been mounted!");
   }
   ```

3. **What is the difference between `componentDidUpdate()` and `componentWillUnmount()`?**  
   `componentDidUpdate()` is called after a component's updates are flushed to the DOM, while `componentWillUnmount()` is called just before a component is removed from the DOM.

4. **What is the purpose of `shouldComponentUpdate()`?**  
   `shouldComponentUpdate()` allows you to optimize performance by deciding whether a component should re-render or not.

   **Example:**  
   ```javascript
   shouldComponentUpdate(nextProps, nextState) {
       return this.state.value !== nextState.value;
   }
   ```

5. **What is the replacement for `componentWillMount()` in functional components?**  
   In functional components, the `useEffect` hook with an empty dependency array (`[]`) replaces `componentWillMount()`.

   **Example:**  
   ```javascript
   useEffect(() => {
       console.log("Component mounted!");
   }, []);
   ```

6. **What is the purpose of `getDerivedStateFromProps()`?**  
   `getDerivedStateFromProps()` is called right before rendering and is used to update the state based on changes in props.

   **Example:**  
   ```javascript
   static getDerivedStateFromProps(props, state) {
       if (props.value !== state.value) {
           return { value: props.value };
       }
       return null;
   }
   ```

---

### **2. Routing (6 Questions)**

7. **What is React Router?**  
   React Router is a library used for routing in React applications. It allows navigation between different components without reloading the page.

8. **How do you create a route in React Router?**  
   Use the `Route` component to define a route.

   **Example:**  
   ```javascript
   <Route path="/about" component={About} />
   ```

9. **What is the purpose of `useHistory()` in React Router?**  
   `useHistory()` provides access to the history instance, allowing you to navigate programmatically.

   **Example:**  
   ```javascript
   const history = useHistory();
   history.push("/home");
   ```

10. **What is the difference between `Link` and `NavLink`?**  
    `Link` is used for navigation, while `NavLink` adds an active class to the link when it matches the current URL.

    **Example:**  
    ```javascript
    <NavLink to="/about" activeClassName="active">About</NavLink>
    ```

11. **How do you handle 404 routes in React Router?**  
    Use a `Route` with no `path` or a `*` wildcard to handle 404 routes.

    **Example:**  
    ```javascript
    <Route path="*" component={NotFound} />
    ```

12. **What is the purpose of `useParams()`?**  
    `useParams()` is used to access dynamic parameters in the URL.

    **Example:**  
    ```javascript
    const { id } = useParams();
    ```

---

### **3. State Management (6 Questions)**

13. **What is state in React?**  
    State is a built-in object used to store data that can change over time and affect the component's rendering.

14. **What is the difference between state and props?**  
    State is managed within a component, while props are passed from a parent component.

15. **What is the purpose of `useState()`?**  
    `useState()` is a hook used to add state to functional components.

    **Example:**  
    ```javascript
    const [count, setCount] = useState(0);
    ```

16. **What is Redux?**  
    Redux is a state management library used to manage global state in React applications.

17. **What is the purpose of `useReducer()`?**  
    `useReducer()` is a hook used for complex state logic, similar to Redux.

    **Example:**  
    ```javascript
    const [state, dispatch] = useReducer(reducer, initialState);
    ```

18. **What is Context API?**  
    Context API is a built-in feature in React for sharing state across the component tree without passing props manually.

    **Example:**  
    ```javascript
    const MyContext = React.createContext();
    ```

---

### **4. Forms in React (6 Questions)**

19. **What are controlled components in React?**  
    Controlled components are form elements whose values are controlled by React state.

    **Example:**  
    ```javascript
    <input type="text" value={value} onChange={(e) => setValue(e.target.value)} />
    ```

20. **What is the purpose of `onSubmit` in forms?**  
    `onSubmit` is used to handle form submission.

    **Example:**  
    ```javascript
    <form onSubmit={handleSubmit}>
        <button type="submit">Submit</button>
    </form>
    ```

21. **How do you handle multiple inputs in a form?**  
    Use a single state object to manage multiple inputs.

    **Example:**  
    ```javascript
    const [formData, setFormData] = useState({ name: "", email: "" });
    ```

22. **What is Formik?**  
    Formik is a library for building forms in React, simplifying form handling and validation.

23. **What is the purpose of `useFormik()`?**  
    `useFormik()` is a hook provided by Formik to manage form state and validation.

    **Example:**  
    ```javascript
    const formik = useFormik({
        initialValues: { name: "" },
        onSubmit: values => console.log(values),
    });
    ```

24. **How do you validate forms in React?**  
    Use libraries like Formik or Yup for form validation.

    **Example:**  
    ```javascript
    const schema = Yup.object().shape({
        name: Yup.string().required("Name is required"),
    });
    ```

---

### **5. React Authentication (6 Questions)**

25. **What is JWT?**  
    JWT (JSON Web Token) is a compact, URL-safe token used for authentication and authorization.

26. **How do you store JWT in the browser?**  
    Store JWT in `localStorage` or `sessionStorage`.

    **Example:**  
    ```javascript
    localStorage.setItem("token", jwtToken);
    ```

27. **What is the purpose of `useEffect()` in authentication?**  
    `useEffect()` is used to check authentication status when the component mounts.

    **Example:**  
    ```javascript
    useEffect(() => {
        if (!isAuthenticated) {
            history.push("/login");
        }
    }, []);
    ```

28. **What is OAuth?**  
    OAuth is an open standard for access delegation, commonly used for third-party authentication.

29. **How do you implement protected routes in React?**  
    Use a higher-order component (HOC) or a custom hook to check authentication before rendering a route.

    **Example:**  
    ```javascript
    const ProtectedRoute = ({ component: Component, ...rest }) => (
        <Route {...rest} render={(props) => (
            isAuthenticated ? <Component {...props} /> : <Redirect to="/login" />
        )} />
    );
    ```

30. **What is the purpose of `axios` in authentication?**  
    `axios` is used to send authenticated requests with JWT tokens.

    **Example:**  
    ```javascript
    axios.get("/api/data", { headers: { Authorization: `Bearer ${token}` } });
    ```

---

## **Part 2: MongoDB (20 Questions)**

### **1. CRUD Operations (5 Questions)**

1. **What is MongoDB?**  
   MongoDB is a NoSQL database that stores data in flexible, JSON-like documents.

2. **How do you insert a document in MongoDB?**  
   Use the `insertOne()` or `insertMany()` methods.

   **Example:**  
   ```javascript
   db.collection.insertOne({ name: "John", age: 30 });
   ```

3. **How do you update a document in MongoDB?**  
   Use the `updateOne()` or `updateMany()` methods.

   **Example:**  
   ```javascript
   db.collection.updateOne({ name: "John" }, { $set: { age: 31 } });
   ```

4. **How do you delete a document in MongoDB?**  
   Use the `deleteOne()` or `deleteMany()` methods.

   **Example:**  
   ```javascript
   db.collection.deleteOne({ name: "John" });
   ```

5. **What is the purpose of `find()` in MongoDB?**  
   `find()` is used to query documents in a collection.

   **Example:**  
   ```javascript
   db.collection.find({ age: { $gt: 25 } });
   ```

---

### **2. Querying (5 Questions)**

6. **What is the purpose of `$gt` in MongoDB?**  
   `$gt` is used to find documents where a field's value is greater than a specified value.

   **Example:**  
   ```javascript
   db.collection.find({ age: { $gt: 25 } });
   ```

7. **How do you sort documents in MongoDB?**  
   Use the `sort()` method.

   **Example:**  
   ```javascript
   db.collection.find().sort({ age: 1 });
   ```

8. **What is the purpose of `$in` in MongoDB?**  
   `$in` is used to find documents where a field's value matches any value in an array.

   **Example:**  
   ```javascript
   db.collection.find({ age: { $in: [25, 30] } });
   ```

9. **How do you limit the number of documents returned in a query?**  
   Use the `limit()` method.

   **Example:**  
   ```javascript
   db.collection.find().limit(10);
   ```

10. **What is the purpose of `$regex` in MongoDB?**  
    `$regex` is used to perform pattern matching in queries.

    **Example:**  
    ```javascript
    db.collection.find({ name: { $regex: /^J/ } });
    ```

---

### **3. Integration with Node.js (5 Questions)**

11. **How do you connect MongoDB to a Node.js application?**  
    Use the `mongoose` library or the native MongoDB driver.

    **Example:**  
    ```javascript
    mongoose.connect("mongodb://localhost:27017/mydb");
    ```

12. **What is Mongoose?**  
    Mongoose is an ODM (Object Data Modeling) library for MongoDB and Node.js.

13. **How do you define a schema in Mongoose?**  
    Use the `Schema` class.

    **Example:**  
    ```javascript
    const userSchema = new mongoose.Schema({ name: String, age: Number });
    ```

14. **What is the purpose of `mongoose.model()`?**  
    `mongoose.model()` is used to create a model from a schema.

    **Example:**  
    ```javascript
    const User = mongoose.model("User", userSchema);
    ```

15. **How do you query documents using Mongoose?**  
    Use the `find()` method.

    **Example:**  
    ```javascript
    User.find({ age: { $gt: 25 } });
    ```

---

### **4. Indexing in MongoDB (5 Questions)**

16. **What is indexing in MongoDB?**  
    Indexing improves query performance by creating indexes on fields.

17. **How do you create an index in MongoDB?**  
    Use the `createIndex()` method.

    **Example:**  
    ```javascript
    db.collection.createIndex({ name: 1 });
    ```

18. **What is a compound index?**  
    A compound index is an index on multiple fields.

    **Example:**  
    ```javascript
    db.collection.createIndex({ name: 1, age: -1 });
    ```

19. **What is the purpose of `explain()` in MongoDB?**  
    `explain()` provides information about query execution.

    **Example:**  
    ```javascript
    db.collection.find({ age: 25 }).explain();
    ```

20. **What is a unique index?**  
    A unique index ensures that no two documents have the same value for the indexed field.

    **Example:**  
    ```javascript
    db.collection.createIndex({ email: 1 }, { unique: true });
    ```

---

## **Part 3: Node.js (20 Questions)**

### **1. Basic Server (5 Questions)**

1. **What is Node.js?**  
   Node.js is a runtime environment for executing JavaScript on the server.

2. **How do you create a basic server in Node.js?**  
   Use the `http` module.

   **Example:**  
   ```javascript
   const http = require("http");
   const server = http.createServer((req, res) => {
       res.end("Hello, World!");
   });
   server.listen(3000);
   ```

3. **What is the purpose of `require()` in Node.js?**  
   `require()` is used to import modules in Node.js.

4. **What is `package.json`?**  
   `package.json` is a file that contains metadata about a Node.js project, including dependencies.

5. **How do you install dependencies in Node.js?**  
   Use the `npm install` command.

   **Example:**  
   ```bash
   npm install express
   ```

---

### **2. File System (5 Questions)**

6. **What is the `fs` module in Node.js?**  
   The `fs` module is used to interact with the file system.

7. **How do you read a file in Node.js?**  
   Use the `fs.readFile()` method.

   **Example:**  
   ```javascript
   fs.readFile("file.txt", "utf8", (err, data) => {
       console.log(data);
   });
   ```

8. **How do you write to a file in Node.js?**  
   Use the `fs.writeFile()` method.

   **Example:**  
   ```javascript
   fs.writeFile("file.txt", "Hello, World!", (err) => {
       if (err) throw err;
   });
   ```

9. **What is the purpose of `fs.appendFile()`?**  
   `fs.appendFile()` is used to append data to a file.

   **Example:**  
   ```javascript
   fs.appendFile("file.txt", "New Data", (err) => {
       if (err) throw err;
   });
   ```

10. **How do you delete a file in Node.js?**  
    Use the `fs.unlink()` method.

    **Example:**  
    ```javascript
    fs.unlink("file.txt", (err) => {
        if (err) throw err;
    });
    ```

---

### **3. Middleware (5 Questions)**

11. **What is middleware in Node.js?**  
    Middleware is a function that has access to the request and response objects and can modify them.

12. **What is the purpose of `app.use()` in Express.js?**  
    `app.use()` is used to register middleware in Express.js.

    **Example:**  
    ```javascript
    app.use((req, res, next) => {
        console.log("Middleware executed!");
        next();
    });
    ```

13. **What is `body-parser`?**  
    `body-parser` is middleware used to parse incoming request bodies.

    **Example:**  
    ```javascript
    app.use(bodyParser.json());
    ```

14. **What is the purpose of `next()` in middleware?**  
    `next()` is used to pass control to the next middleware function.

15. **How do you create custom middleware in Express.js?**  
    Define a function that takes `req`, `res`, and `next` as parameters.

    **Example:**  
    ```javascript
    const logger = (req, res, next) => {
        console.log(`${req.method} ${req.url}`);
        next();
    };
    app.use(logger);
    ```

---

### **4. Single-Threaded Application (5 Questions)**

16. **What does it mean for Node.js to be single-threaded?**  
    Node.js uses a single thread to handle requests, but it can perform non-blocking I/O operations.

17. **What is the event loop in Node.js?**  
    The event loop is a mechanism that allows Node.js to perform non-blocking I/O operations.

18. **What is `process.nextTick()`?**  
    `process.nextTick()` is used to schedule a callback to be executed in the next iteration of the event loop.

    **Example:**  
    ```javascript
    process.nextTick(() => {
        console.log("Next tick!");
    });
    ```

19. **What is the purpose of `setImmediate()`?**  
    `setImmediate()` is used to execute a callback after the current event loop cycle.

    **Example:**  
    ```javascript
    setImmediate(() => {
        console.log("Immediate!");
    });
    ```

20. **What is the difference between `setTimeout()` and `setImmediate()`?**  
    `setTimeout()` schedules a callback after a specified delay, while `setImmediate()` schedules a callback to be executed in the next event loop cycle.

---

## **Part 4: Express.js (20 Questions)**

### **1. Request and Response (5 Questions)**

1. **What is Express.js?**  
   Express.js is a web application framework for Node.js.

2. **How do you handle GET requests in Express.js?**  
   Use the `app.get()` method.

   **Example:**  
   ```javascript
   app.get("/", (req, res) => {
       res.send("Hello, World!");
   });
   ```

3. **What is the purpose of `req.params`?**  
   `req.params` is used to access route parameters.

   **Example:**  
   ```javascript
   app.get("/users/:id", (req, res) => {
       const userId = req.params.id;
   });
   ```

4. **What is the purpose of `req.query`?**  
   `req.query` is used to access query parameters.

   **Example:**  
   ```javascript
   app.get("/search", (req, res) => {
       const query = req.query.q;
   });
   ```

5. **How do you send a JSON response in Express.js?**  
   Use the `res.json()` method.

   **Example:**  
   ```javascript
   res.json({ message: "Hello, World!" });
   ```

---

### **2. Error Handling (5 Questions)**

6. **How do you handle errors in Express.js?**  
   Use middleware with four parameters (`err`, `req`, `res`, `next`).

   **Example:**  
   ```javascript
   app.use((err, req, res, next) => {
       res.status(500).send("Something went wrong!");
   });
   ```

7. **What is the purpose of `next(err)`?**  
   `next(err)` is used to pass an error to the next error-handling middleware.

8. **How do you handle 404 errors in Express.js?**  
   Use a middleware at the end of all routes.

   **Example:**  
   ```javascript
   app.use((req, res) => {
       res.status(404).send("Page not found!");
   });
   ```

9. **What is the purpose of `res.status()`?**  
   `res.status()` is used to set the HTTP status code of the response.

   **Example:**  
   ```javascript
   res.status(404).send("Not Found");
   ```

10. **How do you log errors in Express.js?**  
    Use `console.error()` or a logging library like `winston`.

    **Example:**  
    ```javascript
    app.use((err, req, res, next) => {
        console.error(err.stack);
        res.status(500).send("Internal Server Error");
    });
    ```

---

### **3. Connecting with MongoDB (5 Questions)**

11. **How do you connect Express.js to MongoDB?**  
    Use the `mongoose` library.

    **Example:**  
    ```javascript
    mongoose.connect("mongodb://localhost:27017/mydb");
    ```

12. **What is the purpose of `mongoose.connection`?**  
    `mongoose.connection` is used to access the MongoDB connection.

    **Example:**  
    ```javascript
    mongoose.connection.on("connected", () => {
        console.log("Connected to MongoDB");
    });
    ```

13. **How do you define a model in Mongoose?**  
    Use the `mongoose.model()` method.

    **Example:**  
    ```javascript
    const User = mongoose.model("User", userSchema);
    ```

14. **How do you perform CRUD operations in Express.js with MongoDB?**  
    Use Mongoose methods like `find()`, `save()`, `updateOne()`, and `deleteOne()`.

    **Example:**  
    ```javascript
    app.get("/users", async (req, res) => {
        const users = await User.find();
        res.json(users);
    });
    ```

15. **What is the purpose of `mongoose.Schema`?**  
    `mongoose.Schema` is used to define the structure of documents in a collection.

    **Example:**  
    ```javascript
    const userSchema = new mongoose.Schema({ name: String, age: Number });
    ```

---

### **4. Scaffolding (5 Questions)**

16. **What is scaffolding in Express.js?**  
    Scaffolding is the process of generating a basic project structure automatically.

17. **What is `express-generator`?**  
    `express-generator` is a tool to create an Express.js application skeleton.

    **Example:**  
    ```bash
    npx express-generator myapp
    ```

18. **What is the purpose of `bin/www` in an Express.js project?**  
    `bin/www` is the entry point for starting the Express.js server.

19. **How do you run an Express.js application?**  
    Use the `npm start` command.

    **Example:**  
    ```bash
    npm start
    ```

20. **What is the purpose of `app.set()` in Express.js?**  
    `app.set()` is used to configure application settings.

    **Example:**  
    ```javascript
    app.set("view engine", "ejs");
    ```



    Create by [Fakrul-Hossain](https://github.com/fakrul-hossain).

