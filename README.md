# Traitement_Signal_TP1
 # Objectifs
Représentation de signaux et applications de la transformée de Fourier discrète
(TFD) sous Matlab.
 Evaluation de l’intérêt du passage du domaine temporel au domaine fréquentiel
dans l’analyse et l’interprétation des signaux physiques réels.
# Représentation temporelle et fréquentielle 
### 1)Tracer le signal x(t). Fréquence d’échantillonnage : fe = 10000Hz, Intervalle : Nombre d’échantillons : N = 5000.
<img width="489" alt="Screenshot 2023-01-24 at 21 55 57" src="https://user-images.githubusercontent.com/87026851/214417510-da3df04b-1229-49b1-9c3f-62791dde3b64.png">

```
    fe = 1e4;
    te = 1/fe;
    N  = 10000;
    t  = (0:N-1)*te; 
    x  = 1.2*cos(2*pi*440*t+1.2)+3*cos(2*pi*550*t)+0.6*cos(2*pi*2500*t);
    f = (0:N-1)*(fe/N);
    y = fft(x);
    %Plot
    plot (t, x ,'.')
```
### 2)Calculer la TFD du signal x(t) en utilisant la commande fft, puis tracer son spectre en amplitude

<img width="515" alt="Screenshot 2023-01-24 at 22 18 44" src="https://user-images.githubusercontent.com/87026851/214418786-03890367-0bca-4233-9c9d-a000a0b2e0e6.png">

```
%representation du spectre du signal x Transformé de Fourier
    plot (f, abs(y))
    legend("y=fft(x)");
    xlabel("f");
    ylabel("A");
```
### 3)Pour mieux visualiser le contenu fréquentiel du signal, utiliser la fonction fftshift
<img width="485" alt="Screenshot 2023-01-24 at 22 24 39" src="https://user-images.githubusercontent.com/87026851/214420798-94dcb85f-4b78-4f3e-bff3-ef78783f39f0.png">

``` 
    fshift = (-N/2:N/2-1)*(fe/N); 
    z = fftshift(x);
   %on represente le spectre d'amplitude  centré à la fréquence  zéro.
    plot(fshift,fftshift(2*abs(y)/N));
    legend("Spectre d'Amplitude centré en 0");
    xlabel("f");
    ylabel("A");
```
### 4)Créer un nouveau signal xnoise, en introduisant un bruit blanc gaussien dans le signal d’origine x(t), puis visualisez-le.
<img width="466" alt="Screenshot 2023-01-24 at 22 37 28" src="https://user-images.githubusercontent.com/87026851/214426775-44526801-2b9d-41b9-9727-15cde46dc66e.png">

```
    bruit = 2*randn(size(x));%creation du bruit blanc gaussien de faible intensité
    xbruit = x+bruit;%on l ajoute au signal x
    plot(t,xbruit,'.')
```
### 5) Utiliser la commande sound pour écouter le signal et puis le signal bruité.
 
````
  sound(xbruit,fe)

### 6) Calculez puis tracer le spectre de puissance du signal bruité centré à la fréquence zéro.

````
    ybruit = fft(xbruit);%transformé de fourier du signal bruité 
    %on represente le spectre d'amplitude du signal bruité avec un bruit blanc gaussien de faible intensité
    plot(fshift,fftshift(2*abs(ybruit)/N))
    xlabel("f");
    ylabel("A");
