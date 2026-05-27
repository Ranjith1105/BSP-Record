## EXP NO: 6  QRS COMPLEX DETECTION FROM ECG SIGNAL

## DATE :

## AIM

To analyze the ECG signal using MATLAB and extract important features such as heart rate, QRS complex, and waveform visualization.

## APPARATUS / SOFTWARE REQUIRED

1. Computer with MATLAB installed

2. Sample ECG signal file (.mat or .csv)

3. Biomedical Signal Processing Toolbox (if available)


## THEORY

The Electrocardiogram (ECG) is a bioelectrical signal that represents the electrical activity of the heart over time.

A typical ECG waveform consists of P-wave, QRS complex, and T-wave.

Analysis of ECG helps in detecting cardiac abnormalities such as arrhythmia and myocardial infarction.

Key parameters in ECG analysis include:

•	Heart rate (beats per minute)

•	R-R interval (time between successive R-peaks)

•	Amplitude of QRS complex

•	Signal filtering to remove baseline wander and noise


## ALGORITHM 

1.	Load the ECG signal into MATLAB.
	
2.	Plot the raw ECG signal to visualize waveform characteristics.
	
3.	Apply preprocessing filters:
	
   	  Remove 50 Hz power-line noise using a notch filter.

      Remove baseline drift using a high-pass filter (cutoff ≈ 0.5 Hz).

4.	Detect R-peaks using the Pan–Tompkins algorithm or MATLAB’s findpeaks() function.
	
5.	Compute heart rate from R-R intervals.
	
6.	Plot the filtered ECG with detected R-peaks.
	
7.	Display extracted parameters such as heart rate and number of beats.




## MATLAB Code:
```
clear;
clc;
close all;

fs = 360;
t = 0:1/fs:5;

% Baseline ECG components
ecg = 0.8*sin(2*pi*1*t) + 0.4*sin(2*pi*2*t);

% Add sharp QRS complexes
r_locs = [0.2 1.2 2.2 3.2 4.2];
for k = 1:length(r_locs)
    ecg = ecg + 5*exp(-((t-r_locs(k))/0.025).^2);
end

% Small noise
ecg = ecg + 0.02*randn(size(t));

% Filter
[b,a] = butter(4,[0.5 40]/(fs/2),'bandpass');
ecg_filt = filtfilt(b,a,ecg);

% Detect R-peaks
[pks,locs_R] = findpeaks(ecg_filt,...
    'MinPeakHeight',3,...
    'MinPeakDistance',round(0.5*fs));

% Heart rate
RR = diff(locs_R)/fs;
HR = 60./RR;
Avg_HR = mean(HR);

% Plot
figure;
plot(t,ecg_filt,'b','LineWidth',1.2);
hold on;
plot(locs_R/fs,pks,'ro','MarkerFaceColor','r','MarkerSize',8);

grid on;
title('Synthetic ECG with Detected QRS Complexes');
xlabel('Time (s)');
ylabel('Amplitude (mV)');
legend('Filtered ECG','R peaks');

fprintf('Average Heart Rate = %.2f bpm\n',Avg_HR);

```

## Sample Output:

•	ECG waveform plotted with identified R-peaks.

•	Display of average heart rate (e.g., Average Heart Rate = 76.45 bpm).

•	Clean, denoised ECG signal after filtering.


## OUTPUT
 
<img width="958" height="1018" alt="image" src="https://github.com/user-attachments/assets/70bf4a7f-98d1-4085-b2f0-61ae5be104f8" />


## RESULT:

The ECG signal was successfully analyzed using MATLAB.

The QRS complex was detected, and the average heart rate was computed accurately.

