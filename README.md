# Brandon's Pro Football Position Finder

# this function safely gets a number so the program doesn't crash if the user types something wrong
def get_int_input(prompt):
    while True:
        try:
            return int(input(prompt))
        except ValueError:
            print("Please enter a valid number.")


# this function gets height in feet and inches and converts it into total inches
def get_height_in_inches():
    print("Enter your height:")
    feet = get_int_input("Feet: ")
    inches = get_int_input("Inches: ")
    return feet * 12 + inches


def main():

    # loop so the program can run again
    while True:

        # ask user for offense or defense and clean up input
        side = input("Would you like offense or defense? ").strip().lower()

        # get weight safely
        weight = get_int_input("Enter your weight in pounds: ")

        # get height safely
        height = get_height_in_inches()

        # realistic size limits for this model
        MIN_WEIGHT = 191
        MAX_WEIGHT = 239   # UPDATED MAX
        MIN_HEIGHT = 67   # 5'7
        MAX_HEIGHT = 77   # 6'5

        # check weight range
        if weight < MIN_WEIGHT or weight > MAX_WEIGHT:
            print("Weight is outside the allowed range (191–239).")
            continue  # restart program

        # check height range
        if height < MIN_HEIGHT or height > MAX_HEIGHT:
            print("Height is outside the allowed range (5'7–6'5).")
            continue  # restart program

        # OFFENSE LOGIC
        if side == "offense":

            if 190 <= weight <= 206 and 70 <= height <= 77:
                print("You would likely be a Wide Receiver or Quarterback.")

            else:
                if 206 < weight <= 239 and 69 <= height <= 77:
                    print("You would likely be a Tight End.")

                else:
                    if 239 < weight <= 278 and 70 <= height <= 77:
                        print("You would likely be an Offensive Lineman.")

                    else:
                        print("No offensive position matched your size.")

        else:

            # DEFENSE LOGIC
            if side == "defense":

                if 190 <= weight <= 206 and 70 <= height <= 75:
                    print("You would likely be a Cornerback or Safety.")

                else:
                    if 206 < weight <= 239 and 67 <= height <= 72:
                        print("You would likely be a Linebacker or Defensive End.")

                    else:
                        if 239 < weight <= 278 and 70 <= height <= 77:
                            print("You would likely be a Defensive Lineman.")

                        else:
                            print("No defensive position matched your size.")

            else:
                print("Please choose either offense or defense.")
                continue

        # ask if user wants to run again
        again = input("Would you like to try again? (yes/no): ").strip().lower()

        if again != "yes":
            print("Program ended.")
            break


# start the program
main()
