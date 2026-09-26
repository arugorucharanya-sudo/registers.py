# Digital Register Calculator
# Electrical Engineering / Digital Circuits
#
# Supports:
# 1. PIPO Register
# 2. SISO Shift Register
# 3. SIPO Shift Register
# 4. PISO Shift Register
# 5. Left Shift
# 6. Right Shift
# 7. Binary to Decimal
# 8. Decimal to Binary


def validate_binary(data):
    """Check whether the input contains only binary digits."""
    return all(bit in "01" for bit in data)


def decimal_to_binary():
    print("\n========== DECIMAL TO BINARY ==========")

    number = int(input("Enter a decimal number: "))

    if number < 0:
        print("Please enter a positive number.")
        return

    binary = bin(number)[2:]

    print(f"Decimal: {number}")
    print(f"Binary : {binary}")


def binary_to_decimal():
    print("\n========== BINARY TO DECIMAL ==========")

    binary = input("Enter binary number: ")

    if not validate_binary(binary):
        print("Error: Enter only 0 and 1.")
        return

    decimal = int(binary, 2)

    print(f"Binary : {binary}")
    print(f"Decimal: {decimal}")


def pipo_register():
    print("\n========== PIPO REGISTER ==========")

    data = input("Enter binary data: ")

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    print("\nParallel Input:")
    print(data)

    print("Parallel Output:")
    print(data)

    print("\nData is loaded and read in parallel.")


def siso_register():
    print("\n========== SISO SHIFT REGISTER ==========")

    data = input("Enter binary data: ")

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    register = list(data)

    print("\nInitial Register:")
    print(" ".join(register))

    print("\nRight Shift Operations:")

    for i in range(len(register)):
        register.insert(0, "0")
        register.pop()

        print(f"Shift {i + 1}: {' '.join(register)}")

    print("\nSISO operation completed.")


def sipo_register():
    print("\n========== SIPO SHIFT REGISTER ==========")

    data = input("Enter serial binary data: ")

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    register = ["0"] * len(data)

    print("\nSerial Data:", data)

    for i, bit in enumerate(data):
        register.pop(0)
        register.append(bit)

        print(
            f"Clock {i + 1}: "
            f"{' '.join(register)}"
        )

    print("\nParallel Output:")
    print(" ".join(register))


def piso_register():
    print("\n========== PISO SHIFT REGISTER ==========")

    data = input("Enter parallel binary data: ")

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    register = list(data)

    print("\nParallel Data Loaded:")
    print(" ".join(register))

    print("\nSerial Output:")

    for i in range(len(register)):
        output = register.pop(0)

        print(f"Clock {i + 1}: {output}")


def left_shift():
    print("\n========== LEFT SHIFT ==========")

    data = input("Enter binary data: ")
    positions = int(input("Enter number of shifts: "))

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    result = data

    print("\nInitial:", result)

    for i in range(positions):
        result = result[1:] + "0"
        print(f"Shift {i + 1}: {result}")


def right_shift():
    print("\n========== RIGHT SHIFT ==========")

    data = input("Enter binary data: ")
    positions = int(input("Enter number of shifts: "))

    if not validate_binary(data):
        print("Error: Enter only 0 and 1.")
        return

    result = data

    print("\nInitial:", result)

    for i in range(positions):
        result = "0" + result[:-1]
        print(f"Shift {i + 1}: {result}")


def main():

    while True:

        print("\n==============================================")
        print("       DIGITAL REGISTER CALCULATOR")
        print("       Electrical Engineering")
        print("==============================================")

        print("1. PIPO Register")
        print("2. SISO Shift Register")
        print("3. SIPO Shift Register")
        print("4. PISO Shift Register")
        print("5. Left Shift")
        print("6. Right Shift")
        print("7. Binary to Decimal")
        print("8. Decimal to Binary")
        print("9. Exit")

        choice = input("\nEnter your choice: ")

        try:
            if choice == "1":
                pipo_register()

            elif choice == "2":
                siso_register()

            elif choice == "3":
                sipo_register()

            elif choice == "4":
                piso_register()

            elif choice == "5":
                left_shift()

            elif choice == "6":
                right_shift()

            elif choice == "7":
                binary_to_decimal()

            elif choice == "8":
                decimal_to_binary()

            elif choice == "9":
                print("\nThank you for using Digital Register Calculator!")
                break

            else:
                print("\nInvalid choice. Please select 1-9.")

        except ValueError:
            print("\nPlease enter a valid value.")


if __name__ == "__main__":
    main()
