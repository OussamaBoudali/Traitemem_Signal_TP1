# Traitemem_Signal_TP1
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
