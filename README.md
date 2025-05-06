# Mini-Project
Applet Code

     import java.applet.Applet;
     import java.awt.*;
     import java.awt.event.*;

    /*
    <applet code="CalculatorApplet" width=300 height=200>
    </applet>
     */

    public class CalculatorApplet extends Applet implements ActionListener {

    TextField num1Field, num2Field, resultField;
    Button addButton, subButton, mulButton, divButton;

    public void init() {
        // Set layout
        setLayout(new GridLayout(5, 2, 5, 5));

        // Create components
        Label num1Label = new Label("Number 1:");
        num1Field = new TextField();

        Label num2Label = new Label("Number 2:");
        num2Field = new TextField();

        addButton = new Button("+");
        subButton = new Button("-");
        mulButton = new Button("*");
        divButton = new Button("/");

        Label resultLabel = new Label("Result:");
        resultField = new TextField();
        resultField.setEditable(false);

        // Add components to applet
        add(num1Label);
        add(num1Field);
        add(num2Label);
        add(num2Field);

        add(addButton);
        add(subButton);
        add(mulButton);
        add(divButton);

        add(resultLabel);
        add(resultField);

        // Register event listeners
        addButton.addActionListener(this);
        subButton.addActionListener(this);
        mulButton.addActionListener(this);
        divButton.addActionListener(this);
    }

    public void actionPerformed(ActionEvent e) {
        try {
            double num1 = Double.parseDouble(num1Field.getText());
            double num2 = Double.parseDouble(num2Field.getText());
            double result = 0;

            if (e.getSource() == addButton) {
                result = num1 + num2;
            } else if (e.getSource() == subButton) {
                result = num1 - num2;
            } else if (e.getSource() == mulButton) {
                result = num1 * num2;
            } else if (e.getSource() == divButton) {
                if (num2 == 0) {
                    resultField.setText("Error: Divide by zero");
                    return;
                }
                result = num1 / num2;
            }

            resultField.setText(String.valueOf(result));

        } catch (NumberFormatException ex) {
            resultField.setText("Invalid input"); }}
                                            }
