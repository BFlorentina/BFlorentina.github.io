# Performing a Loop in a Flowchart

Loops are generally used in UiPath Studio in complex scenarios where there is a need to repeat a set of instructions until a condition (or a set of conditions) is true. Further, we will exemplify a loop used in a Flowchart activity.

## Example
In our example, we will ask the user to pick a number from *1* to *n* and we will display in the **Output panel** all the numbers smaller than *n* divisible by *2*. After iterating through all these numbers, we will write their sum in the **Output panel**. To build this automation, follow the steps:

1. On the **Start** tab, select **New Project** > **Process**. The **New Blank Process** window opens.
2. In the **Name** field type “Performing a Loop in a Flowchart” and leave the default project location. Click **Create**. The **Design** tab is displayed.
3. In the Ribbon menu, select **New** > **Flowchart**. The **New Flowchart** window opens. As you can see, the name and the location are inherited from the project. Click **Create**. A new Design Canvas is created in the **Designer** panel.
4. In the **Activities** panel, search for an **Input Dialog** activity. To add it to the **Designer** panel, you can drag and drop it or double click on it. An **Input Dialog** is added to the **Designer** panel. Connect it to the **Start** node.

> ***Note: To connect nodes in the Designer Panel, click one of the activities and drag it by holding down the mouse button to another activity until arrows appear around the target activity while hovering over it with the mouse. Drop it over the desired arrow.***

5. In the **Variables** panel, create an Int32 variable named “PickNumber”.
6. Select the **Input Dialog** and in the **Properties** panel type: **Label** = “Please enter a number equal to or greater than 1”, **Title** = "Data input" and **Result** = “PickNumber”.
7. Add a **Flow Decision** activity and connect it to the **Input dialog** activity.
8. In the **Properties** panel of the new **Flow Decision** activity type: **DisplayName** = “Flow Decision 1” and **Condition** = “PickNumber>=1”. The condition verifies if the number given by the user is greater than or equal to *1*.
9. Connect the **False** branch of **Flow Decision 1** to the **Input Dialog** activity. This way, if the condition of the flow decision is not met, the user will be prompted again to pick a number.
10. Create a new Int32 variable named “i” with the default value of *0*.
11. Add a **Flow Decision** activity and connect it to the **True** branch of **Flow Decision 1**.
12. In the **Properties** panel of the new **Flow Decision** activity type: **DisplayName** = “Flow Decision 2” and **Condition** = “i<=PickNumber”. This will iterate through all the numbers greater than *0* and smaller than *PickNumber*.
13. Add an **Assign** activity and connect it to the **True** branch of **Flow Decision 2**.
14. In the **Properties** panel of the new **Assign** activity type: **DisplayName** = “Assign 1”, **To** = “i” and **Value** = “i+1”. This will increment the value of *i* by one, at every step of the iteration.
15. Add a **Flow Decision** activity and connect it to **Assign 1**.
16. In the **Properties** panel of the new **Flow Decision** activity type: **DisplayName** = “Flow Decision 3” and **Condition** = “i Mod2=0”. This condition verifies if the value of *i* is divisible by 2.
17. Connect the **False** branch of **Flow Decision 3** to **Flow Decision 2**.
18. Create a new Int32 variable named “sum” with the default value of *0*.
19. Add an **Assign** activity and connect it to the **True** branch of **Flow Decision 3**.
20. In the **Properties** panel of the new **Assign** activity type: **DisplayName** = “Assign 2”, **To** = “sum” and **Value** = “sum+i”. This will later sum up all the values of *i* that meet the conditions of Flow Decisions 1, 2 and 3.
21. Add a **Write Line** activity and connect it to **Assign 2**.
22. In the **Properties** panel of the new **Write Line** activity type: **DisplayName** = “Write Line 1” and **Text** = “i.ToString”. This method converts the Int32 variable i to a string variable and prints it to the **Output** panel which supports only strings.
23. Connect **Write Line 1** to **Flow Decision 2**. This will force the loop to continue the iteration conditioned by **Flow Decision 2**.
24. Add a **Write Line** activity and connect it to the **False** branch of **Flow Decision 2**.
25. In the **Properties** panel of the new **Write Line** activity type: **DisplayName** = “Write Line 2” and **Text** = “sum.ToString”. When the iteration of all numbers smaller than *PickNumber* and divisible by *2* stops, the **Write Line 2** activity will print their sum calculated by **Assign 2** activity.
The following screenshot shows how the workflow should look in the end.

![Flowchart](/images/Loop flowchart.jpg)
