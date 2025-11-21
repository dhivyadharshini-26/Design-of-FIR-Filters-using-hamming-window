# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;


M = input("Enter the Odd Filter Length = ");    
Wc = input("Enter the Digital Cutoff Frequency (in radians) = ");  

alpha = (M - 1) / 2;   

for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;  
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

for n = 1:M
    W(n) = 0.54 - (0.46 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

h = hd .* W;
disp(h, "Filter Coefficients are:");


[hzm, fr] = frmag(h, 256); 

subplot(2,1,1);
plot(2*fr, hzm);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude");
title("Frequency Response of FIR LPF using Hamming Window");

subplot(2,1,2);
hzm_dB = 20 * log10(hzm);
plot(2*fr, hzm_dB);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude (dB)");
title("Frequency Response of FIR LPF using Hamming Window (in dB)");
```

# OUTPUT

<img width="1893" height="1199" alt="E4 - FIR(hamming)" src="https://github.com/user-attachments/assets/b025611e-b6fd-4e84-85f3-c89c63f77b21" />

# RESULT

Thus the design of low pass FIR digital filter was generated using SCILAB.
