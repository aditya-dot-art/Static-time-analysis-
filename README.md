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

We calculate the slack by taking the worst timeing constraint.Also in this combinational circuit, toward the input side, we can't do anything it is directly connected to source but in case if flip flop, we can take a flip flop with lower delay so in input side the slack become positive

<img width="1287" height="502" alt="Screenshot 2025-11-18 151518" src="https://github.com/user-attachments/assets/d5b016f6-8433-40cc-8452-a74fc63d3d15" />

In this image we can clearly see that the there are two way to reach at 'd' point by taking the worst path delay and low path delay. As earlier we have the worst path so the slack came to be negative but in this situation if we take less time delay path then the slack shuold come positive.

Also in the real world the lower time delay path should be taken.Then by taking the best path then at 'd' point the arrival time come out to be 6.9 not 7.8.

So the worst case path is also called as Graph Based Analysis(GBA) and best case path is caleed as Path Based Analysis(PBA). 

By taking the arrival time 6.9 at 'd' point, at output pin the slack become 7.0.

Now take this into another level by taking pin node convection with same circuitry by making the input and output of all gates to nodes like for 'a' input is like 'a1' and output is 'a2' and for the time delay of gate a shown by 2 by making the vertices between a1 to a2.

The detailed timing analysis with the help of pin node convection in which we represent the time delay, arrival time, required arrival time and slack.

With this slack timing graph we can check where we have to make changes for nwgative slack that can be done easily as shown in figure: 
<img width="1303" height="473" alt="Screenshot 2025-11-18 160156" src="https://github.com/user-attachments/assets/069f7f5b-33f2-4f2d-992d-be9e41b0f12c" />

---

Now let's forward to next level i.e. open the launch and the capture flop and see the trnasistor level of circuitry.

Firstly we have to see the give justification why we have doing that. 

let's take the clock frequency is 1 GHz and time period is 1 ns under scenerio setup max path analysis tells us that the combination delay or delay from the clock generation to D  input of capture flop should be less than clock period.

let's take the combinational delay is θ and the time period is T then it is necessary to have less combinational delay then time period i.e. θ<T. This consideration is done without using any buffer or can be said to be ideal case means the data should be reached the capture flop before clock period T.

Now by using CTS add the buffer between clock path but by adding the buffer the condition should remain unchanged i.e. θ<T but there are modifications done due addtion of buffer i.e.(θ+1+2) < (T+1+3+4) 

<img width="1453" height="815" alt="Screenshot 2025-11-21 181021" src="https://github.com/user-attachments/assets/d47fc79f-2660-4ce1-943c-7a585c73b95d" />

Here 1 represent the time delay of 1st buffer likewise 2 represent the time delay of 2nd buffer and so on.

Lets take Δ1 = (1+2) and Δ2 = (1+3+4).

Here if the clock reached to launch flop at 0ns now reached to Δ1ns same for capture flop now the clock reached by (T+Δ2)ns.

Also the difference of Δ1 and Δ2 is called as skew.

skew = Δ1 + Δ2,

Now open up the capture flop and check about the timing constraint in it. As the D flip flop is made of 2 MUX in which one is negative latch and 2nd is positive latch.

The differnce between negative and positive latch is just how we connect the clock to nmos and pmos which can be seen by the given figures
<img width="1473" height="597" alt="Screenshot 2025-11-21 002843" src="https://github.com/user-attachments/assets/f1f7d825-734c-4e24-83a5-be6d025b67d1" />

So the negative latch operates on negative level of clock and positive latch on positive level clock and the combination of both represents the flip flop.

Latch is made of two transmission gates which is made of pmos pass transistor and nmos pass transistor and thesee transmission is connected with invertor. Here the value of clock decide whether the gates will work or not.
 
Let's give a ideal clock, as the transition time from low to high or high to low is zero.

As negative latch based on the ideal clock so for the negative level of the clock the Tr1 will be active i.e. nmos and pmos will be active and there will be direct path between the D input and output Qm so at D input what will be latch out at Qm. Now the time required from input to output is depend on  Tr1 and 2 invertor.Here the Tr3 is also active but there is no output till now then there will be don't care condition.


<img width="1445" height="618" alt="Screenshot 2025-11-21 004354" src="https://github.com/user-attachments/assets/e15b519d-9f64-4faa-84e8-8a66125b15eb" />

