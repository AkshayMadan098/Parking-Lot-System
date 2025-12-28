# Parking Lot System

## 🎯 Overview

This Parking Lot System is designed to efficiently manage parking spaces across multiple floors, handle different vehicle types, and automate the parking and unparking process. The system follows SOLID principles and implements various design patterns to ensure scalability, maintainability, and extensibility.

## ✨ Features

- **Multi-Floor Support**: Manage parking lots with multiple floors
- **Vehicle Type Management**: Support for different vehicle types (Car, Motorcycle, Truck, etc.)
- **Automated Slot Assignment**: Automatically finds and assigns the nearest available parking slot
- **Ticket Generation**: Generates unique tickets for each parked vehicle
- **Fee Calculation**: Calculates parking fees based on vehicle type and duration
- **Real-time Availability**: Track available and occupied slots in real-time
- **Query Operations**: 
  - Find vehicles by registration number
  - Find vehicles by color
  - Display occupied/free slots
  - Generate parking reports

## 🏗️ System Design

### Core Components

1. **ParkingLot**: Main entry point managing the entire parking system
2. **Floor**: Represents individual floors with multiple parking spaces
3. **ParkingSpace**: Individual parking slots with specific vehicle type support
4. **Vehicle**: Abstract representation of vehicles (Car, Motorcycle, Truck)
5. **Ticket**: Parking ticket generated when a vehicle is parked
6. **ParkingStrategy**: Strategy pattern for slot allocation
7. **FeeCalculator**: Calculates parking fees based on various parameters

### Class Diagram

```
ParkingLot
├── Floor[]
│   └── ParkingSpace[]
│       └── Vehicle
├── ParkingStrategy
├── FeeCalculator
└── TicketManager
```

## 🔧 Prerequisites

- **Java Development Kit (JDK)**: Version 8 or higher
- **Build Tool**: Maven or Gradle
- **IDE** (Optional): IntelliJ IDEA, Eclipse, or VS Code

## 📦 Installation

### Clone the Repository

```bash
git clone https://github.com/AkshayMadan098/Parking-Lot-System.git
cd Parking-Lot-System
```

### Build the Project

#### Using Maven:
```bash
mvn clean install
```

#### Using Gradle:
```bash
./gradlew build
```

## 🚀 Usage

### Running the Application

#### From Command Line:
```bash
java -jar target/parking-lot-system.jar
```

#### From IDE:
Run the main class: `com.parkinglot.Main`

### Command-Line Interface

The system supports the following commands:

```bash
# Create a parking lot with specified capacity
create_parking_lot <number_of_floors> <slots_per_floor>

# Park a vehicle
park <vehicle_type> <registration_number> <color>

# Unpark a vehicle
leave <ticket_id>

# Display parking status
status

# Find registration numbers by color
registration_numbers_for_cars_with_colour <color>

# Find slot numbers by color
slot_numbers_for_cars_with_colour <color>

# Find slot by registration number
slot_number_for_registration_number <registration_number>

# Display available slots
display_free_slots <vehicle_type>

# Exit the application
exit
```

### Example Usage

```bash
# Initialize parking lot
create_parking_lot 3 10

# Park vehicles
park CAR KA-01-HH-1234 White
park MOTORCYCLE KA-02-HH-9999 Red
park TRUCK KA-03-BB-0001 Black

# Unpark a vehicle
leave PR1234FL1SL001

# Query operations
registration_numbers_for_cars_with_colour White
slot_number_for_registration_number KA-01-HH-1234
status
```

## 📁 Project Structure

```
Parking_Lot_System/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── parkinglot/
│   │   │           ├── model/
│   │   │           │   ├── Vehicle.java
│   │   │           │   ├── Car.java
│   │   │           │   ├── Motorcycle.java
│   │   │           │   ├── Truck.java
│   │   │           │   ├── ParkingSpace.java
│   │   │           │   ├── Floor.java
│   │   │           │   └── Ticket.java
│   │   │           ├── service/
│   │   │           │   ├── ParkingLot.java
│   │   │           │   ├── ParkingStrategy.java
│   │   │           │   └── FeeCalculator.java
│   │   │           ├── controller/
│   │   │           │   └── ParkingController.java
│   │   │           ├── exception/
│   │   │           │   └── ParkingException.java
│   │   │           └── Main.java
│   │   └── resources/
│   │       └── application.properties
│
├── pom.xml / build.gradle
└── README.md
```

## 🎨 Design Patterns Used

1. **Singleton Pattern**: Ensures only one instance of ParkingLot exists
2. **Factory Pattern**: Creates different types of vehicles
3. **Strategy Pattern**: Implements different parking slot allocation strategies
4. **Observer Pattern**: Notifies when parking slots become available
5. **Command Pattern**: Encapsulates parking operations as commands

## 📚 API Documentation

### ParkingLot Class

```java
// Initialize parking lot
public static ParkingLot getInstance(int floors, int slotsPerFloor)

// Park a vehicle
public Ticket parkVehicle(Vehicle vehicle)

// Unpark a vehicle
public boolean unparkVehicle(String ticketId)

// Get parking fee
public double getParkingFee(String ticketId)

// Check availability
public int getAvailableSlots(VehicleType type)
```

### Vehicle Class

java
// Vehicle types
enum VehicleType {
    CAR, MOTORCYCLE, TRUCK
}

// Vehicle properties
String registrationNumber
String color
VehicleType type
