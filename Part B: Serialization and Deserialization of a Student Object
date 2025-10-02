import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;

class Student implements Serializable {
    private static final long serialVersionUID = 1L;

    int studentID;
    String name;
    char grade;

    public Student(int studentID, String name, char grade) {
        this.studentID = studentID;
        this.name = name;
        this.grade = grade;
    }

    @Override
    public String toString() {
        return "Student [ID=" + studentID + ", Name=" + name + ", Grade=" + grade + "]";
    }
}

public class SerializationDemo {
    public static void main(String[] args) {
        String filename = "student.ser";
        Student studentToWrite = new Student(101, "Ayush", 'A');

        try (FileOutputStream fileOut = new FileOutputStream(filename);
             ObjectOutputStream objOut = new ObjectOutputStream(fileOut)) {
            objOut.writeObject(studentToWrite);
            System.out.println("Student object has been serialized successfully.");
        } catch (IOException e) {
            System.err.println("Error during serialization: " + e.getMessage());
            e.printStackTrace();
        }

        Student studentToRead = null;

        try (FileInputStream fileIn = new FileInputStream(filename);
             ObjectInputStream objIn = new ObjectInputStream(fileIn)) {
            studentToRead = (Student) objIn.readObject();
            System.out.println("Student object has been deserialized successfully.");
        } catch (IOException | ClassNotFoundException e) {
            System.err.println("Error during deserialization: " + e.getMessage());
            e.printStackTrace();
        }

        if (studentToRead != null) {
            System.out.println("Retrieved Data: " + studentToRead);
        } else {
            System.out.println("Could not retrieve student data.");
        }
    }
}
