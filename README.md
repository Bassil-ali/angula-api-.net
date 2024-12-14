# Angular 18 and .NET Backend API CRUD Application

## Overview
This project demonstrates a full-stack CRUD application using **Angular 18** for the frontend and **.NET** for the backend API. The system provides a basic structure to create, read, update, and delete data while maintaining modularity, scalability, and best practices.

## Features
1. **Frontend**: Built with Angular 18, providing a dynamic and responsive user interface.
2. **Backend**: Developed with .NET (ASP.NET Core), offering a RESTful API for data management.
3. **CRUD Operations**: Supports all basic CRUD operations.
4. **Database Integration**: Uses a SQL Server database.
5. **Error Handling**: Implements error handling and validation for seamless operation.

---

## Project Structure
### Frontend (Angular 18)
- **`src/app/components`**: Contains Angular components for various views.
- **`src/app/services`**: Contains Angular services for API communication.
- **`src/app/models`**: Defines TypeScript interfaces/models for data handling.
- **`src/environments`**: Environment-specific configurations.

### Backend (.NET)
- **Controllers**: Define API endpoints.
- **Models**: Represent database entities.
- **Services**: Encapsulate business logic.
- **Repositories**: Handle database interactions.
- **Migrations**: Manage database schema changes.

---

## Prerequisites
### Frontend
- Node.js (>= 16.x)
- Angular CLI (>= 18.x)

### Backend
- .NET SDK (>= 6.0)
- SQL Server

---

## Getting Started
### Backend Setup
1. Clone the repository.
   ```bash
   git clone <repository-url>
   cd backend
   ```
2. Restore dependencies.
   ```bash
   dotnet restore
   ```
3. Apply database migrations.
   ```bash
   dotnet ef database update
   ```
4. Run the application.
   ```bash
   dotnet run
   ```
5. The API will be available at `http://localhost:5000/api`.

### Frontend Setup
1. Navigate to the Angular project directory.
   ```bash
   cd frontend
   ```
2. Install dependencies.
   ```bash
   npm install
   ```
3. Update API endpoint in `src/environments/environment.ts`.
   ```typescript
   export const environment = {
     production: false,
     apiUrl: 'http://localhost:5000/api'
   };
   ```
4. Start the Angular development server.
   ```bash
   ng serve
   ```
5. The application will be available at `http://localhost:4200`.

---

## CRUD Endpoints (Backend API)
### Base URL: `http://localhost:5000/api`

#### 1. Get All Items
- **Endpoint**: `/items`
- **Method**: GET
- **Response**: List of items.

#### 2. Get Item by ID
- **Endpoint**: `/items/{id}`
- **Method**: GET
- **Response**: Single item details.

#### 3. Create Item
- **Endpoint**: `/items`
- **Method**: POST
- **Body**: JSON object representing the new item.

#### 4. Update Item
- **Endpoint**: `/items/{id}`
- **Method**: PUT
- **Body**: JSON object with updated details.

#### 5. Delete Item
- **Endpoint**: `/items/{id}`
- **Method**: DELETE

---

## Angular Service Example
```typescript
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import { environment } from '../../environments/environment';
import { Item } from '../models/item.model';

@Injectable({
  providedIn: 'root',
})
export class ItemService {
  private apiUrl = environment.apiUrl + '/items';

  constructor(private http: HttpClient) {}

  getItems(): Observable<Item[]> {
    return this.http.get<Item[]>(this.apiUrl);
  }

  getItemById(id: number): Observable<Item> {
    return this.http.get<Item>(`${this.apiUrl}/${id}`);
  }

  createItem(item: Item): Observable<Item> {
    return this.http.post<Item>(this.apiUrl, item);
  }

  updateItem(id: number, item: Item): Observable<Item> {
    return this.http.put<Item>(`${this.apiUrl}/${id}`, item);
  }

  deleteItem(id: number): Observable<void> {
    return this.http.delete<void>(`${this.apiUrl}/${id}`);
  }
}
```

---

## Acknowledgments
- **Angular**: [https://angular.io](https://angular.io)
- **.NET**: [https://dotnet.microsoft.com](https://dotnet.microsoft.com)

