<h1 align="center" style="color:#2F4F4F;">Auth & Expense Management System</h1>

<p align="center">
    <img src="https://imgs.search.brave.com/7DSG7nhZAi4fvXfz-rcLd0copinI974vTx5bd3rCCdQ/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9pbWdj/ZG4uc3RhYmxlZGlm/ZnVzaW9ud2ViLmNv/bS8yMDI0LzMvMTgv/MzJhYmQ1MTAtMGYy/Ni00MDEzLWI2MTEt/YTVjNTIzNGJlN2U5/LmpwZw" alt="Project Logo" width="200"/>
</p>

<h2>🚀 Overview</h2>
<p>
This project is a robust microservices-based system that handles JWT token authentication, authorization, and expense management. It leverages Kafka for inter-service communication and Redis for caching while integrating OpenAI LangChain for processing bank transaction messages.
</p>

<hr>

<h2>🖥️ Frontend Overview</h2>

<p>
The frontend of this project is built using <strong>ReactJS</strong> to provide a seamless user experience for authentication, expense management, and transaction insights. It features an interactive and responsive UI powered by Context API for state management.
</p>

<h3>🔹 Key Features</h3>
<ul>
    <li><strong>Authentication & Authorization</strong> – Secure login with JWT tokens.</li>
    <li><strong>Expense Management</strong> – Users can add, edit, and delete expenses.</li>
    <li><strong>Data Visualization</strong> – Expense trends displayed via charts.</li>
    <li><strong>State Management</strong> – Utilizes Context API for efficient global state handling.</li>
    <li><strong>Responsive UI</strong> – Optimized design for different devices.</li>
</ul>
<img src="https://github.com/Saiharshith17/ExpenseTrackerProject/blob/main/img.png" alt="Architecture Diagram" width="100%"/>

<h2>🛠️ Services</h2>

<h3>1. 🔐 AuthService</h3>
<ul>
    <li>Handles JWT authentication and user authorization.</li>
    <li>Generates Access & Refresh Tokens.</li>
    <li>Utilizes Redis for token caching.</li>
</ul>

<h3>2. 👤 UserService</h3>
<ul>
    <li>Processes user-related requests (e.g., <code>getUserDetails</code>).</li>
    <li>Integrated with Kafka for communication.</li>
    <li>Uses Redis for caching user data.</li>
</ul>

<h3>3. 🔄 IntegrationService</h3>
<ul>
    <li>Integrates OpenAI LangChain.</li>
    <li>Converts bank transaction details to JSON format.</li>
    <li>Uses refresh tokens to communicate with ExpenseService via Kafka.</li>
</ul>

<h3>4. 💰 ExpenseService</h3>
<ul>
    <li>Manages operations like <code>getExpense</code>, <code>addExpense</code>, etc.</li>
    <li>Secures API endpoints using Kong API Gateway.</li>
    <li>Handles real-time data via Kafka.</li>
</ul>

<hr>

<h2>🛠️ Technologies Used</h2>
<table>
    <tr>
        <th>Category</th>
        <th>Technologies</th>
    </tr>
    <tr>
        <td>Frontend</td>
        <td>ReactJS, JavaScript, HTML, CSS, Context API</td>
    </tr>
    <tr>
        <td>Backend</td>
        <td>Java, Spring Boot, Groovy, RESTful API, Hibernate</td>
    </tr>
    <tr>
        <td>Database</td>
        <td>MySQL</td>
    </tr>
    <tr>
        <td>Caching & Messaging</td>
        <td>Redis, Kafka</td>
    </tr>
    <tr>
        <td>Other Tools</td>
        <td>Docker, OpenAI LangChain, Kong API Gateway</td>
    </tr>
</table>

<hr>

<h2>📌 Architecture Overview</h2>
<img src="https://github.com/Saiharshith17/ExpenseTrackerProject/blob/main/Architecture.png" alt="Architecture Diagram" width="100%"/>


<p>
The architecture follows a microservices pattern where:
</p>
<ul>
    <li>🔑 <b>AuthService</b> manages authentication & authorization.</li>
    <li>🧑 <b>UserService</b> handles user data and integrates with Kafka.</li>
    <li>🤖 <b>IntegrationService</b> processes transactions with OpenAI LangChain.</li>
    <li>💰 <b>ExpenseService</b> handles all expense-related operations.</li>
</ul>

<hr>

<h2>⚙️ Setup Instructions</h2>

<pre>
<b>1. Clone the repository:</b>
$ git clone &lt;repo-url&gt;
$ cd &lt;project-directory&gt;

<b>2. Setup environment variables:</b>
- Configure database connections.
- Set JWT secret keys.
- Define Kafka topics.
- Configure Redis settings.

<b>3. Run services:</b>
$ docker-compose up -d

<b>4. Start Frontend:</b>
$ cd frontend
$ npm install
$ npm start
</pre>

<hr>

<h2>🔗 API Endpoints</h2>

<table>
  <tr>
    <th>Service</th>
    <th>Method</th>
    <th>Endpoint</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>AuthService</td>
    <td>POST</td>
    <td>/auth/v1/login</td>
    <td>Authenticate user and issue access token</td>
  </tr>
  <tr>
    <td>AuthService</td>
    <td>POST</td>
    <td>/auth/v1/refreshToken</td>
    <td>Generate a new access token using a refresh token</td>
  </tr>
  <tr>
    <td>AuthService</td>
    <td>POST</td>
    <td>/auth/v1/signup</td>
    <td>Register a new user</td>
  </tr>
  <tr>
    <td>UserService</td>
    <td>GET</td>
    <td>/user/v1/details</td>
    <td>Fetch user details</td>
  </tr>
  <tr>
    <td>ExpenseService</td>
    <td>GET</td>
    <td>/expense/v1/getExpense</td>
    <td>Retrieve a list of expenses</td>
  </tr>
  <tr>
    <td>ExpenseService</td>
    <td>POST</td>
    <td>/expense/v1/addExpense</td>
    <td>Add a new expense</td>
  </tr>
  <tr>
    <td>ExpenseService</td>
    <td>DELETE</td>
    <td>/expense/v1/removeExpense</td>
    <td>Remove an expense</td>
  </tr>
  <tr>
    <td>IntegrationService</td>
    <td>POST</td>
    <td>/v1/ds/message</td>
    <td>Process and convert bank transaction messages</td>
  </tr>
  <tr>
    <td>Health Check</td>
    <td>GET</td>
    <td>/health</td>
    <td>Check service health status</td>
  </tr>
</table>


<hr>

<h2>🚀 Future Enhancements</h2>
<ul>
    <li>Implement rate limiting and security hardening.</li>
    <li>Introduce a notification service for real-time updates.</li>
    <li>Optimize caching strategies for better performance.</li>
</ul>

<hr>

<h2>🤝 Contributing</h2>
<ul>
    <li>Fork the repository.</li>
    <li>Create a new branch.</li>
    <li>Commit and push changes.</li>
    <li>Submit a pull request.</li>
</ul>

<hr>

<h2>📜 License</h2>
<p>This project is licensed under the MIT License.</p>

<h2>📧 Contact</h2>
<p>For queries, please reach out to <b>eedarasaiharshith6699@gmail.com</b></p>
