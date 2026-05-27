## EXP NO:03	DESIGN OF DIGITAL BUTTERWORTH IIR FILTER 

## DATE :

## AIM:

To design a digital Butterworth filter using bilinear method satisfying the constraints using matlab. Assume T=1 sec


		          0.707 ≤│H(w)│≤ 1.0        ; 0 ≤w ≤ 0.2 π
                                             │H(w)│≤  0.08     ; 0.4π ≤ w ≤ π

## ALGORITHM:

Start the matlab software

Assign the variable for pass band ripple ,stop band ripple, pass band and stopband frequency

Determine the order of filter using the required formula.

Find the filter co-efficient a and b.

Assign the time and amplitude.

Plot the magnitude and phase angle.

Give the x label and ylabel and title it.

Save and run the program.


## PROGRAM:

```
clear all
clc

AP=0.707;					
AS=0.08;					
PEF_D=0.2*pi;					
SEF_D=0.4*pi;					
T=1;						
alpha_P=-20*log10(AP)				
alpha_S=-20*log10(AS)				

PEF_A=(2/T)*tan((PEF_D/2)
SEF_A=(2/T)*tan((SEF_D/2)

[N,CF]=buttord(PEF_A,SEF_A,alpha_P,alpha_S,'s')        

[Bn,An]=butter(N,,1,'s');				
display('Normalized Transfer Function is,')
Hsn=tf(Bn,An)

[B,A]=butter(N,CF,'s');				
display('Unnormalised Transfer Function is,')
Hs=tf(B,A)

[num,den]=bilinear(B,A,1/T);			
% Digital Transfer Function
display('Digital Transfer Function is,')
Hz=tf(num,den,T)

w=0:pi/16:pi;
display('Frequency Response is,')
Hw=freqz(num,den,w)				
% Frequency response
display('Magnitude Response is,')
Hw_mag=abs(Hw)				
% Magnitude response
plot(w/pi,Hw_mag,'k');grid;

title('Magnitude Response of Butterworth 3rd order Lowpass Filter','fontweight','b');
xlabel('Normalised frequency, \omega/\pi','fontweight','b');
ylabel('Magnitude','fontweight','b');

```




## OUTPUT

<img width="957" height="1013" alt="image" src="https://github.com/user-attachments/assets/a0f12b44-6388-48a1-a992-d8b9f3885560" />




 






## RESULT:

Thus, digital Butterworth IIR filter with the given specifications was designed using MatLab.
 
