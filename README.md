# electrical-system
# guide to supply electrical devices
[electrical system.py](https://github.com/user-attachments/files/24245257/electrical.system.py)
DEVICE_NAME = "Raspberry pi pico"   # WILL ADD ARDUINO, LED, MOTOR, ETC
MAX_VOLTAGE = 5.5  # Volts(V)       # WORK ON SHORTENING CODE AND CLEANING UP
MIN_VOLTAGE = 1.8  # (V)
MAX_TOTAL_CURRENT = 0.05  # Amps(A)

# --Start of program--

Device = input("What device are you using")
if Device.lower() == DEVICE_NAME.lower():
    print("Your device is supported")
else:
    print("Your device isnt compatabile")
    exit()

# float value(can include decimal) #string sequence of charecters
current_input_string = input("what is your input current(A)")
current_input_float = float(current_input_string)
if current_input_float > MAX_TOTAL_CURRENT:
    print("WARNING OVERCURRENT")
    print("DO NOT CONNECT SUPPLY")
else:
    print("SUCCESS")
    print("suitable input")


voltage_input_string = input("What is your input voltage(volts)?")
if voltage_input_string.replace('.', '', 1).isdigit():
    voltage_input_float = float(voltage_input_string)
    # FOR resistor recomendation
    volt_drop_needed = voltage_input_float - MAX_VOLTAGE
    # R = I/R
    suggested_resistor = volt_drop_needed / current_input_float


if voltage_input_float > MAX_VOLTAGE:
    print("WARNING the max input voltage is 5.5v")
    print("Do not connect supply to board")
    print("TO lower voltage {MAX_RECCOMENDED_VOLTAGE} you can add a resistor")
    print(
        f"You need a resistor of approximately {suggested_resistor:.2f} Ohms in series.")

elif voltage_input_float < MIN_VOLTAGE:
    print("voltage is below recomended range")
    print("Device may not operate")

else:
    print("succes voltage is within safe limit")
    print("YOUR CURRENT AND VOLTAGE ARE SUTIABLE TO CONTINUE!")
