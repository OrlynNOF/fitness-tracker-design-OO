#fitness-tracker-design
Fitness Tracker Psuedocode and Flowchart and IPO Chart

**Course** ITP 100 Software Design & Logic
**Author** ITP 100 Orlyn Ovando-Flores
**Deliverable:** Algorithim Design (IPO, Flowchart, Psuedocode) 

## 1. Problem Description & Design
* **Problem** Students need a command-line interface to track daily cardiovascular and strength excerise duration, validate that inputs are realistic, and review their progress toward a weekly target of 120 minutes. 
* **Scope:** 
  * Features a continuous main loop with 2 hierarchal submenus (Cardio and Strength)
  * Validate menu bounds (rejects valutes outside menu options) and duration inputs (rejects vegative numbers).
  * Aggregates total minutes in memory during execution and outputs a progeress summary on demand.
  * Terminates cleanly when the user selects the Exit option.

 # 2. IPO Chart (Input - Process - Output) 
| Input | Proccessing | Output |
| :---  | :---------- | :----- |
 'main_choice' (Integer: 1-4<br>
 'sub_choice' (Integer: 1-4<br> 
 1. Initalize 'total_cardio = 0', total_strength = 0', <br2> Loop main menu display until user enters, '4'.<br>3 Validate that 'main_choice" is between 1 and 4. <br>4> If '1' (Cardio) or '2' (Strength):<br>&emsp;a.Display respective submenu.<br>&emsp;b. Validate 'sub_choice' between 1 and 3. <br>&emsp;c. Prompt for duration; loop until 'duration >= 0'. <br>&emsp;d. Map choice to activity name.<br> &emsp;e Add 'duration' to running total..<br>5. If '3' (Summary):<br>&emspia. Calculate 'total_active = total_cardio + total_strength'.<br>&emsp;b. Determine goal achievement status ($>=120$ min).<br>&emspic. Display formatted summary report.<br>6. If '4' (Exit): Display exit farewell and terminate. | Invalid input warning messages<br> Success confirmation of logged micnutes and activity name<br> Formatted Activity Summary: <br>&emsp;- Total Cardio Minutes<br>&emsp; - Total Strength Minutes<br>&emsp; - Total Active Minutes<br>&emp;- Total Strength Minutes<br>&emsp;- Total Active Minutes<br>&emsp;- Weekly Goal Status Message<br> Exit farewell message |

## 3. Psuedocode 


 Module Main()
     DECLARE Integer total_cardio = 0 
     DECLARE Integer total_strength = 0 
     DECLARE Integer total_active = 0
     DECLARE String main_choice = ""
     DECLARE String sub_choice = "" 
     DECLARE Real duration = 0,0 
     DECLARE String activity_name = ""
     
     DISPLAY "==================================="
     DISPLAY "      CAMPUS FITNESS TRACKER "
     DISPLAY "==================================="

    While True
          // Step 1: Main Menu & Input Validation 
          Display "---MAIN MENU---"
          Display "1. Log Cardio Workout"
          Display "2. Log Strength Workout"
          Display "3. View Activity Summary"
          Display "4. Exit" 
          Display "Enter your choice (1-4): "
          Input main_choice

          While main_choice < 1 OR main_choice > 4 
                Display "Invaild. Choice must be 1,2,3, or 4. Try Again:" 
          End While
        // Step 2: Handle Cardio Menu
        IF main_choice == 1 THEN
            DISPLAY "--- CARDIO MENU ---"
            DISPLAY "1. Running / Jogging"
            DISPLAY "2. Cycling"
            DISPLAY "3. Swimming"
            DISPLAY "Enter cardio activity (1-3):"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                activity_name = "Running / Jogging"
            ELSE IF sub_choice == 2 THEN
                activity_name = "Cycling"
            ELSE
                activity_name = "Swimming"
            END IF

            DISPLAY "Enter duration in minutes:"
            INPUT duration

            WHILE duration < 0
                DISPLAY "Invalid. Please enter minutes >= 0:"
                INPUT duration
            END WHILE

            total_cardio = total_cardio + duration
            DISPLAY "Successfully added ", duration, " minutes for ", activity_name, "."
            
           // Step 3: Handle Strength Menu
           ELSE IF main_choice == 2 THEN
            DISPLAY "--- STRENGTH MENU ---"
            DISPLAY "1. Upper Body"
            DISPLAY "2. Lower Body"
            DISPLAY "3. Core & Flexibility"
            DISPLAY "Enter strength category (1-3):"
            INPUT sub_choice

            WHILE sub_choice < 1 OR sub_choice > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                activity_name = "Upper Body"
            ELSE IF sub_choice == 2 THEN
                activity_name = "Lower Body"
            ELSE
                activity_name = "Core & Flexibility"
            END IF

            DISPLAY "Enter duration in minutes:"
            INPUT duration

            WHILE duration < 0
                DISPLAY "Invalid. Please enter minutes >= 0:"
                INPUT duration
            END WHILE

            total_strength = total_strength + duration
            DISPLAY "Successfully added ", duration, " minutes for ", activity_name, "."

        // Step 4: Handle Activity Summary
        ELSE IF main_choice == 3 THEN
            total_active = total_cardio + total_strength

            DISPLAY "=========================================="
            DISPLAY "            ACTIVITY SUMMARY              "
            DISPLAY "=========================================="
            DISPLAY "Total Cardio:    ", total_cardio, " minutes"
            DISPLAY "Total Strength:  ", total_strength, " minutes"
            DISPLAY "Total Active:    ", total_active, " minutes"

            IF total_active >= 120 THEN
                DISPLAY "Status: Goal achieved! You exceeded 120 weekly active minutes."
            ELSE IF total_active > 0 THEN
                DISPLAY "Status: Keep Going! ", (120 - total_active), " more minutes needed to hit your weekly target."
            ELSE
                DISPLAY "Status: In progress. Keep going to reach your 120-minute goal!"
            END IF
            DISPLAY "=========================================="

        // Step 5: Handle Exit
        ELSE IF main_choice == 4 THEN
            DISPLAY "Thank you for using Personal Fitness Tracker. Stay active!"
        END IF

    END WHILE
END MODULE