Now talk about the positive in which will be active at positive then the Tr2 and Tr4 will be active as from past output at Qm the Tr2 will give the same output and for Tr4 the output from the Tr1 will be act a input of Tr4 then there will be transmission between the input of Tr4 and output i.e. output is present as D. This is how we get the output.

Now connect the positive and negative latch which give us a D flip flop. This flip flop is based on positive edge triggered flip flop using master slave configuration.
<img width="1474" height="664" alt="Screenshot 2025-11-21 190929" src="https://github.com/user-attachments/assets/1b889039-3831-4300-ad84-21e4fd9d8999" />

here we see that the first is negative latch so the it will wait for negative or low signal for sending the input data to Qm i.e. to the invertor no. 5 that is connected to input of tansmission gate 4.

So when the negative level comes then Qm get the D input and Tr2 holds the data so that when the positive level of clock come then it send it to Tr4 like this we get the output from the D input. Now again the negative level of clock will come fot this Tr3 will hold the value till again the positive level come.This is the way the input D comes out to be output Q.

Set-up time:- Time before rising edge of clock that the input D become valid i.e. D input has to be stable such that Qm is sent out to Q reliably.

  Input D takes time to reach Tr4 is delay of 3 of invertor and 1 transmission gate delay to become stable before rising edge of clock.

  Here there are couples of things we have to consider i.e. 
  1. Library set up time :- for the capture flop.
  2. Clocl to Q delay:- needed by the launch flop i.e. the amount of time in which data will take time to get out of particular flop.When we look into the clock to Q delay it is said that application of clock     after that the input comes out of the flip flop.

Also the D input for Tr4 i.e. D' is already at the input of Tr4 and during the positive level of clock it took time of dealy of Tr4 and the delay of invertor 6 for reaching to output i.e. Q.

Hold time:- It is the time need to D input to be stable after the application of clock. In this for positive clock the Tr1 is off, so D is allowed to change after the clock edge so hold time for this will be zero.

Library setup time:- Time required for the data to stablised within the capture flop
    (θ + Δ1) < (T + Δ2) - S

---

## JITTER 
Eye diagram:- It gets from the outside the timing analysis i.e. provided by the foundry.
Lets takes idealistic case for clock i.e. there is no jitter as shown below  
<img width="1407" height="646" alt="Screenshot 2025-11-21 110051" src="https://github.com/user-attachments/assets/765dc2c6-d70c-4be3-affc-4ab879e65dde" />

This is the first level of eye diagram.

Now take some realistic scenerio i.e. zeroth edge of clock signal which is suppoose to come at zeroth time point but there is variation over here due to clock path, which is very huge, the result is that at each point receive clock at different time but somewhere zeroth. 
<img width="1282" height="640" alt="Screenshot 2025-11-21 110803" src="https://github.com/user-attachments/assets/671e266d-b81e-4ee5-beb6-7b3dc0e79b99" />
This is the second level of eye diagram.

There ia another of idealistic power supply i.e. power is constant at level but in real there is variation in power supply like voltage deop and ground bound.

Now combine the eye diagram and power supply variation for realistic case 
<img width="936" height="330" alt="Screenshot 2025-11-21 120244" src="https://github.com/user-attachments/assets/97b7338d-31ad-4b2f-9a6f-3cb5440cfbac" />
This is the third level of eye diagram(more realistic)

--- 

NOISE MARGIN:- Noise margin is the safe electrical tolerance that prevents noise from corrupting logic levels. It defines how much disturbance a digital signal can survive while still being interpreted as the correct binary value.

There is range of data till the electrical appliance consider that as low or high.

Jitter:- The temporary variation in clock period is called as jitter
<img width="1060" height="567" alt="Screenshot 2025-11-21 125342" src="https://github.com/user-attachments/assets/5912efe8-cffc-4182-b0ef-dd930b98850a" />

If the clock period arrived before 0ns i.e. (0-Δ1) and complete after (T+Δ2) then there is increament in clock period and vice versa. so this is the temporary variation in clock period is called as jitter. 
and this jitter is model with parameter called 'uncertainity'.
This uncertainity is subtracted from the clock period and this is accountaibility in the timing analysis i.ie.
    this uncertainity is represented by SU then the delay equation become
    (θ + Δ1) < (T + Δ2) - S - SU
    <img width="1423" height="787" alt="Screenshot 2025-11-23 011623" src="https://github.com/user-attachments/assets/2f7f1913-7ffd-4aea-9db1-6fddac851930" />

That's all for setup timing analysis for single clock.
