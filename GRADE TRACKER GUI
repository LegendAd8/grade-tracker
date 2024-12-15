import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;

public class StudentGradeTrackerGUI {

    // ArrayList to store grades
    private static ArrayList<Integer> grades = new ArrayList<>();

    public static void main(String[] args) {
        // Create the main window (JFrame)
        JFrame frame = new JFrame("Student Grade Tracker");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(400, 400);

        // Create components for the GUI
        JPanel panel = new JPanel();
        panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));

        JLabel instructionLabel = new JLabel("Enter grade (0-100) and click Add Grade.");
        JTextField gradeInput = new JTextField(10);
        JButton addGradeButton = new JButton("Add Grade");
        JTextArea gradeListArea = new JTextArea(10, 30);
        gradeListArea.setEditable(false);

        JButton calculateButton = new JButton("Calculate Stats");
        JLabel resultLabel = new JLabel("Results will appear here.");

        // Add components to the panel
        panel.add(instructionLabel);
        panel.add(gradeInput);
        panel.add(addGradeButton);
        panel.add(new JScrollPane(gradeListArea));  // Use JScrollPane to make it scrollable
        panel.add(calculateButton);
        panel.add(resultLabel);

        frame.add(panel);

        // Action listener for Add Grade button
        addGradeButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    int grade = Integer.parseInt(gradeInput.getText());

                    if (grade >= 0 && grade <= 100) {
                        grades.add(grade);
                        gradeListArea.append(grade + "\n");
                        gradeInput.setText(""); // Clear input field
                    } else {
                        JOptionPane.showMessageDialog(frame, "Please enter a grade between 0 and 100.");
                    }
                } catch (NumberFormatException ex) {
                    JOptionPane.showMessageDialog(frame, "Invalid input. Please enter a valid number.");
                }
            }
        });

        // Action listener for Calculate Stats button
        calculateButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                if (grades.isEmpty()) {
                    resultLabel.setText("No grades entered.");
                    return;
                }

                // Calculate average, highest, and lowest
                int total = 0;
                int highest = grades.get(0);
                int lowest = grades.get(0);

                for (int grade : grades) {
                    total += grade;
                    if (grade > highest) {
                        highest = grade;
                    }
                    if (grade < lowest) {
                        lowest = grade;
                    }
                }

                double average = total / (double) grades.size();
                resultLabel.setText(String.format("Average: %.2f, Highest: %d, Lowest: %d", average, highest, lowest));
            }
        });

        // Set the window visible
        frame.setVisible(true);
    }
}
