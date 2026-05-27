## EXP NO: 5 DESIGN OF FIR FILTER USING RECTANGULAR WINDOWS 
## DATE :

## AIM:

To design a linear phase FIR band stop filter to reject frequencies in the range 0.4π  to 0.65π rad/sec using rectangular window , by taking 7 samples of window sequence using matlab.

## ALGORITHM:

1. Assign the variable for pass band ripple ,stop band ripple, pass band and stop band frequency

2. Determine the order of filter using the required formula.
	
3. Find the filter co-efficient b.
	
4. Assign the time and amplitude.
	
5. Plot the magnitude and phase angle for LPF.HPF,BPF&BSF.
	
6. Give the x label and ylabel and title it.

   
## PROGRAM:
```
clear all;
clc;

Wc1 = 0.4*pi;
Wc2 = 0.65*pi;

N = 7;

a = (N-1)/2;

% Center coefficient
hna = 1 - ((Wc2 - Wc1)/pi);

% Calculate impulse response coefficients
k = 1:(N-1)/2;
n = k - 1 - a;

hd = (sin(Wc1*n) - sin(Wc2*n))./(pi*n);
hn = hd;

% Complete impulse response
Hn = [hn hna fliplr(hn)];

disp('Impulse Response Coefficients:');
disp(Hn);

% Frequency response
w = 0:pi/16:pi;

Hw1 = hna*exp(-1j*w*a);
Hw2 = zeros(size(w));

for m = 1:a
    Hw3 = hn(m) * (exp(1j*w*(1-m)) + exp(-1j*w*(1-m+2*a)));
    Hw2 = Hw2 + Hw3;
end

Hw = Hw1 + Hw2;

H_mag = abs(Hw);

figure;
plot(w/pi, H_mag, 'k', 'LineWidth', 1.5);
grid on;

title('Magnitude Response', 'FontWeight', 'bold');
xlabel('Normalized Frequency, \omega/\pi', 'FontWeight', 'bold');
ylabel('Magnitude', 'FontWeight', 'bold');
```

## OUTPUT 
<img width="936" height="1018" alt="image" src="https://github.com/user-attachments/assets/6ccedac2-9390-4391-87c0-aba0b9a502c9" />


## RESULT
Thus the FIR filter with the given specifications was designed using rectangular windowing technique.
