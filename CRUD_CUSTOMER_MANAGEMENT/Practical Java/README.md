# Generic Spring Boot CRUD Application

A generalized Spring Boot CRUD template that can be easily customized for different entities (Students, Books, Products, etc.) by changing just a few variables.

## Features

- ✅ Generic entity with `id`, `name`, and `field2`
- ✅ Complete CRUD operations (Create, Read, Update, Delete)
- ✅ RESTful API endpoints
- ✅ ArrayList-based in-memory storage (no database needed)
- ✅ Easy customization via `application.properties`
- ✅ Lightweight - only Spring Boot Web dependency

## Project Structure

```
src/
├── main/
│   ├── java/com/example/crud/
│   │   ├── CrudApplication.java          # Main application
│   │   ├── config/
│   │   │   └── EntityConfig.java         # Entity configuration
│   │   ├── model/
│   │   │   └── Entity.java               # Generic entity model
│   │   ├── repository/
│   │   │   └── EntityRepository.java     # JPA repository
│   │   ├── service/
│   │   │   └── EntityService.java        # Business logic
│   │   └── controller/
│   │       └── EntityController.java     # REST endpoints
│   └── resources/
│       └── application.properties        # Configuration file
└── pom.xml
```

## How to Use

### 1. Customize Your Entity

Edit `src/main/resources/application.properties`:

```properties
# For Students
entity.entity-name=student
entity.field1-name=name
entity.field2-name=course

# For Books
# entity.entity-name=book
# entity.field1-name=title
# entity.field2-name=author

# For Products
# entity.entity-name=product
# entity.field1-name=name
# entity.field2-name=price
```

### 2. Run the Application

```bash
mvn spring-boot:run
```

Or in IntelliJ IDEA:
1. Open the project
2. Run `CrudApplication.java`

The application will start on `http://localhost:8080`

### 3. API Endpoints

The endpoints automatically change based on your entity configuration:

#### Example: Students Configuration

**POST** `/students` - Create a new student
```json
{
  "name": "John Doe",
  "field2": "Computer Science"
}
```

**GET** `/students` - Get all students

**GET** `/students/{id}` - Get student by ID

**PUT** `/students/{id}` - Update student
```json
{
  "name": "John Doe",
  "field2": "Software Engineering"
}
```

**DELETE** `/students/{id}` - Delete student

#### Example: Books Configuration

Change `application.properties` to:
```properties
entity.entity-name=book
entity.field1-name=title
entity.field2-name=author
```

Endpoints become:
- **POST** `/books`
- **GET** `/books`
- **GET** `/books/{id}`
- **PUT** `/books/{id}`
- **DELETE** `/books/{id}`

Request body:
```json
{
  "name": "1984",
  "field2": "George Orwell"
}
```

## Testing with cURL

```bash
# Create
curl -X POST http://localhost:8080/students \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","field2":"Computer Science"}'

# Get All
curl http://localhost:8080/students

# Get by ID
curl http://localhost:8080/students/1

# Update
curl -X PUT http://localhost:8080/students/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","field2":"Software Engineering"}'

# Delete
curl -X DELETE http://localhost:8080/students/1
```

## Quick Configuration Examples

### 1. Student Management
```properties
entity.entity-name=student
entity.field1-name=name
entity.field2-name=course
```

### 2. Employee Management
```properties
entity.entity-name=employee
entity.field1-name=name
entity.field2-name=department
```

### 3. Book Management
```properties
entity.entity-name=book
entity.field1-name=title
entity.field2-name=author
```

### 4. Product Management
```properties
entity.entity-name=product
entity.field1-name=name
entity.field2-name=price
```

### 5. Course Management
```properties
entity.entity-name=course
entity.field1-name=code
entity.field2-name=name
```

### 6. Teacher Management
```properties
entity.entity-name=teacher
entity.field1-name=name
entity.field2-name=subject
```

### 7. Contact Management
```properties
entity.entity-name=contact
entity.field1-name=name
entity.field2-name=phone
```

### 8. Customer Management
```properties
entity.entity-name=customer
entity.field1-name=name
entity.field2-name=address
```

### 9. Vehicle Management
```properties
entity.entity-name=vehicle
entity.field1-name=number
entity.field2-name=owner
```

### 10. Patient Management
```properties
entity.entity-name=patient
entity.field1-name=name
entity.field2-name=disease
```

## Data Storage

This application uses **ArrayList** for in-memory storage. No database required!

- Data is stored in memory using `List<Entity>`
- Auto-incrementing IDs using `AtomicLong`
- Data is reset when application restarts
- Perfect for learning and prototyping

## Requirements

- Java 17+
- Maven 3.6+
- IntelliJ IDEA (or any IDE)

## Notes

- The entity uses generic field names: `id`, `name`, and `field2`
- `name` maps to the first meaningful field (name, title, code, etc.)
- `field2` maps to the second field (course, author, price, etc.)
- JSON requests/responses use these generic field names
- The API path dynamically changes based on configuration

## License

Free to use for educational purposes.

