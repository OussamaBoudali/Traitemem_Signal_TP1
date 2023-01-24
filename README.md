# Traitemem_Signal_TP1
 # Objectifs
Représentation de signaux et applications de la transformée de Fourier discrète
(TFD) sous Matlab.
 Evaluation de l’intérêt du passage du domaine temporel au domaine fréquentiel
dans l’analyse et l’interprétation des signaux physiques réels.
# Représentation temporelle et fréquentielle 
## 1)Tracer le signal x(t). Fréquence d’échantillonnage : fe = 10000Hz, Intervalle : Nombre d’échantillons : N = 5000.
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
