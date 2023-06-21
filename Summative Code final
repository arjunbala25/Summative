import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class MetabolicChartGUI extends JFrame {
    private JTextField ageField;
    private JTextField weightField;
    private JTextField heightField;
    private JTextField fitnessGoalField;
    private JTextArea outputArea;

    public MetabolicChartGUI() {
        setTitle("Metabolic Chart");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        // Create input fields
        JPanel inputPanel = new JPanel(new GridLayout(5, 2));
        inputPanel.add(new JLabel("Age: "));
        ageField = new JTextField();
        inputPanel.add(ageField);
        inputPanel.add(new JLabel("Weight kg: "));
        weightField = new JTextField();
        inputPanel.add(weightField);
        inputPanel.add(new JLabel("Height cm: "));
        heightField = new JTextField();
        inputPanel.add(heightField);
        inputPanel.add(new JLabel("Fitness Goal (Weight Loss, Muscle Gain, Weight Maintenance.): "));
        fitnessGoalField = new JTextField();
        inputPanel.add(fitnessGoalField);
        JButton calculateButton = new JButton("Calculate");
        inputPanel.add(calculateButton);
        add(inputPanel, BorderLayout.NORTH);

        // Create output area
        outputArea = new JTextArea();
        outputArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(outputArea);
        add(scrollPane, BorderLayout.CENTER);

        // Calculate button action listener
        calculateButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                calculateMetabolicChart();
            }
        });

        pack();
        setLocationRelativeTo(null); // Center the window on the screen
        setVisible(true);
    }

    private void calculateMetabolicChart() {
        // Get user input
        int age = Integer.parseInt(ageField.getText());
        double weight = Double.parseDouble(weightField.getText());
        double height = Double.parseDouble(heightField.getText());
        String fitnessGoal = fitnessGoalField.getText();

        // Calculate metabolic information
        double bmr = calculateBMR(age, weight, height);
        double carbohydrates = calculateCarbohydrates(bmr);
        double proteins = calculateProteins(bmr);
        double fats = calculateFats(bmr);
        String workoutRecommendation = getWorkoutRecommendation(fitnessGoal);

        // Display results
        String output = "BMR: " + bmr + "\n"
                + "Carbohydrates: " + carbohydrates + "g\n"
                + "Proteins: " + proteins + "g\n"
                + "Fats: " + fats + "g\n"
                + "Workout Recommendation: " + workoutRecommendation;
        outputArea.setText(output);
    }

    private double calculateBMR(int age, double weight, double height) {
    // BMR calculation logic
    double bmr = 0.0;
    
    if (age >= 18) {
        bmr = 66 + (13.75 * weight) + (5 * height) - (6.75 * age);
    } else {
        // Apply different calculation for individuals under 18 years old
        bmr = 88.362 + (13.397 * weight) + (4.799 * height) - (5.677 * age);
    }
    
    return bmr;
}

private double calculateCarbohydrates(double bmr) {
    // Carbohydrates calculation logic
    double carbohydrates = bmr * 0.5 / 4; // Assumes 50% of calories come from carbohydrates (1 gram of carbs = 4 calories)
    return carbohydrates;
}

private double calculateProteins(double bmr) {
    // Proteins calculation logic
    double proteins = bmr * 0.2 / 4; // Assumes 20% of calories come from proteins (1 gram of protein = 4 calories)
    return proteins;
}

private double calculateFats(double bmr) {
    // Fats calculation logic
    double fats = bmr * 0.3 / 9; // Assumes 30% of calories come from fats (1 gram of fat = 9 calories)
    return fats;
}
private String getWorkoutRecommendation(String fitnessGoal) {
    // Workout recommendation logic
    String recommendation = "";
    // Implement the workout recommendation logic based on the user's fitness goal
    // Example workout recommendations based on different goals:
    if (fitnessGoal.equalsIgnoreCase("Weight Loss")) {
        recommendation = "30 minutes of cardio exercises and strength training 3 times a week.";
    } else if (fitnessGoal.equalsIgnoreCase("Muscle Gain")) {
        recommendation = "Weight lifting exercises targeting major muscle groups 4 times a week.";
    } else if (fitnessGoal.equalsIgnoreCase("Weight Maintenance")) {
        recommendation = "Combination of cardio and strength training exercises 3-4 times a week.";
    }
    // Adjust the logic and recommendations based on the specific fitness goals you want to support
    // ...
    return recommendation;
}
    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new MetabolicChartGUI();
            }
        });
    }
}
