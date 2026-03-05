# 🏨 Ocean View Resort

> **Hotel Reservation Management System** — A modern Java EE web application for managing hotel operations

![Java](https://img.shields.io/badge/Java-8+-orange?style=flat-square&logo=openjdk)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=flat-square&logo=mysql&logoColor=white)
![Tomcat](https://img.shields.io/badge/Tomcat-8.5+-yellow?style=flat-square&logo=apache-tomcat)
![Maven](https://img.shields.io/badge/Maven-3.6+-red?style=flat-square&logo=apache-maven)
![JAX--RS](https://img.shields.io/badge/JAX--RS-2.0-green?style=flat-square)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔐 **Authentication** | Secure login with role-based access (Admin, Manager, Receptionist) |
| 📅 **Reservations** | Create, manage, and track bookings with auto-generated confirmation numbers |
| 🛏️ **Room Management** | Track availability, types, rates, and amenities |
| 👥 **Guest Management** | Maintain guest profiles and history |
| 💰 **Billing** | Auto-calculate charges, taxes, discounts, and process payments |
| 📊 **Reports** | Dashboard, daily, revenue, and occupancy reports |

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────┐
│   📱 PRESENTATION         index.html (SPA)                   │
├──────────────────────────────────────────────────────────────┤
│   🌐 WEB SERVICES         JAX-RS REST Resources              │
│      Auth │ Guest │ Room │ Reservation │ Bill │ Report      │
├──────────────────────────────────────────────────────────────┤
│   ⚙️ SERVICE              AuthService │ ReservationService   │
├──────────────────────────────────────────────────────────────┤
│   💾 DATA ACCESS          DAO Pattern + Factory Pattern      │
├──────────────────────────────────────────────────────────────┤
│   🗄️ DATABASE             MySQL (oceanviewdb)                │
└──────────────────────────────────────────────────────────────┘
```

### 📦 Design Patterns

| Pattern | Usage |
|---------|-------|
| **Singleton** | `DatabaseConnection`, `AuthService`, `ReservationService` |
| **DAO** | Data access abstraction for all entities |
| **Factory** | `DAOFactory` for creating DAO instances |
| **Facade** | `ReservationService` for coordinating complex operations |
| **MVC** | Model-View-Controller separation |

---

## 🚀 Quick Start

### Prerequisites

- ☕ JDK 8+
- 📦 Maven 3.6+
- 🗄️ MySQL 8.0+
- 🐱 Apache Tomcat 8.5+

### Installation

**1. Clone & Setup Database**
```bash
mysql -u root -p < database/oceanview_seed.sql
```

**2. Configure Database Connection**

Edit `src/main/java/com/oceanview/util/DatabaseConnection.java`:
```java
private static final String DB_URL = "jdbc:mysql://localhost:3306/oceanviewdb";
private static final String DB_USER = "root";
private static final String DB_PASSWORD = "your_password";
```

**3. Build & Deploy**
```bash
mvn clean package
# Copy target/OceanViewResort-1.0-SNAPSHOT.war to Tomcat webapps/
```

**4. Access Application**
```
http://localhost:8080/OceanViewResort-1.0-SNAPSHOT/
```

### 🔑 Default Credentials
| Username | Password | Role |
|----------|----------|------|
| `admin` | `admin123` | Admin |

---

## 📡 API Endpoints

### 🔐 Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/login` | Login |
| `POST` | `/api/auth/logout` | Logout |
| `GET` | `/api/auth/current` | Current user |

### 👥 Guests
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/guests` | List all |
| `GET` | `/api/guests/{id}` | Get by ID |
| `POST` | `/api/guests` | Create |
| `PUT` | `/api/guests/{id}` | Update |
| `DELETE` | `/api/guests/{id}` | Delete |

### 🛏️ Rooms
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/rooms` | List all |
| `GET` | `/api/rooms/available` | Available rooms |
| `POST` | `/api/rooms` | Create |
| `PUT` | `/api/rooms/{id}` | Update |

### 📅 Reservations
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/reservations` | List all |
| `POST` | `/api/reservations` | Create |
| `PUT` | `/api/reservations/{id}/status` | Update status |

### 💰 Bills
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/bills` | List all |
| `POST` | `/api/bills` | Generate |
| `PUT` | `/api/bills/{id}/payment` | Process payment |

### 📊 Reports
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/reports/dashboard` | Dashboard summary |
| `GET` | `/api/reports/daily` | Daily report |
| `GET` | `/api/reports/revenue` | Revenue report |
| `GET` | `/api/reports/occupancy` | Occupancy report |

---

## 📁 Project Structure

```
OceanViewResort/
├── 📄 pom.xml
├── 📁 database/
│   └── oceanview_seed.sql
└── 📁 src/main/
    ├── 📁 java/com/oceanview/
    │   ├── config/          # JAX-RS config
    │   ├── model/           # Entity classes
    │   ├── dao/             # Data access layer
    │   ├── service/         # Business logic
    │   ├── util/            # Utilities
    │   └── webservice/      # REST endpoints
    └── 📁 webapp/
        ├── index.html       # SPA frontend
        └── WEB-INF/web.xml
```

---

## 🗄️ Database Schema

```
USERS ──────────── GUESTS
                      │
                      │ 1:N
                      ▼
ROOMS ◄─────────── RESERVATIONS
         N:1          │
                      │ 1:1
                      ▼
                    BILLS
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Backend** | Java 8+, JAX-RS 2.0, Jersey 2.29.1 |
| **Database** | MySQL 8.0, JDBC |
| **Server** | Apache Tomcat 8.5+ |
| **Build** | Apache Maven |
| **Frontend** | HTML5, CSS3, JavaScript (SPA) |
| **JSON** | Gson 2.8.9 |

---

## 📝 License

This project is developed for educational purposes.

---

<p align="center">
  <b>🌊 Ocean View Resort</b> — <i>Beachfront Hotel Management System</i>
</p>
| receptionist | recep123 | RECEPTIONIST |
| manager | manager123 | MANAGER |

**Room Types:**
| Type | Rate/Night (LKR) | Max Occupancy |
|------|------------------|---------------|
| SINGLE | 5,000 - 5,500 | 1 |
| DOUBLE | 8,000 - 8,500 | 2 |
| DELUXE | 12,000 - 12,500 | 3 |
| SUITE | 20,000 - 22,000 | 4 |
| FAMILY | 15,000 - 16,000 | 5-6 |

### Appendix B: Bill Calculation Formula

```
Room Charges = Rate per Night × Number of Nights
Service Charges = Room Charges × 10%
Tax Amount = Room Charges × 10%
Total Amount = Room Charges + Service Charges + Tax Amount - Discount
```

---

**Developed by:** Ocean View Resort Development Team  
**Version:** 1.0  
**Date:** January 2026
