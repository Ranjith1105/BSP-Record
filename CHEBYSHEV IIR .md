## EXP NO: 4	DESIGN OF DIGITAL CHEBYSHEV IIR FILTER

## DATE :

## AIM:

To design a digital Chebyshev filter using bilinear method satisfying the constraints using matlab. Assume T=1 sec

0.8 ≤│H(w)│≤ 1.0               ; 0 ≤w ≤ 0.2 π
                                                      │H(w)│≤  0.2              ; 0.32 ≤ w ≤ π

## ALGORITHM:


1. Start the  matlab software.
 
2. Assign the variable for pass band ripple ,stop band ripple, pass band and stop band frequency.
 
3. Determine the order of filter using the required formula.
   
4. Find the filter co-efficient a and b.

5. Assign the time and amplitude.
 
6. Plot the magnitude and phaseangle.
 
7. Give the x labe land ylabel and title it.
    
8. Save and run the program.

## PROGRAM:

```
clear all
clc

AP=0.8;						
AS=0.2;						
PEF_D=0.2*pi;					
SEF_D=0.32*pi;					
T=1;						
alpha_P=-20*log10(AP)				
alpha_S=-20*log10(AS)				

PEF_A=(2/T)*tan(PEF_D/2)
SEF_A=(2/T)*tan(SEF_D/2)

[N,CF]=cheb1ord(PEF_A,SEF_A,alpha_P,alpha_S,'s')	

[Bn,An]=cheby1(N,alpha_P,1,'s');			
display('Normalized Transfer Function is,')
Hsn=tf(Bn,An)

[B,A]=cheby1(N,alpha_P,CF,'s');			
display('Unnormalised Transfer Function is,')
Hs=tf(B,A)

[num,den]=impinvar(B,A,1/T);			
display('Digital Transfer Function is,')
Hz=tf(num,den,T)

w=0:pi/16:pi;
display('Frequency Response is,')
Hw=freqz(num,den,w)				
display('Magnitude Response is,')
Hw_mag=abs(Hw)				
plot(w/pi,Hw_mag,'k');grid;

title('Magnitude Response of Chebyshev 3rd order Lowpass Filter','fontweight','b');
xlabel('Normalised frequency, \omega/\pi','fontweight','b');
ylabel('Magnitude','fontweight','b');
```




## OUTPUT

<img width="957" height="1018" alt="image" src="https://github.com/user-attachments/assets/27e282d8-e108-4190-a5c7-66219c2967d9" />





##  RESULT:

Thus,the digital Chebyshev filter with the given specifications was designed using MatLab.
 
