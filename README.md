# Design of FIR Filters using Hamming Window
# DESIGN OF LOW PASS AND HIGH PASS FIR DIGITAL FILTER
## AIM

To design and implement Low Pass and High Pass FIR digital filters using the Hamming Window method in SCILAB.

## APPARATUS REQUIRED

PC installed with SCILAB

## PROGRAM
# Low Pass FIR Filter
~~~
clc;
clear;
close;

// Low Pass FIR Filter using Hamming Window
N = 31; // Filter length
fc = 0.3; // Normalized cutoff frequency (fc = Fcutoff / (Fs/2))
n = 0:N-1;
alpha = (N-1)/2;

// Hamming window
w = 0.54 - 0.46cos(2%pi*n/(N-1));

// Ideal Low Pass Filter Impulse Response
hd = zeros(1, N);
for i = 1:N
if (i-1) == alpha then
hd(i) = 2fc;
else
hd(i) = sin(2%pifc(i-1-alpha)) / (%pi*(i-1-alpha));
end
end

// Multiply by window
h = hd .* w;

// Frequency Response
[H, f] = frmag(h, 512);

// Plot
figure;
subplot(2,1,1);
plot(f, 20*log10(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title('LOW PASS FIR FILTER (Hamming Window)');

subplot(2,1,2);
plot(f, atan(imag(H), real(H)));
xlabel('Normalized Frequency');
ylabel('Phase (radians)');
title('Phase Response');
~~~

# High Pass FIR Filter
~~~
clc;
clear;
close;

// High Pass FIR Filter using Hamming Window
N = 31; // Filter length
fc = 0.3; // Normalized cutoff frequency
n = 0:N-1;
alpha = (N-1)/2;

// Hamming window
w = 0.54 - 0.46cos(2%pi*n/(N-1));

// Ideal High Pass Filter Impulse Response
hd = zeros(1, N);
for i = 1:N
if (i-1) == alpha then
hd(i) = 1 - 2fc;
else
hd(i) = -sin(2%pifc(i-1-alpha)) / (%pi*(i-1-alpha));
end
end

// Multiply by window
h = hd .* w;

// Frequency Response
[H, f] = frmag(h, 512);

// Plot
figure;
subplot(2,1,1);
plot(f, 20*log10(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title('HIGH PASS FIR FILTER (Hamming Window)');

subplot(2,1,2);
plot(f, atan(imag(H), real(H)));
xlabel('Normalized Frequency');
ylabel('Phase (radians)');
title('Phase Response');
~~~

## OUTPUT
# Low Pass FIR Filter
<img width="948" height="821" alt="image" src="https://github.com/user-attachments/assets/8f2bd5c0-0ba2-4746-a7f8-12d46f4fdd76" />


# High Pass FIR Filter
<img width="941" height="748" alt="image" src="https://github.com/user-attachments/assets/3028ab60-61b6-42bf-beb8-f4c90dc9ab06" />


## RESULT
The Low Pass and High Pass FIR digital filters were successfully designed and implemented using the Hamming Window method in SCILAB.
