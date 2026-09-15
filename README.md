# Design-of-FIR-Filters-using-rectangular-window
# EXP 4 A : DESIGN OF FIR DIGITAL FILTERS USING RECTANGULAR WINDOW
# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM for LPF,HPF,BPF, BSF
```
clc;
clear;
close;



N = 21;
M = 10;

fc = 0.3;
f1 = 0.2;
f2 = 0.5;

n = (0:N-1)';
w = ones(N,1);


hLP = zeros(N,1);

for k = 1:N
    if n(k) == M then
        hLP(k) = fc;
    else
        hLP(k) = sin(%pi*fc*(n(k)-M)) / ...
                 (%pi*(n(k)-M));
    end
end

hLP = hLP .* w;


hHP = zeros(N,1);

for k = 1:N
    if n(k) == M then
        hHP(k) = 1 - fc;
    else
        hHP(k) = -sin(%pi*fc*(n(k)-M)) / ...
                 (%pi*(n(k)-M));
    end
end

hHP = hHP .* w;


hBP = zeros(N,1);

for k = 1:N
    if n(k) == M then
        hBP(k) = f2 - f1;
    else
        hBP(k) = (sin(%pi*f2*(n(k)-M)) - ...
                  sin(%pi*f1*(n(k)-M))) / ...
                 (%pi*(n(k)-M));
    end
end

hBP = hBP .* w;


hBS = zeros(N,1);

for k = 1:N
    if n(k) == M then
        hBS(k) = 1 - f2 + f1;
    else
        hBS(k) = (sin(%pi*f1*(n(k)-M)) - ...
                  sin(%pi*f2*(n(k)-M))) / ...
                 (%pi*(n(k)-M));
    end
end

hBS = hBS .* w;


disp("LPF Coefficients:");
disp(hLP);

disp("HPF Coefficients:");
disp(hHP);

disp("BPF Coefficients:");
disp(hBP);

disp("BSF Coefficients:");
disp(hBS);


scf(1);
clf();

subplot(2,2,1);
plot2d3(n, hLP);
xtitle("LPF Impulse Response", "n", "hLP(n)");
xgrid();

subplot(2,2,2);
plot2d3(n, hHP);
xtitle("HPF Impulse Response", "n", "hHP(n)");
xgrid();

subplot(2,2,3);
plot2d3(n, hBP);
xtitle("BPF Impulse Response", "n", "hBP(n)");
xgrid();

subplot(2,2,4);
plot2d3(n, hBS);
xtitle("BSF Impulse Response", "n", "hBS(n)");
xgrid();


xLP = zeros(1024,1);
xHP = zeros(1024,1);
xBP = zeros(1024,1);
xBS = zeros(1024,1);

xLP(1:N) = hLP;
xHP(1:N) = hHP;
xBP(1:N) = hBP;
xBS(1:N) = hBS;


HLP = fft(xLP, 1);
HHP = fft(xHP, 1);
HBP = fft(xBP, 1);
HBS = fft(xBS, 1);


f = (0:511)' / 512;

magLP = abs(HLP(1:512));
magHP = abs(HHP(1:512));
magBP = abs(HBP(1:512));
magBS = abs(HBS(1:512));


scf(2);
clf();

subplot(2,2,1);
plot(f, magLP);
xtitle("LPF Frequency Response", ...
       "Frequency / pi", "Magnitude");
xgrid();

subplot(2,2,2);
plot(f, magHP);
xtitle("HPF Frequency Response", ...
       "Frequency / pi", "Magnitude");
xgrid();

subplot(2,2,3);
plot(f, magBP);
xtitle("BPF Frequency Response", ...
       "Frequency / pi", "Magnitude");
xgrid();

subplot(2,2,4);
plot(f, magBS);
xtitle("BSF Frequency Response", ...
       "Frequency / pi", "Magnitude");
xgrid();

```

# OUTPUT for LPF,HPF,BPF, BSF

<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/79299f80-3c4f-4540-a1e1-d948198fd268" />

<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/a7249342-7830-4dca-99f7-5fe7ec2dffb5" />

# RESULT

THE DESIGN OF FIR DIGITAL FILTER IS SUCCESSFULLY COMPLETED USING SCILAB.
