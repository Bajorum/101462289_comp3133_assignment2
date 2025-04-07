# Employee Management System API

A powerful GraphQL API for employee management with comprehensive authentication and data operations.

## 🚀 Features

- **Authentication & Authorization**
  - JWT-based secure authentication
  - Role-based access control
  - Password encryption
  - Token management

- **Employee Operations**
  - Create, read, update, and delete employees
  - Advanced filtering and search capabilities
  - Department and designation management
  - Data validation

- **GraphQL Implementation**
  - Optimized queries and mutations
  - Strong type definitions
  - Comprehensive resolvers
  - Error handling

- **Database Integration**
  - MongoDB connection with Mongoose ODM
  - Efficient data modeling
  - Indexing for performance
  - Data integrity constraints

## 📋 Technical Stack

- **Backend**: Node.js, Express.js
- **API**: Apollo Server (GraphQL)
- **Database**: MongoDB with Mongoose
- **Authentication**: JWT (JSON Web Tokens)
- **Testing**: Jest, Apollo Server Testing
- **Documentation**: GraphQL Playground/Apollo Sandbox

## 🔧 Installation

### Prerequisites
- Node.js (v16+)
- MongoDB (local or Atlas)
- npm or yarn

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/employee-management-api.git
cd employee-management-api
```

2. **Install dependencies**
```bash
npm install
```

3. **Environment configuration**
Create a `.env` file in the root directory:
```
PORT=4000
MONGODB_URI=mongodb://localhost:27017/employee_db
JWT_SECRET=your_secure_jwt_secret
JWT_EXPIRATION=1d
NODE_ENV=development
```

4. **Start the server**
```bash
# Development mode with hot-reloading
npm run dev

# Production mode
npm start
```

5. **Access GraphQL Playground**
Open your browser and navigate to `http://localhost:4000/graphql`

## 📊 API Schema

### Types

```graphql
type User {
  id: ID!
  username: String!
  email: String!
  role: String!
  createdAt: String!
}

type Employee {
  id: ID!
  name: String!
  email: String!
  phone: String
  designation: String!
  department: String!
  salary: Float
  joinDate: String
  address: String
  isActive: Boolean!
  createdAt: String!
  updatedAt: String!
}

type AuthPayload {
  token: String!
  user: User!
}
```

### Queries

```graphql
type Query {
  # Employee queries
  getEmployees(limit: Int, offset: Int): [Employee!]!
  getEmployeeById(id: ID!): Employee
  getEmployeesByDepartment(department: String!): [Employee!]!
  getEmployeesByDesignation(designation: String!): [Employee!]!
  searchEmployees(term: String!): [Employee!]!
  
  # User queries
  me: User
}
```

### Mutations

```graphql
type Mutation {
  # Authentication mutations
  register(username: String!, email: String!, password: String!): AuthPayload!
  login(email: String!, password: String!): AuthPayload!
  
  # Employee mutations
  createEmployee(input: EmployeeInput!): Employee!
  updateEmployee(id: ID!, input: EmployeeUpdateInput!): Employee!
  deleteEmployee(id: ID!): Boolean!
}
```

## 🔒 Authentication

The API uses JWT authentication. Include the token in HTTP headers:

```
{
  "Authorization": "Bearer YOUR_JWT_TOKEN"
}
```

## 📈 Performance Considerations

- **Pagination**: Implement cursor-based pagination for large datasets
- **Caching**: Use Apollo Server caching for frequently accessed data
- **Batching**: Utilize DataLoader for batching database queries
- **Indexing**: Ensure proper MongoDB indexes for query optimization

## 🧪 Testing

Run the test suite:

```bash
# Run all tests
npm test

# Run with coverage report
npm run test:coverage
```

## 📖 Documentation

Complete API documentation is available through GraphQL Playground when running the server locally, or through Apollo Sandbox if deployed.

## 🛣️ Roadmap

- Implement file uploads for employee profile pictures
- Add real-time subscriptions for data updates
- Create advanced reporting capabilities
- Develop comprehensive admin dashboard API endpoints

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.