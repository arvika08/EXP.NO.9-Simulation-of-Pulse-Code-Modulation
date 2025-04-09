# EXP.NO.4-Simulation-of-Pulse-Code-Modulation


# AIM:

To simulate the process of Pulse Code Modulation (PCM), including sampling, quantization, encoding, and basic visualization of modulation/demodulation using Python.

# SOFTWARE REQUIRED:

Google Colab / Jupyter Notebook

Python 3.x

Required Libraries:

numpy for numerical operations

matplotlib for plotting


# ALGORITHMS:

Start the program.

Initialize parameters like sampling rate, frequency of analog signal, duration, and number of quantization levels.

Generate time vector using the sampling rate and duration.

Create an analog message signal using a sine wave.

Generate a clock signal with a higher frequency to simulate the sampling clock.

Quantize the analog message signal using defined quantization levels.

Encode the quantized signal into digital form by converting amplitude values to integer levels (PCM).

Plot the message signal, clock signal, quantized (PCM) signal, and demodulated signal.

End the program.


# PROGRAM:

import matplotlib.pyplot as plt

import numpy as np

sampling_rate = 5000

frequency = 50

duration = 0.1

quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels

quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step

pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)

plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')

plt.title("Message Signal (Analog)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')

plt.title("Clock Signal (Increased Frequency)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 3)

plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')

plt.title("PCM Modulated Signal (Quantized)")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(4, 1, 4)

plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')

plt.title("Signal Without Demodulation")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.tight_layout()

plt.show()


# OUTPUT:

![image](https://github.com/user-attachments/assets/6d04a472-4819-49ec-8c2b-ef0b356549d8)

# Result:

The PCM system was successfully simulated. The analog message signal was sampled, quantized, and encoded into a digital PCM signal. The simulation also showed the effect of quantization and basic demodulated output. The plots visually represent how PCM works in digital communication systems

 
