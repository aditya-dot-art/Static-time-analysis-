# Static-time-analysis-
Learn about how the time configure in semiconductor level or chip level.

#Arrival time:- It is the time to reach from the starting point to end point is called arrival time.The actual time it takes for data to propagate from the launch flip-flop (source) through the combinational logic to the capture flip-flop.

Arrival time usually calculated at the end point.

As from the first image there are four end point are as D of first flip flop, D of second flip flop and there are two end point for output (OUT)port i.e. first from the D from second flip flop and one from the input port (IN).<img width="1920" height="1200" alt="Screenshot 2025-11-08 231030" src="https://github.com/user-attachments/assets/ff40def8-a5ae-420a-b906-5b2e53943029" />

---

 #Requird time:- It define what's the system specifications or need of system.The time by which the data must arrive at the capture flip-flop's data pin to meet the timing constraint (setup or hold) relative to the capture clock edge.
 
Example:- the frequency of the design is one gigahertz, so we have to make such a arrangements such that the arrival time fulfill the requirements of one gigahertz or one nanosecond.

---

 Slack:- the diffence between the arrival time and required time. 
 
Example:- The data should be at the first flip flop should be between .5 ns to 3ns means the data can take the minimum time .5 ns and max time 3 ns.

Let's say that the arrival time is 3.5 ns then the diffence between the min time from arrival time is called as min slack time i.e 3ns and in the same way the difference between the arrival time from max time is max slack time.

The max slack time is known as setup slack or setup timing and the min slack time is known as hold slack hold timing.

---

Types of setup/hold analysis:-
1. reg2reg:- it is timing path from first flip flop or launch flop to next flip flp or capture flop.
2. in2reg:- it is timing path from input pin to launch flop .
3. reg2out:- it is timing path from capture flop output to output pin.
4. in2out:- it is timing path from input pin to output pin i.e. from giving input to getting the output.
5. clock getting:-it is for getting the timing path from other clock to clock of capturing flop or gate output.
    
   for getting the clock at differnt flip flop or following circuit we don't using directly instead of we using the clock getting technique that is power saving which is combination of differnt logic gates and flip flops.<img width="1429" height="533" alt="Screenshot 2025-11-14 234957" src="https://github.com/user-attachments/assets/2a901960-d02d-4726-b2b9-f04aff18a507" />
<img width="1122" height="465" alt="Screenshot 2025-11-16 100419" src="https://github.com/user-attachments/assets/aa2e0065-5418-464d-9405-5ee1dfdf8577" />
 This technique, clock getting, is useful switching the following circuit i.e. we can control wheather the output of launching flop should feed to capturing flop. 
6. recovery/removal:- it is timing path from the another logic circuit to reset of flip flop that control when to feed the reset signal.
    
7. data-to-data:- this check is used to save the power in the way of reset signal which is dependant of 'a' signal from combinational logic and 'ctrl signal' whci control the and gate output i.e. if the ctrl signal is one then the 'a' data will come out so that the capture flop can reset or set itsself.

   Also 'a' and 'ctrl signal' should be synchronous, for this we have to tuned in that way that there a relation between 'a' and 'ctrl signal'. This can be get by the making the end point of some circuit which  can be get by data-to-data check. By this way we can make a both signal as end point and there are multiple timing path coming to both pin, one from the launch flop and one from other flop that is use for the control the clock of capture flop. Data-to-data check is diffent from other check as it as both pin is a data signal and all other except clock getting is dependant on flop's end point but in this both check is input of a gate.
   
9. Latch timing:- We have seen that flip flop will tranparent when there edge triggerring but there are another circuitry which is dependant of level trigger not on edge trigger.

   If we want to make the timing path between flop to latch, which is not made before, for this latch borrow some time from level timing that is called as time borrowing so there are two timing path comes into picture, one from lauch flop to latch in which the time borrowing actually happened and one from the latch to flip flop in which the latch give some time to flip flop. <img width="1118" height="487" alt="Screenshot 2025-11-16 102953" src="https://github.com/user-attachments/assets/81e54524-10e2-4cf3-95f3-68613ae80958" />
<img width="1157" height="447" alt="Screenshot 2025-11-16 104039" src="https://github.com/user-attachments/assets/3d32923f-7459-43f0-a735-b8f9ae6c9cdd" />
## 1st is coming in to reg to reg and 2nd, 3rd and 4th IO TIMING. 

