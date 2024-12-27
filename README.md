# Compare-frequency-response-of-FIR-filter-using-various-window-function-in-SIMULINK-MAT-LAB
Digital signal processing often involves designing Finite Impulse Response (FIR) filters to meet specific frequency domain requirements. FIR filters are characterized by their impulse response, which is finite in duration, making them computationally efficient and offering desirable properties such as linear phase response.


Matlab program: 



clc;
clear all; close all; n=20; fp=200; fs=600; f=1000; wp=2* (fp/f)
WS=2*(fs/f)
wn= [wp, ws ]
%window=boxcar(n+1); % rectangular window %window=bartlett(n+1);% traiangular window %window=hamming (n+1);% hamming wondow %window= hanning (n+1);% hanning window window= kaiser(n+1); % kasiser window wn=2*(fp/fs)
/b=fir1(n, wn, window)
b=fir1(n,wn, 'high', window)
[H,w]=freqz(b, 1)
subplot (2,1,1)
plot(w/pi, 20*1og(abs(H)))
xlabel( 'nf')
ylabel ('mag in dB' )
title("mag response")
subplot (2,1,2)
plot(w/pi, angle(H))
xlabel('nf')
ylabel ( 'mag in dB')
title("phase response")
