# OPTA-PROG-SYNCHRONIZATION-VARIABLES
This programming aims to synchronize the last data read in the Arduino Cloud variable with a local variable. The step below this will be demonstrated below:

This programming simply counts pulses, where each pulse will be incremented by 0.002 in a widget, in addition we also have a virtual button connecting an OPTA output.

# 1° STEP

Create a local variable, in this case this variable named "contagem" is starting at 3,928
![image](https://github.com/user-attachments/assets/64f7b77b-0847-4f0e-9860-f768d93d150b)


# 2° STEP

Create a variable in the Cloud to store these read values.
Create a variable in the Cloud to store these read values. In this case, a variable named "iniciado" was created.
![image](https://github.com/user-attachments/assets/e27fec92-3001-4713-a5d1-4cf362a0d2c7)

# 3° STEP

Inside the void loop, increment a widget by 0.002 for each pulse received at a digital input of the OPTA.
contagem = contagem + 0.002; 

Then store this value in the Cloud variable:

iniciado = contagem;
![image](https://github.com/user-attachments/assets/cbcd687a-ad06-4446-8a59-0b7115a52344)

# 4° STEP

It is necessary to create the Arduino Cloud return functions within the Void setup.
These functions are intended to execute something in the programming according to the Cloud connection status.
The Cloud provides 3 functions:

- Synchronization
- Connected
- Disconnected

In this case, only the synchronization and disconnection functions were added, but we are only using the synchronization function in the programming, as it is the most important in this case.

![image](https://github.com/user-attachments/assets/c6aabc1a-5027-4733-b991-1a01dc923bf1)


# 5° STEP
Let's create a function called "void doThisOnSync()" which will have the function of synchronizing the last value read in the Cloud variable with the variable stored in OPTA.

Let's create a function called "void doThisOnSync()" that will synchronize the last value read in the Cloud variable with the variable stored in OPTA.
After creating this function, it is necessary to add a small piece of code:

contagem = iniciado;

It is not necessary to include Serial.println(contagem);

![image](https://github.com/user-attachments/assets/755cd9ed-f905-4785-81c9-b84f80d94c78)


# CONCLUSION
The code with these functions is available here for consultation, the other files are not necessary for this synchronization, only the code snippets mentioned here are important.
