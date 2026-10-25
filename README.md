# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:



## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by:DHARUN ARULSELVAN
Registeration Number :212224220024
*/
```

activity_main
```

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="24dp"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/factorial_calculator"
        android:textSize="26sp"
        android:layout_marginBottom="24dp" />

    <EditText
        android:id="@+id/numberInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:minHeight="48dp"
        android:hint="@string/enter_a_number"
        android:inputType="number"
        android:importantForAutofill="no" />

    <Button
        android:id="@+id/factorialButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:minHeight="48dp"
        android:text="@string/factorial"
        android:layout_marginTop="20dp" />

</LinearLayout>
```
MainActivity.java

```

package com.example.explicit;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText numberInput;
    Button factorialButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        numberInput = findViewById(R.id.numberInput);
        factorialButton = findViewById(R.id.factorialButton);

        factorialButton.setOnClickListener(v -> {
            String value = numberInput.getText().toString().trim();

            if (value.isEmpty()) {
                numberInput.setError(getString(R.string.enter_a_number));
                return;
            }

            int number;

            try {
                number = Integer.parseInt(value);
            } catch (NumberFormatException e) {
                numberInput.setError(getString(R.string.error_enter_valid_number));
                return;
            }

            if (number < 0 || number > 20) {
                numberInput.setError(getString(R.string.error_enter_number_range));
                return;
            }

            Intent intent = new Intent(MainActivity.this, MainActivity2.class);
            intent.putExtra("number", number);
            startActivity(intent);
        });
    }
}
```
activity2.xml

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="24dp">

    <TextView
        android:id="@+id/resultText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/factorial_result"
        android:textSize="28sp" />

</LinearLayout>

```
MainActivity2.java

```

package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity2);

        result = findViewById(R.id.result);

        String number = getIntent().getStringExtra("number");

        int n = Integer.parseInt(number);
        long fact = 1;
        for(int i = 1; i <= n; i++)
        {
            fact = fact * i;
        }

        result.setText("Factorial of " + n + " = " + fact);

    }
}
```
## OUTPUT
<img width="1727" height="1078" alt="image" src="https://github.com/user-attachments/assets/19c38822-54c4-4d08-87d2-98bfba56ee76" />

<img width="1735" height="1078" alt="image" src="https://github.com/user-attachments/assets/e6fad1cc-d8ef-4ddd-ac89-719f84b99795" />


<img width="1733" height="1077" alt="image" src="https://github.com/user-attachments/assets/d4bc4331-c654-41c1-961f-ee0127610681" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


