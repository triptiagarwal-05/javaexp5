import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class EmployeeManagementSystem {

    private static final String FILE_NAME = "employees.txt";
    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        while (true) {
            displayMenu();
            System.out.print("Enter your choice (1-3): ");
            String choice = scanner.nextLine();

            switch (choice) {
                case "1":
                    addEmployee();
                    break;
                case "2":
                    displayAllEmployees();
                    break;
                case "3":
                    System.out.println("Exiting the application. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please enter a number between 1 and 3.");
            }
            System.out.println("\nPress Enter to continue...");
            scanner.nextLine();
        }
    }

    private static void displayMenu() {
        System.out.println("\n--- Employee Management System ---");
        System.out.println("1. Add an Employee");
        System.out.println("2. Display All Employees");
        System.out.println("3. Exit the Application");
        System.out.println("---------------------------------");
    }

    private static void addEmployee() {
        System.out.println("\n--- Add New Employee ---");
        try {
            System.out.print("Enter Employee ID: ");
            String id = scanner.nextLine();
            System.out.print("Enter Employee Name: ");
            String name = scanner.nextLine();
            System.out.print("Enter Designation: ");
            String designation = scanner.nextLine();
            System.out.print("Enter Salary: ");
            double salary = Double.parseDouble(scanner.nextLine());

            try (FileWriter fw = new FileWriter(FILE_NAME, true);
                 BufferedWriter bw = new BufferedWriter(fw)) {
                String employeeRecord = String.format("%s,%s,%s,%.2f", id, name, designation, salary);
                bw.write(employeeRecord);
                bw.newLine();
                System.out.println("Employee record added successfully!");
            }
        } catch (IOException e) {
            System.err.println("Error writing to file: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.err.println("Invalid input for salary. Please enter a valid number.");
        }
    }

    private static void displayAllEmployees() {
        System.out.println("\n--- All Employee Records ---");
        try (FileReader fr = new FileReader(FILE_NAME);
             BufferedReader br = new BufferedReader(fr)) {

            String line;
            boolean foundRecords = false;
            System.out.printf("%-10s | %-20s | %-20s | %-10s%n", "ID", "Name", "Designation", "Salary");
            System.out.println("-------------------------------------------------------------------");

            while ((line = br.readLine()) != null) {
                foundRecords = true;
                String[] details = line.split(",");
                if (details.length == 4) {
                    System.out.printf("%-10s | %-20s | %-20s | %-10s%n", details[0], details[1], details[2], details[3]);
                }
            }

            if (!foundRecords) {
                System.out.println("No employee records found. The file might be empty.");
            }

        } catch (IOException e) {
            System.err.println("No employee records found. Please add an employee first.");
        }
    }
}
