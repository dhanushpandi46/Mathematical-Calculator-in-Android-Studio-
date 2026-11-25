# Mathematical-Calculator-in-Android-Studio-
To design and develop a mathematical calculator application using Android Studio that performs basic arithmetic operations such as addition, subtraction, multiplication and division through a user-friendly graphical interface.

EXPERIMENT: MATHEMATICAL CALCULATOR USING ANDROID STUDIO
# AIM
To design and develop a mathematical calculator application using Android Studio that performs basic arithmetic operations such as addition, subtraction, multiplication and division through a user-friendly graphical interface.

# SOFTWARE REQUIREMENTS
•	Android Studio
•	Java Programming Language
•	XML Layout Editor
•	Android Emulator or Android Mobile
•	Android SDK

# THEORY
Android Studio is an Integrated Development Environment (IDE) used to develop Android applications. Android applications can be developed using Java and XML.
A mathematical calculator application consists of graphical user interface elements such as:
•	EditText – To enter numerical values.
•	Button – To select arithmetic operations.
•	TextView – To display the calculated result.
Java event-handling methods are used to perform the selected mathematical operations when the user clicks the corresponding buttons.

# PROCEDURE
1.	Open Android Studio.
2.	Select New Project and choose Empty Views Activity.
3.	Enter the project name as MathematicalCalculator.
4.	Select Java as the programming language.
5.	Design the user interface using XML Layout Editor.
6.	Add two EditText fields to enter numerical values.
7.	Add four buttons for Addition, Subtraction, Multiplication and Division.
8.	Add a TextView to display the result.
9.	Open MainActivity.java and write the Java program to perform arithmetic operations.
10.	Use setOnClickListener() to handle button-click events.
11.	Execute the application using an Android Emulator or physical Android device.
12.	Enter two numbers and select the required arithmetic operation.
13.	Verify the displayed result.

# ALGORITHM
1.	Start the application.
2.	Initialize the user interface components.
3.	Accept two numerical inputs from the user.
4.	Select the required arithmetic operation.
5.	Convert the input values into numerical data types.
6.	Perform the selected arithmetic operation.
7.	Check for division by zero when division is selected.
8.	Display the calculated result.
9.	Repeat the process for another operation.
10.	Stop.
    
# PROGRAM

# XML

package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import java.text.DecimalFormat;

public class MainActivity extends AppCompatActivity {

    EditText num1, num2;
    Button add, sub, mul, div, clear;
    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        num1 = findViewById(R.id.num1);
        num2 = findViewById(R.id.num2);

        add = findViewById(R.id.btnAdd);
        sub = findViewById(R.id.btnSub);
        mul = findViewById(R.id.btnMul);
        div = findViewById(R.id.btnDiv);
        clear = findViewById(R.id.btnClear);

        result = findViewById(R.id.txtResult);

        add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('+');
            }
        });

        sub.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('-');
            }
        });

        mul.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('*');
            }
        });

        div.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('/');
            }
        });

        clear.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                num1.setText("");
                num2.setText("");
                result.setText("Result: ");
                num1.requestFocus();
            }
        });
    }

    private void calculate(char operator) {

        String value1 = num1.getText().toString().trim();
        String value2 = num2.getText().toString().trim();

        if (value1.isEmpty() || value2.isEmpty()) {
            Toast.makeText(this,
                    "Please enter both numbers",
                    Toast.LENGTH_SHORT).show();
            return;
        }

        try {
            double a = Double.parseDouble(value1);
            double b = Double.parseDouble(value2);
            double answer = 0;

            switch (operator) {

                case '+':
                    answer = a + b;
                    break;

                case '-':
                    answer = a - b;
                    break;

                case '*':
                    answer = a * b;
                    break;

                case '/':
                    if (b == 0) {
                        result.setText("Result: Cannot divide by zero");
                        return;
                    }
                    answer = a / b;
                    break;
            }

            DecimalFormat df = new DecimalFormat("0.##########");
            result.setText("Result: " + df.format(answer));

        } catch (NumberFormatException e) {
            result.setText("Result: Invalid input");
        }
    }
}

# MAIN ACTIVITY JAVA

package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import java.text.DecimalFormat;

public class MainActivity extends AppCompatActivity {

    EditText num1, num2;
    Button add, sub, mul, div, clear;
    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        num1 = findViewById(R.id.num1);
        num2 = findViewById(R.id.num2);

        add = findViewById(R.id.btnAdd);
        sub = findViewById(R.id.btnSub);
        mul = findViewById(R.id.btnMul);
        div = findViewById(R.id.btnDiv);
        clear = findViewById(R.id.btnClear);

        result = findViewById(R.id.txtResult);

        add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('+');
            }
        });

        sub.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('-');
            }
        });

        mul.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('*');
            }
        });

        div.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                calculate('/');
            }
        });

        clear.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                num1.setText("");
                num2.setText("");
                result.setText("Result: ");
                num1.requestFocus();
            }
        });
    }

    private void calculate(char operator) {

        String value1 = num1.getText().toString().trim();
        String value2 = num2.getText().toString().trim();

        if (value1.isEmpty() || value2.isEmpty()) {
            Toast.makeText(this,
                    "Please enter both numbers",
                    Toast.LENGTH_SHORT).show();
            return;
        }

        try {
            double a = Double.parseDouble(value1);
            double b = Double.parseDouble(value2);
            double answer = 0;

            switch (operator) {

                case '+':
                    answer = a + b;
                    break;

                case '-':
                    answer = a - b;
                    break;

                case '*':
                    answer = a * b;
                    break;

                case '/':
                    if (b == 0) {
                        result.setText("Result: Cannot divide by zero");
                        return;
                    }
                    answer = a / b;
                    break;
            }

            DecimalFormat df = new DecimalFormat("0.##########");
            result.setText("Result: " + df.format(answer));

        } catch (NumberFormatException e) {
            result.setText("Result: Invalid input");
        }
    }
}


# EXPECTED OUTPUT

<img width="1600" height="821" alt="image" src="https://github.com/user-attachments/assets/683ef619-1c86-4ab9-b3df-4c37f7a1817d" />


# APPLICATION FEATURES
•	Simple and user-friendly interface.
•	Performs four basic arithmetic operations.
•	Accepts numerical inputs from users.
•	Displays calculated results instantly.
•	Handles division-by-zero errors.

# RESULT
Thus, the Mathematical Calculator application was successfully designed and developed using Android Studio with Java and XML. The application performs addition, subtraction, multiplication and division and displays the corresponding results successfully.

# CONCLUSION
The experiment provides practical knowledge of Android application development, XML-based user interface design, Java programming, and event handling using Android Studio.

