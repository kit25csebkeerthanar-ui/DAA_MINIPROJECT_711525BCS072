import java.util.*;

class Student {
    int id;
    String name;
    String department;
    int year;
    double cgpa;

    Student(int id, String name, String department,
            int year, double cgpa) {
        this.id = id;
        this.name = name;
        this.department = department;
        this.year = year;
        this.cgpa = cgpa;
    }

    void display() {
        System.out.println("ID         : " + id);
        System.out.println("Name       : " + name);
        System.out.println("Department : " + department);
        System.out.println("Year       : " + year);
        System.out.println("CGPA       : " + cgpa);
    }
}

public class StudentSearchSystem {

    static Student linearSearch(ArrayList<Student> list, int id) {
        for (Student s : list) {
            if (s.id == id)
                return s;
        }
        return null;
    }

    static Student binarySearch(ArrayList<Student> list, int id) {
        int low = 0;
        int high = list.size() - 1;

        while (low <= high) {
            int mid = (low + high) / 2;

            if (list.get(mid).id == id)
                return list.get(mid);

            if (list.get(mid).id < id)
                low = mid + 1;
            else
                high = mid - 1;
        }

        return null;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        students.add(new Student(105, "Arun", "CSE", 2, 8.2));
        students.add(new Student(101, "Priya", "IT", 3, 9.1));
        students.add(new Student(108, "Rahul", "CSE", 1, 7.9));
        students.add(new Student(103, "Divya", "ECE", 2, 8.7));
        students.add(new Student(110, "Kavin", "CSE", 3, 8.9));

        students.sort(Comparator.comparingInt(s -> s.id));

        System.out.print("Enter Student ID to search: ");
        int id = sc.nextInt();

        Student result = binarySearch(students, id);

        if (result != null) {
            System.out.println("\nStudent Found:");
            result.display();
        } else {
            System.out.println("\nStudent not found.");
        }

        sc.close();
    }
}
