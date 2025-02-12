# Laboratorio de procesamiento digital de señales #2
                                                                       Silvana Pardo Cepeda

# Introducción
 En este laboratorio tenemos como objetivo analizar y comprender la convolución, la correlación y la transformación de señales en el dominio de la frecuencia.
La convolución corresponde a la descripción de  la respuesta de un sistema a una señal de entrada, la cual calculamos tanto manualmente como con la utilización de python entre una señal x[n] y un sistema h[n], donde los datos fueron obtenidos de los documentos personales de cada uno.
La correlación  la utilizamos para medir la similitud entre señales en función del tiempo o el desplazamiento, a través de dos señales sinusoidales y la representamos gráficamente.
Por último,  utilizamos como herramienta una señal de electromiografía, obtenida de la base de datos physionet, con la que obtuvimos estadísticos descriptivos como  frecuencia media, frecuencia mediana, desviación estándar, histograma de frecuencias, analizando a través de la transformada de fourier  estas señales en el dominio de la frecuencia, y obteniendo su gráfica su transformada, como su densidad espectral. 

# Convolución a mano y digitalizada 
Inicialmente tomamos los datos de nuestros documentos de identidad y código estudiantil, y realizamos la convolución  manualmente, que consiste en hacer una serie de multiplicación que relaciona la señal x[n] y un sistema h[n], y realizamos también su respectiva gráfica individualmente para  x[n] y para  h[n], y una gráfica que las relaciona,  como se puede ver a continuación:

