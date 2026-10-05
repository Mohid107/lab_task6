# Task 1 — Identified Constraints

Below are 10 core constraints that the ARLCCS must always satisfy to ensure safe interaction between trains and road traffic:

* **C1: The barrier must not open while a train is present in the crossing.**
  * *Reason:* Opening the barrier would allow road traffic to enter the active track area, resulting in catastrophic collisions.

* **C2: Warning lights and audible alarms must be activated before the road barriers begin to close.**
  * *Reason:* Gives motorists and pedestrians adequate advance warning to clear the tracks before physical barriers drop.

* **C3: Road traffic signals must turn red before the road barriers start closing.**
  * *Reason:* Prevents new vehicles from entering the crossing zone just as the physical barriers begin descent.

* **C4: The road barriers must be fully closed prior to the train entering the crossing zone.**
  * *Reason:* Ensures the crossing is completely sealed off before the train crosses the intersection.

* **C5: If a primary train-detection sensor fails, the system must enter a safe fallback mode and keep barriers closed.**
  * *Reason:* Prevents hazardous ambiguity caused by lost sensor data.

* **C6: The barriers must not open if there is a communication loss with the safety-monitoring unit.**
  * *Reason:* Ensures fail-safe operation when the central supervising node loses connectivity.

* **C7: If an obstruction or sensor conflict is detected, the safety-monitoring unit must alert the control-center interface.**
  * *Reason:* Guarantees that operators are immediately notified of abnormal states or hardware malfunctions.

* **C8: The system must not clear or open the crossing if conflicting sensor readings occur.**
  * *Reason:* Resolves ambiguity conservatively; if one sensor reports a train and another reports clear, safety takes precedence.

* **C9: In the event of an emergency condition triggered from the control center, the barriers must immediately close and warnings must sound.**
  * *Reason:* Allows manual override by operators during external emergencies near the tracks.

* **C10: The barriers must remain closed until all detection sensors confirm the train has completely cleared the crossing zone.**
  * *Reason:* Prevents premature opening while tail cars or multi-unit trains are still passing through.
