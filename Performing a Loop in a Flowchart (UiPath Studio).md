# Performing a Loop in a Flowchart

Loops are generally used in UiPath Studio in complex scenarios where there is a need to repeat a set of instructions until a condition (or a set of conditions) is true. Further, we will exemplify a loop used in a Flowchart activity.

## Example
In our example, we will ask the user to pick a number from 1 to n and we will display in the Output panel all the numbers smaller than n divisible by 2. After iterating through all these numbers, we will write their sum in the Output panel. To build this automation, follow the steps:

1. On the Start tab, select New Project > Process. The New Blank Process window opens.
2. In the Name field type “Performing a Loop in a Flowchart” and leave the default project location. Click Create. The Design tab is displayed.
3. In the Ribbon menu, select New > Flowchart. The New Flowchart window opens. As you can see, the name and the location are inherited from the project. Click Create. A new Design Canvas is created in the Designer panel.
4. In the Activities panel, search for Input Dialog activity. To add it to the Designer panel, you can drag and drop it or double click on it. An Input Dialog is added to the Designer panel. Connect it to the Start node.
>***Note: To connect nodes in the Designer Panel, click one of the activities and drag it by holding down the mouse button to another activity until arrows appear around the target activity while hovering over it with the mouse. Drop it over the desired arrow.***
5. In the Variables panel, create an Int32 variable named “PickNumber”.
6. Select the Input Dialog and go to the Properties panel. In the Label field type “Please enter a number equal to or greater than 1”, in the Title field type "Data input" and in the Result field type “PickNumber”.
7. Add a Flow Decision activity and connect it to the Input dialog activity.
8. In the Properties panel of the new Flow Decision activity, in the Condition field type “PickNumber>=1”. This condition verifies if the number given by the user is greater than or equal to 1.
9. In the DisplayName field type “Flow Decision 1”
10. Connect the False branch of Flow Decision 1 to the Input Dialog activity. This way, if the condition of the flow decision is not met, the user will be prompted again to pick a number.
11. Create a new Int32 variable named “i” with the default value of 0.
12. Add a Flow Decision activity and connect it to the True branch of Flow Decision 1.
13. In the Properties panel of the new Flow Decision activity, in the DisplayName field type “Flow Decision 2” and in the Condition field type “i<=PickNumber”. This will iterate through all the numbers greater than 0 and smaller than PickNumber.
14. Add an Assign activity and connect it to the True branch of Flow Decision 2.
15. In the Properties panel of the new Assign activity, in the DisplayName field type “Assign 1”, in the To field type “i” and in the Value field type “i+1”. This will increment the value of i by one, at every step of the iteration.
16. Add a Flow Decision activity and connect it to Assign 1.
17. In the Properties panel of the new Flow Decision activity, in the DisplayName field type “Flow Decision 3” and in the Condition field type “i Mod2=0”. This condition verifies if the value of i is divisible by 2.
18. Connect the False branch of Flow Decision 3 to Flow Decision 2.
19. Create a new Int32 variable named “sum” with the default value of 0.
20. Add an Assign activity and connect it to the True branch of Flow Decision 3.
21. In the Properties panel of the new Assign activity, in the DisplayName field type “Assign 2”, in the To field type “sum” and in the Value field type “sum+i”. This will later sum up all the values of i that meet the conditions of Flow Decisions 1, 2 and 3.
22. Add a Write Line activity and connect it to Assign 2.
23. In the Properties panel of the new Write Line activity, in the DisplayName field type “Write Line 1” and in the Text field type “i.ToString”. This method converts the Int32 variable i to a string variable and prints it to the Output panel which supports only strings.
24. Connect Write Line 1 to Flow Decision 2. This will force the loop to continue the iteration conditioned by Flow Decision 2.
25. Add a Write Line activity and connect it to the False branch of Flow Decision 2.
26. In the Properties panel of the new Write Line activity, in the DisplayName field type “Write Line 2” and in the Text field type “sum.ToString”. When the iteration of all numbers smaller than PickNumber and divisible by 2 stops, the Write Line 2 activity will print their sum calculated by Assign 2 activity.
The following screenshot shows how the workflow should look in the end.
