## AIM:
To demonstrate ideal sampling of a continuous signal using Scilab, ensuring accurate signal reconstruction while avoiding aliasing

## COMPONENTS REQUIRED:
python IDE with Numpy and Scipy

## PROGRAM:
~~~
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample
fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
~~~
## OUTPUT WAVEFORMS:
![image.](https://github.com/user-attachments/assets/a1fee3ef-4ac4-4e48-bf17-3d76f89f64e5)

![image.](https://github.com/user-attachments/assets/a9f1224d-0ed1-4e77-be81-ceaf74363694)


![image.](https://github.com/user-attachments/assets/d6a778be-774a-49f3-b130-25ae48bdbbe7)


## RESULT:
Ideal sampling captures a continuous signal at perfect intervals, ensuring accurate reconstruction if sampled at twice the highest frequency (Nyquist rate). It’s a key concept in digital signal processing and telecommunications. Practical systems approximate ideal sampling with some limitations.
