  

### 06 Collection

![[/image 30.png|image 30.png]]

Template & Lösung

```JavaScript
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Optional;
import java.util.function.Consumer;
import java.util.Collection;

class Student {
    String name;
    int age;
    double grade;

    Student(String name, int age, double grade) {
        this.name = name;
        this.age = age;
        this.grade = grade;
    }

    @Override
    public String toString() {
        return "Student{name='" + name + "', age=" + age + ", grade=" + grade + '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }
        if (o == null || getClass() != o.getClass()) {
            return false;
        }
        Student student = (Student) o;
        return name.equals(student.name);
    }

    @Override
    public int hashCode() {
        return name.hashCode();
    }
}

public class StudentExample {

    public static void main(String[] args) {
        Collection<Student> students = new ArrayList<>();
        Student alice = new Student("Alice", 20, 3.5);
        Student bob = new Student("Bob", 19, 2.8);
        Student charlie = new Student("Charlie", 22, 3.9);
        Student david = new Student("David", 18, 2.4);
        Student eve = new Student("Eve", 21, 3.6);
        //Fügen Sie die Student-Objekte der ArrayList hinzu.
        students.add(alice);
        students.add(bob);
        students.add(charlie);
        students.add(david);
        students.add(eve);

        System.out.println("All students:");
        printStudents(students);

        int minAge = 20;
        // Entfernen Sie alle Studenten unter dem Mindestalter minAge
        removeStudentsBelowAge(students, minAge);

        System.out.println("\nStudents aged " + minAge + " or older:");
        printStudents(students);


        Student newStudent1 = new Student("Frank", 21, 3.7);
        Student newStudent2 = new Student("Alice", 20, 3.5);
        // Fügen Sie den neuen Studenten "Frank"und "Alice" hinzu, wenn sie nicht bereits in der Liste sind
        addStudentIfAbsent(students, newStudent1);
        addStudentIfAbsent(students, newStudent2);

        System.out.println("\nAfter adding new students:");
        printStudents(students);

        // Finden Sie einen Studenten mit einem bestimmten Namen
        Student foundStudent = findStudentByName(students, "Alice");
        if (foundStudent != null) {
            System.out.println(foundStudent);
        }

        System.out.println("\nUpdating grades:");
        // Erhöhen Sie die Noten aller Studenten um 0.5
        updateGrades(students, student -> student.grade += 0.5);
        printStudents(students);

        System.out.println("\nNotifying students from 'Charlie':");
        notifyStudentsFrom(students, "Charlie");

        System.out.println("\nRemoving students with grades below 3.0:");
        // Entfernen Sie alle Studenten mit einer Note unter 3.0
        removeStudentsWithLowGrades(students, 3.0);
        printStudents(students);
    }

    public static void printStudents(Collection<Student> students) {
        // Diese Methode gibt alle Studenten in der Konsole aus
        for (Student student : students) {
            System.out.println(student);
        }

    }

    public static void removeStudentsBelowAge(Collection<Student> students, int minAge) {
        // Diese Methode entfernt alle Studenten unter dem angegebenen Mindestalter
        // Nutzen Sie dabei einen Iterator
        Iterator<Student> iterator = students.iterator();
        while (iterator.hasNext()) {
            Student student = iterator.next();
            if (student.age < minAge) {
                iterator.remove();
            }
        }
    }

    public static void addStudentIfAbsent(Collection<Student> students, Student newStudent) {
        // Diese Methode fügt einen neuen Studenten hinzu, wenn er nicht bereits in der Liste ist
        for (Student student : students) {
            if (student.equals(newStudent)) {
                return;
            }
        }

    }

    public static Student findStudentByName(Collection<Student> students, String name) {
        // Diese Methode sucht nach einem Studenten mit einem bestimmten Namen und gibt ihn zurück, falls vorhanden
        for (Student student : students) {
            if (student.name.equals(name)) {
                return student;
            }
        }
        return null;
    }

    public static void notifyStudentsFrom(Collection<Student> students, String name) {
        // Diese Methode benachrichtigt alle verbleibenden Studenten ab einem bestimmten Namen. 
        //Die Benachrichtigung soll einfach in Form einer Konsolenausgabe erfolgen: "Sending Notification to ...
        for (Student student : students) {
            if (student.name.equals(name)) {
                System.out.println("Sending Notification to " + student.name);
            }
        }
    }

    public static void updateGrades(Collection<Student> students, Consumer<Student> gradeUpdater) {
        // Diese Methode aktualisiert die Noten der Studenten basierend auf der übergebenen Funktion
        for (Student student : students) {
            gradeUpdater.accept(student);
        }
    }

    public static void removeStudentsWithLowGrades(Collection<Student> students, double minGrade) {
        // Diese Methode entfernt alle Studenten mit einer Note unter der angegebenen Mindestnote
        // Nutzen Sie removeIf
        students.removeIf(student -> student.grade < minGrade);
    }
}
```