![image](https://github.com/user-attachments/assets/40cb0544-0997-4f34-9ebb-fb4d986cef6e)
![image](https://github.com/user-attachments/assets/8a4532d6-898d-4b4c-8ea4-fed0c75b5acd)
![image](https://github.com/user-attachments/assets/f0dad6c3-c6a4-4f82-8f71-0c2359f3c43a)
![image](https://github.com/user-attachments/assets/03ee50e5-fb9c-40fe-aadb-cfa73c9a5614)



Posteriormente, se realizó el mismo proceso a través de las herramientas de python, programando tanto el cálculo de la convolución como sus gráficas respectivamente, y lo obtuvimos así:


![image](https://github.com/user-attachments/assets/b08e5eaf-65a7-4d4a-aa7f-b80015eefbb8)
![image](https://github.com/user-attachments/assets/0d55882e-e5ba-4589-9512-b7b5ce8c6f84)
![image](https://github.com/user-attachments/assets/35cec8ef-b47b-4a19-b89b-ef362dae3403)
![image](https://github.com/user-attachments/assets/8e561244-c4a7-45b0-8f06-fcbc91a34d15)
![image](https://github.com/user-attachments/assets/fd2a7358-aee3-48a6-9f62-bfb2ee90e453)

 Primero definimos dos arreglos NumPy h[n] que representa la respuesta de un sistema, y x[n], que es la señal de entrada. Luego, generamos la convolución con np.convolve(h, x), lo que genera una nueva señal y[n] que es la versión procesada de x[n] al pasar por el sistema h[n] Para visualiza el proceso hacemos tres gráficos con Matplotlib, el primero muestra h[n] el segundo muestra x[n] y el tercero muestra y[n], la salida del sistema. 
 
# Correlación
Para hallar la correlación  que mide la similitud entre dos señales en función del desplazamiento que la podemos definir como  la suma ponderada del producto de las señales desplazadas en el tiempo, y puede ser autocorrelación (cuando se compara una señal consigo misma) o correlación cruzada (cuando se comparan dos señales diferentes)que es nuestro caso, la obtuvimos así:


![image](https://github.com/user-attachments/assets/2dbce0c7-7719-4de6-b0cb-e55fc2be31ff)
![image](https://github.com/user-attachments/assets/4c5a1d45-cac3-4a2c-8fac-fa967207f74e)


A partir de las dos señales, una frecuencia de 100 Hz y un periodo de muestreo de 1.25 ms, calculamos su correlación cruzada utilizando np.correlate(), que mide la similitud entre ambas señales, se grafican las señales originales y su correlacion  utilizando gráficos de líneas discretas plt.stem(), lo que nos  permite visualizar cómo varía la relación entre las señales dependiendo del retardo aplicado.


![image](https://github.com/user-attachments/assets/e9184ce6-98a5-4fd8-9e24-38526a50b33a)


# Descarga e importación de la señal, estadísticos descriptivos, transformada de fourier y estadísticos en función de frecuencia

Se utilizó la base de datos gratuita PhysioNet que permitió la descarga de una señal electromiográfica, el archivo fundamental .mat indispensable para que se logre la lectura de la señal.
Creamos una carpeta en el escritorio del computador donde agregamos este archivo y el archivo de código python donde haremos la programación necesaria.
Abrimos el archivo python y anteriormente debimos haber descargado la librería wfdb para logar la lectura de la señal desde el archivo, graficamos los datos de el EMG en el dominio del tiempo, que se debe ver asi (ejemplo):


![image](https://github.com/user-attachments/assets/e3f8a3f3-a126-4cc7-bca9-4eec66b8dbdc)
![image](https://github.com/user-attachments/assets/0be44933-edc3-4021-be16-2467e1b8b626)
![image](https://github.com/user-attachments/assets/bde4ef18-e044-4c66-92e5-b4e4a2957d3d)



Luego de este paso, calculamos los estadísticos descriptivos de la señal calculados y por funciones:


![image](https://github.com/user-attachments/assets/02d348c1-afe6-478c-a18b-3f07cb6e0a88)
![image](https://github.com/user-attachments/assets/5c48512e-960a-40cf-b6b3-f3dec2d315ad)


Media de la señal: Representa el valor promedio de la señal.


Desviación estándar: Indica la dispersión de la señal con respecto a la media.


Coeficiente de variación: Relación entre la desviación estándar y la media.

![image](https://github.com/user-attachments/assets/c2d18bee-6198-4e5c-8134-e787c65dcbbb)

La señal EMG es una señal aleatoria, aperiódica, que puede ser discreta o continua dependiendo de sus muestras, de potencia y con frecuencia predominante entre 20 Hz y 500 Hz. 


La transformada de fourier convierte una señal en el dominio del tiempo a un dominio de la frecuencia. Para nuestra señal electromiográfica (EMG), la transformada nos permite analizar qué componentes de frecuencia están presentes en la actividad muscular registrada.
A continuación, el cómo obtenemos esta gráfica:


![image](https://github.com/user-attachments/assets/abc43fd0-260e-4951-8e63-21a5a87bb23a)
![image](https://github.com/user-attachments/assets/12db85b5-6ef5-459e-86c5-b7522bcca5d5)

Graficamos  la magnitud de la transformada  usando plt.plot(frecuencias, trs_magnitud), donde frecuencias representa los valores en Hz y trs_magnitud indica la intensidad de cada frecuencia, lo que nos permite identificar el rango de frecuencias, eliminar ruido y visualizar una señal en diferentes estados musculares.

Posteriormente,calculamos y obtenemos su densidad espectral:

![image](https://github.com/user-attachments/assets/77dd2a74-9c7e-416a-ba79-824f09778893)

 Utilizamos el método de Welch, que mejora la estimación espectral al dividir la señal en segmentos de 4000 muestras y promediar sus espectros, esta función welch(emg, fs, nperseg=4000) nos muestra cómo se distribuye la potencia de la señal en diferentes frecuencias. Luego, graficamos con plt.semilogy(), y obtenemos la siguiente gráfica:

![image](https://github.com/user-attachments/assets/d4669350-c829-4c81-9951-b91621ee72e6)


Para finalizar, realizamos los cálculos de los estadísticos en función de la frecuencia:

La frecuencia media es el promedio ponderado de las frecuencias en el espectro de la señal


 La frecuencia mediana es el valor que divide el espectro en dos partes con igual energía 

 
La desviación estándar de la frecuencia(fourier) mide la dispersión de las frecuencias respecto a la media

Fueron calculados de esta forma:
![image](https://github.com/user-attachments/assets/5080d674-3673-4bb1-9c67-a64662e1c078)
![image](https://github.com/user-attachments/assets/c54d8c1a-3efe-4529-8f40-ddd3b6461e8f)


 El histograma de frecuencias representa gráficamente la distribución de energía en distintos rangos de frecuencia

 
 ![image](https://github.com/user-attachments/assets/d3de93fb-2da2-4d2a-b69a-e34e1e936ff8)
 ![image](https://github.com/user-attachments/assets/4c0758dc-192f-454e-8c62-d0d849a7cb7a)

 # Conclusiones 
A partir de este laboratorio logramos poner en práctica los conceptos de convolución, correlación, transformada de fourier, estadísticos en dominio de tiempo y de frecuencia y sus respectivas gráficas, utilizando la convolución que nos permite obtener la respuesta de un sistema a una señal de entrada, cómo la correlación mide la semejanza entre dos señales y cómo la transformada de Fourier descompone una señal en sus componentes espectrales. Además, la densidad Espectral  mediante el método de Welch  nos permitió analizar la distribución de energía de una señal electromiográfica, lo que nos permite el estudio de la actividad muscular y la detección de trastornos neuromusculares, siendo herramientas fundamentales para utilizar en estudios y aplicaciones biomédicas, que es el enfoque de nuestra práctica.


 # Bibliografía
 -https://archive.physionet.org/cgi-bin/atm/ATM
 -Cáceres, J. P., & Aditiva, S. (2007). Transformada de Fourier. Londres: Stanford University.
 - HERNÁNDEZ, A., MORA, N. J. E., & VEGA, H. R. (2020). Enseñanza en el análisis de señales aleatorias usando correlación y sus aplicaciones. Utopía y Praxis Latinoamericana, 25(3),
   190-200.





