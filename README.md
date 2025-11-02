# 📝 Full Stack Todo List Application

A modern, feature-rich Todo List application built with **Spring Boot** backend and **React** frontend. Manage your tasks efficiently with priority levels, categories, due dates, and more!

![Java](https://img.shields.io/badge/Java-17+-orange?style=flat&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?style=flat&logo=spring)
![React](https://img.shields.io/badge/React-18+-blue?style=flat&logo=react)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

## ✨ Features

### Backend Features
- ✅ RESTful API with Spring Boot
- ✅ CRUD operations for todos
- ✅ H2 in-memory database
- ✅ JPA/Hibernate for data persistence
- ✅ CORS configuration for frontend integration
- ✅ User management support
- ✅ Priority levels (HIGH, MEDIUM, LOW)
- ✅ Category-based organization
- ✅ Due date tracking
- ✅ Automatic timestamps (createdAt, updatedAt)

### Frontend Features
- ✅ Modern, responsive UI design
- ✅ Real-time CRUD operations
- ✅ Task filtering (All, Active, Completed)
- ✅ Priority-based color coding
- ✅ Category tags
- ✅ Due date display
- ✅ Statistics dashboard
- ✅ Loading states and error handling
- ✅ Smooth animations
- ✅ Mobile-friendly design

## 🚀 Quick Start

### Prerequisites
- **Java 17+** installed
- **Node.js 16+** and npm installed
- **Maven** installed (or use the included Maven wrapper)
- **Git** (optional, for cloning)

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd todo-backend
   ```

2. **Run the Spring Boot application:**
   ```bash
   ./mvnw spring-boot:run
   ```
   
   Or if using Windows:
   ```cmd
   mvnw.cmd spring-boot:run
   ```

3. **Verify backend is running:**
   - Open browser: `http://localhost:8080/api/todos`
   - You should see an empty array `[]` or existing todos

### Frontend Setup

1. **Navigate to frontend directory:**
   ```bash
   cd todo-frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the React application:**
   ```bash
   npm start
   ```

4. **Access the application:**
   - Open browser: `http://localhost:3000`
   - The app should automatically open

## 📁 Project Structure

```
To-Do-List/
├── todo-backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/todo/
│   │   │   │   ├── SpringBootTodoBackendApplication.java
│   │   │   │   ├── config/
│   │   │   │   │   └── CorsConfig.java
│   │   │   │   ├── controller/
│   │   │   │   │   └── TodoController.java
│   │   │   │   ├── model/
│   │   │   │   │   ├── Todo.java
│   │   │   │   │   └── User.java
│   │   │   │   ├── repository/
│   │   │   │   │   ├── TodoRepository.java
│   │   │   │   │   └── UserRepository.java
│   │   │   │   └── service/
│   │   │   │       ├── TodoService.java
│   │   │   │       └── UserService.java
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   ├── pom.xml
│   └── mvnw
│
└── todo-frontend/
    ├── public/
    ├── src/
    │   ├── App.js
    │   ├── App.css
    │   ├── api.js
    │   ├── TodoList.js
    │   ├── TodoList.css
    │   ├── TodoForm.js
    │   ├── TodoForm.css
    │   ├── TodoItem.js
    │   ├── TodoItem.css
    │   └── index.js
    ├── package.json
    └── README.md
```

## 🔌 API Endpoints

### Base URL
```
http://localhost:8080/api/todos
```

### Available Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/todos` | Get all todos |
| GET | `/api/todos/{id}` | Get todo by ID |
| POST | `/api/todos` | Create new todo |
| PUT | `/api/todos/{id}` | Update existing todo |
| DELETE | `/api/todos/{id}` | Delete todo |
| GET | `/api/todos/user/{userId}` | Get todos by user ID |

### Request/Response Examples

#### Create Todo (POST)
```json
POST http://localhost:8080/api/todos
Content-Type: application/json

{
  "title": "Learn Spring Boot",
  "description": "Complete the tutorial",
  "completed": false,
  "priority": "HIGH",
  "category": "Learning",
  "dueDate": "2025-11-15"
}
```

**Response (201 Created):**
```json
{
  "id": 1,
  "title": "Learn Spring Boot",
  "description": "Complete the tutorial",
  "completed": false,
  "priority": "HIGH",
  "category": "Learning",
  "dueDate": "2025-11-15",
  "createdAt": "2025-11-01T12:00:00",
  "updatedAt": "2025-11-01T12:00:00",
  "user": null
}
```

#### Get All Todos (GET)
```json
GET http://localhost:8080/api/todos

Response (200 OK):
[
  {
    "id": 1,
    "title": "Learn Spring Boot",
    "description": "Complete the tutorial",
    "completed": false,
    "priority": "HIGH",
    "category": "Learning",
    "dueDate": "2025-11-15",
    "createdAt": "2025-11-01T12:00:00",
    "updatedAt": "2025-11-01T12:00:00",
    "user": null
  }
]
```

#### Update Todo (PUT)
```json
PUT http://localhost:8080/api/todos/1
Content-Type: application/json

{
  "title": "Learn Spring Boot - COMPLETED",
  "description": "Tutorial finished!",
  "completed": true,
  "priority": "HIGH",
  "category": "Learning",
  "dueDate": "2025-11-15"
}
```

#### Delete Todo (DELETE)
```
DELETE http://localhost:8080/api/todos/1

Response: 204 No Content
```

## 🧪 Testing with Postman

### Import Collection
1. Open Postman
2. Click **Import**
3. Paste this collection:

```json
{
  "info": {
    "name": "Todo API Tests",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "item": [
    {
      "name": "Get All Todos",
      "request": {
        "method": "GET",
        "url": "http://localhost:8080/api/todos"
      }
    },
    {
      "name": "Create Todo",
      "request": {
        "method": "POST",
        "header": [{"key": "Content-Type", "value": "application/json"}],
        "body": {
          "mode": "raw",
          "raw": "{\"title\":\"New Task\",\"completed\":false,\"priority\":\"HIGH\"}"
        },
        "url": "http://localhost:8080/api/todos"
      }
    },
    {
      "name": "Update Todo",
      "request": {
        "method": "PUT",
        "header": [{"key": "Content-Type", "value": "application/json"}],
        "body": {
          "mode": "raw",
          "raw": "{\"title\":\"Updated Task\",\"completed\":true}"
        },
        "url": "http://localhost:8080/api/todos/1"
      }
    },
    {
      "name": "Delete Todo",
      "request": {
        "method": "DELETE",
        "url": "http://localhost:8080/api/todos/1"
      }
    }
  ]
}
```

### Testing with cURL

```bash
# Get all todos
curl -X GET http://localhost:8080/api/todos

# Create a todo
curl -X POST http://localhost:8080/api/todos \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Buy groceries",
    "completed": false,
    "priority": "MEDIUM"
  }'

# Update a todo
curl -X PUT http://localhost:8080/api/todos/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Buy groceries - DONE",
    "completed": true,
    "priority": "MEDIUM"
  }'

# Delete a todo
curl -X DELETE http://localhost:8080/api/todos/1
```

## 🎨 Frontend Components

### Main Components

1. **TodoList.js**
   - Main container component
   - Manages todos state
   - Handles filtering and statistics

2. **TodoForm.js**
   - Create and edit todos
   - Form validation
   - Priority, category, and due date inputs

3. **TodoItem.js**
   - Individual todo display
   - Toggle completion
   - Edit and delete actions
   - Priority badges

4. **api.js**
   - Axios HTTP client configuration
   - API endpoint functions

## ⚙️ Configuration

### Backend Configuration (`application.properties`)

```properties
# Server Configuration
server.port=8080

# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:tododb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

# JPA Configuration
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# H2 Console (optional - for development)
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

### Frontend Configuration

**API Base URL** is configured in `src/api.js`:
```javascript
const api = axios.create({
  baseURL: "http://localhost:8080/api/todos",
  headers: { "Content-Type": "application/json" }
});
```

## 🔧 Troubleshooting

### Common Issues

#### 1. CORS Error
**Error:** `Access to XMLHttpRequest has been blocked by CORS policy`

**Solution:** Ensure `CorsConfig.java` exists in your backend:
```java
@Configuration
public class CorsConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/api/**")
                .allowedOrigins("http://localhost:3000")
                .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                .allowedHeaders("*")
                .allowCredentials(true);
    }
}
```

#### 2. Backend Not Starting
**Error:** Port 8080 already in use

**Solution:**
- Stop any process using port 8080
- Or change port in `application.properties`:
  ```properties
  server.port=8081
  ```
- Update frontend API URL accordingly

#### 3. 404 Errors
**Error:** `GET http://localhost:8080/api/todos/ 404`

**Solution:** Remove trailing slash in `api.js`:
```javascript
export const getTodos = () => api.get(""); // Not api.get("/")
```

#### 4. Frontend Build Errors
**Error:** `npm install` fails

**Solution:**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

## 🚀 Deployment

### Backend Deployment

#### Build JAR file:
```bash
cd todo-backend
./mvnw clean package
```

#### Run JAR:
```bash
java -jar target/todo-backend-0.0.1-SNAPSHOT.jar
```

### Frontend Deployment

#### Build for production:
```bash
cd todo-frontend
npm run build
```

This creates an optimized production build in the `build/` folder.

#### Deploy to hosting services:
- **Netlify:** Drag and drop the `build` folder
- **Vercel:** Connect your GitHub repo
- **AWS S3:** Upload build files to S3 bucket

## 🛠️ Built With

### Backend
- **Spring Boot 3.x** - Application framework
- **Spring Data JPA** - Data persistence
- **H2 Database** - In-memory database
- **Maven** - Dependency management
- **Lombok** - Boilerplate code reduction

### Frontend
- **React 18** - UI library
- **Axios** - HTTP client
- **CSS3** - Styling
- **Lucide React** - Icons (optional)

## 📝 Todo Model

```java
@Entity
public class Todo {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String title;
    private String description;
    private Boolean completed;
    
    @Enumerated(EnumType.STRING)
    private Priority priority; // HIGH, MEDIUM, LOW
    
    private String category;
    private LocalDate dueDate;
    private LocalDateTime createdAt;
    private LocalDateTime updatedAt;
    
    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;
}
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author

Your Name
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com

## 🙏 Acknowledgments

- Spring Boot Documentation
- React Documentation
- Icons by Lucide
- Inspiration from various todo apps

## 📸 Screenshots

### Main Dashboard
![Dashboard Screenshot](screenshots/dashboard.png)

### Create Todo Form
![Form Screenshot](screenshots/form.png)

### Todo List View
![List Screenshot](screenshots/list.png)

---

⭐ **Star this repo if you found it helpful!**

For questions or support, please open an issue on GitHub.