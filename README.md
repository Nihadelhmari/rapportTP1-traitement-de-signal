# rapportTP1-traitement-de-signal
lose all;
clear all;
clc;

Te=1/50;
t=0:Te:10-Te;
fe=50;
N=length(t);
x=sin(2*pi*15*t)+sin(2*pi*20*t);

plot(t,x);
%xlabel('temps');
%ylabel('x(t)');
%title('le signal x(t)');
y=fft(x);
f=(0:N-1)*(fe/N);
plot(f,abs(y));

 f1=-fe/2:fe/N:fe*(N-1)/(2*N);
 y1=fftshift(abs(y)); 
plot(f1,y1);
 
 % Génération du bruit
 sigma = 50;   % variance du bruit
 moy = 0;        % moyenne
 bruit = moy + sigma*randn(1,N);
 s= x + bruit;         % les 2 vecteurs sont de même longueur
%plot(s);
plot(x);

subplot(2,2,1);plot(t,x);title('signal périodique');
subplot(2,2,2); plot(f1,y1);title('les pics');
subplot(2,2,3);plot(t,signal);title('signal bruité');
tfd=fft(signal);
ds=(abs(tfd));
subplot(2,2,4);plot(t,ds);title('densité spectrale de puissance');

%partie1:q1&2

[x,fs]= audioread('bluewhale.au');%charger et lire le fichier %bluewhale.au%
  sound(x,4000);                   %ecouter le chant du rorqual bleu

subplot(2,2,1);
plot(x);
title('signal de blue ');

% %partie2 q3&q4(========)
 fichier =  "bluewhale.au";   %charger le fichier 
 [x,fs]= audioread(fichier);  %lire le fichier
 xx= x(2.45e4:3.10e4);        %Le son à récupérer correspond aux indicesallant de 2.45e4 à 3.10e4.
 sound(xx,4000)               %ecouter le chant du rorqual blue
 figure(1);                   
 N=length(xx);                
 y=abs(fft(xx)).^2/N;
 fshift=(-N/2: N/2-1)*(fs/N)/10;
 plot(fshift,fftshift(y));

 