---

# slew/transition analysis:-
this ensure that the slew or transition is covering between the min or max value. So there is any requirement of slew is done by slew or transiton analysis.This is important so that if the slew is shrf then it can increae the short circuit and if it large then it can increase the more opening time for the gate is turned on . 

It is divided into two parts:-

 1. data skew:- it is determine by the taking the point on data path and checking the slew wheather it is min or max. this specify the the data transition.
<img width="1431" height="565" alt="Screenshot 2025-11-16 115825" src="https://github.com/user-attachments/assets/8c4cbc14-c853-4d5b-83b2-982c6c517462" />

 2. clock skew:- it is very complicated and important for any circuit as it decide when the data will loaded. It can calculate with the reference of the min or max value by tap on the path of clock.
<img width="1447" height="571" alt="Screenshot 2025-11-16 115847" src="https://github.com/user-attachments/assets/1e6d99b3-6765-4ee2-8ecc-f5b5d1a22358" />
in both skew clock skew is complicated as data is not switch often as compared to clock which switch at equal time interval.

# Load analysis 
in this analysis we analysis that what is the data should loaded at every node.
it is also of two types:
1. fanout
2. capacitance

# Clock analysis
1. skew analysis:- in this latency matching is done in flip flop. If the skew doesn't matches then it affect first set of categories i.e. static/hold  analysis
  <img width="1436" height="579" alt="Screenshot 2025-11-16 115933" src="https://github.com/user-attachments/assets/30dafc7f-a883-4ebb-b4d8-8a0185c8ad8a" />
2. pulse analysis:- we expect that same clock pulse will be provided at avery flip flop or latches . So in this check that till what point it can allow the clock pulse in with degrade the clock pulse.

---

## 1. Reg-to-reg
In this we check the delays of diffenert circutry elements like flip flop and combinational circuit as given in diagram <img width="1482" height="685" alt="Screenshot 2025-11-17 180056" src="https://github.com/user-attachments/assets/c3ff7cd7-526d-4ae6-818e-0af0398c7b82" />
First we study about the combinational circuit how the time setup works 
as we take the combinational circuit is combination of AND, OR, BUFFER gate etc. 

With input i1, i2 and i3 and output is o1 as follows 
<img width="1508" height="753" alt="Screenshot 2025-11-17 180921" src="https://github.com/user-attachments/assets/cade364b-a65e-4f29-97ab-1fe49759d159" />
NOw we have to comvert this circuit in to Directed aclylic graph, is also called as timing graph, with sourse s.

In this timing graph we have make all input pins, cells, output pin and other are converted into nodes and assign the time delays by each elements as: 
<img width="1262" height="374" alt="Screenshot 2025-11-17 181755" src="https://github.com/user-attachments/assets/ad41fe6a-8cbd-4123-bc7a-742d56cc0966" />
Now we have to calculate the actual arrival time which is time at any nodes where we can see 'latest transition' after the first clock pulse.
In this scenario we took the worst time delay.

Now we have to calculate the required arrival time which is time at any node where we can expext the 'latest transition' within clock cycle.

In Actual arrival time we are computing from launch flop to capture flop so we add the the arrival time at each and every node but in the case of required arrival time we calcute from capture flop to launch flop by subtracting as at the capture flop RAT is already define and for the RAT we took best time.
<img width="1198" height="471" alt="Screenshot 2025-11-17 183518" src="https://github.com/user-attachments/assets/597fdda1-aa5b-495b-932e-b9978777200d" />

Slack(S):- slack is a critical metric that measures the timing margin of a path in the circuit.

$$\text{Slack} = \text{Data Required Time} - \text{Data Arrival Time}$$

Positive Slack ($\text{Slack} > 0$): Indicates that the timing constraint is met and the path has a safety margin. This is the desired outcome.

Zero Slack ($\text{Slack} = 0$): Indicates that the timing constraint is exactly met.

Negative Slack ($\text{Slack} < 0$): Indicates a timing violation, meaning the path is too slow (Setup violation) or too fast (Hold violation) and the circuit may not function reliably at the specified clock frequency.

AAT is expexted to less than the RAT at every design for meeting the design expectation. 
