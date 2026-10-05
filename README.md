How Does AayuGuide Work?
AayuGuide operates perfectly in a tandem of hardware parts and cloud-based AI back-end system. There are four major steps to be performed: physical data capture (user input), local edge processing, cloud AI transmission and processing, as well as multisensory user feedback.

1. Physical Data Capture (User Input)
First of all, the user presses a physical Push-to-Talk button located on the device. Having pressed the button, the user starts speaking about his symptoms or asking medical questions aloud using the INMP441 microphone. At the same time, the user puts his finger on the MAX30102 sensor that monitors the heart rate and SpO2 blood oxygen level.

2. Local Edge Processing
ESP32-S3 microcontroller built into the physical device becomes its brain. It digitizes the incoming audio from the microphone and collects biometric data from the health sensor simultaneously. After that, all collected information is packed into the one payload.

3. Cloud Transmission
Thanks to its native Wi-Fi connection capabilities, ESP32-S3 sends this payload to the custom-built FastAPI server located in the cloud. So the majority of computations will be done on the server side and the energy will be saved.

4. AI Processing and Analysis
Once the payload arrives at the FastAPI backend, the server begins processing it using a three-level logic. First of all, Speech-to-Text service transforms the user's audio into text. Second, the server merges this text with the live heart rate and SpO2 data and sends this information to the Google Gemini API. The latter is the main medical AI that analyzes the user's symptoms taking into account the vitals and provides an answer.

5. Response Generation
Once the Google Gemini API generates the text-based medical advice, it sends it to the FastAPI server where the Text-to-Speech service converts the text into the digital audio stream. Then the server sends this information back to the AayuGuide device via Wi-Fi.

6. Device Output (User Feedback)
Once the FastAPI backend sends the information to the device, ESP32-S3 microcontroller separates this information into two streams. The text goes to the 2.8-inch ILI9341 TFT screen as the visual feedback. The digital audio stream goes to the MAX98357A amplifier powering the physical speaker producing the audio feedback.
