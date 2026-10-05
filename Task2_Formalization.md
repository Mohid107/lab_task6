# Task 2 — Formalized Constraints

To express the safety rules rigorously, we define the following logical propositions:
* $Train\_Present$ (T)
* $Barrier\_Open$ (BO)
* $Barrier\_Closed$ (BC)
* $Barrier\_Closing$ (BCl)
* $Warnings\_Active$ (WA)
* $Traffic\_Red$ (TR)
* $Sensor\_Failure$ (SF)
* $Comm\_Loss$ (CL)
* $Sensor\_Conflict$ (SC)
* $Emergency$ (E)

Here are the formalized constraints translated into logical expressions using implication ($\to$), negation ($\neg$), and conjunction ($\land$):

1. **C1 (Train Safety):** 
   $$Train\_Present \to \neg Barrier\_Open$$

2. **C2 (Warning Activation):** 
   $$Barrier\_Closing \to Warnings\_Active$$

3. **C3 (Traffic Signal Interlock):** 
   $$Barrier\_Closing \to Traffic\_Red$$

4. **C4 (Barrier Pre-closure):** 
   $$Train\_Present \to Barrier\_Closed$$

5. **C5 (Sensor Failure Safe State):** 
   $$Sensor\_Failure \to Barrier\_Closed$$

6. **C6 (Communication Loss Safe State):** 
   $$Comm\_Loss \to \neg Barrier\_Open$$

7. **C7 (Sensor Conflict Handling):** 
   $$Sensor\_Conflict \to Barrier\_Closed$$

8. **C8 (Emergency Override):** 
   $$Emergency \to Barrier\_Closed$$
