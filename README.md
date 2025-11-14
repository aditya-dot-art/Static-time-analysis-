# Static-time-analysis-
Learn about how the time configure in semiconductor level or chip level
#Arrival time:- It is the time to reach from the starting point to end point is called arrival time. 
Arrival time usually calculated at the end point.
As from the first image there are four end point are as D of first flip flop, D of second flip flop and there are two end point for output (OUT)port i.e. first from the D from second flip flop and one from the input port (IN).
Requird time:- It define what's the system specifications or need of system.
Example:- the frequency of the design is one gigahertz, so we have to make such a arrangements such that the arrival time fulfill the requirements of one gigahertz or one nanosecond.
Slack:- the diffence between the arrival time and required time. 
Example:- Tje data should be at the first flip flop should be between .5 ns to 3ns means the data can take the minimum time .5 ns and max time 3 ns.
Let's say that the arrival time is 3.5 ns then the diffence between the min time from arrival time is called as min slack time i.e 3ns and in the same way the difference between the arrival time from max time is max slack time.
The max slack time is known as setup slack or setup timing and the min slack time is known as hold slack hold timing.
Types of setup/hold analysis:-
1. reg2reg:- it is timing path from first flip flop or launch flop to next flip flp or capture flop.
2. in2reg:- it is timing path from input pin to launch flop .
3. reg2out:- it is timing path from capture flop output to output pin.
4. in2out:- it is timing path from input pin to output pin i.e. from giving input to getting the output.
5. clock getting:-it is for getting the timing path from other clock to clock of capturing flop or gate output. 
   for getting the clock at differnt flip flop or following circuit we don't using directly instead of we using the clock getting technique that is power saving which is combination of differnt logic gates and flip flops.
    This technique, clock getting, is useful switching the following circuit i.e. we can control wheather the output of launching flop should feed to capturing flop. 
7. recovery/removal:- it is tin=ming path from the another logic circuit to reset of flip flop that control to when to feed the reset signal.
# 1st is coming in to reg to reg and 2nd, 3rd and 4th IO TIMING. 
