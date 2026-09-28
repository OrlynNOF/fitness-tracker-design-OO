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
 1. Initalize 'total_cardio = 0', total_strength = 0', <br2> Loop main menu display until user enters, '4'.<br>3 Validate that 'main_choice" is between 1 and 4. <br>4> If '1' (Cardio) or '2' (Strength):<br>&emsp;a.Display respective submenu.<br>&emsp;b. Validate 'sub_choice' between 1 and 3. <br>&emsp;c. Prompt for duration; loop until 'duration >= 0'. <br>&emsp;d. Map choice to activity name.<br> &emsp;e Add 'duration' to running total..<br>5. If '3' (Summary):<br>&emspia. Calculate 'total_active = total_cardio + total_strength'.<br>&emsp;b. Determine goal achievement status ($>=120$ min).<br>&emspic. Display formatted summary report.<br>6. If '4' (Exit): Display exit farewell and terminate. | Invalid input warning messages<br> Success confirmation of logged minutes and activity name<br> Formatted Activity Summary: <br>&emsp;- Total Cardio Minutes<br>&emsp; - Total Strength Minutes<br>&emsp; - Total Active Minutes<br>&emp;- Total Strength Minutes<br>&emsp;- Total Active Minutes<br>&emsp;- Weekly Goal Status Message<br> Exit farewell message |

